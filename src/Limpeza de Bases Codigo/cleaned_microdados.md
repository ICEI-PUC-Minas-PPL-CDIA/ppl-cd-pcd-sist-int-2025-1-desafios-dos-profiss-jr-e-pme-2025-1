# Análise Consolidada de Microdados do Ensino Superior 2023

## Código

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
import os
import tempfile

# Configurações iniciais
pd.set_option('display.max_columns', 50)
plt.style.use('ggplot')
sns.set_palette("husl")

def load_and_process_data(filepath):
    """Carrega e processa os dados"""
    try:
        # Carregar dados
        df = pd.read_csv(filepath, sep=';', encoding='latin-1', low_memory=False)

        # Selecionar colunas relevantes
        cols = [
            'NO_IES', 'SG_UF_IES', 'TP_CATEGORIA_ADMINISTRATIVA',
            'QT_TEC_TOTAL', 'QT_DOC_TOTAL', 'QT_DOC_EX_DOUT',
            'QT_DOC_EX_MEST', 'QT_PERIODICO_ELETRONICO',
            'QT_LIVRO_ELETRONICO', 'IN_ACESSO_PORTAL_CAPES',
            'IN_REPOSITORIO_INSTITUCIONAL', 'IN_SERVICO_INTERNET'
        ]

        # Filtrar colunas disponíveis
        available_cols = [col for col in cols if col in df.columns]
        df = df[available_cols].copy()

        # Converter para numérico
        for col in df.columns:
            if col not in ['NO_IES', 'SG_UF_IES', 'TP_CATEGORIA_ADMINISTRATIVA']:
                df[col] = pd.to_numeric(df[col], errors='coerce')

        # Remover outliers
        numeric_cols = df.select_dtypes(include=np.number).columns
        z_scores = np.abs(stats.zscore(df[numeric_cols]))
        df = df[(z_scores < 3).all(axis=1)]

        return df

    except Exception as e:
        print(f"Erro ao carregar dados: {str(e)}")
        return pd.DataFrame()

def perform_analysis_and_save(df, output_filename):
    """Realiza todas as análises e salva em um único arquivo Excel"""
    if df.empty:
        print("Dados vazios - análise não pode ser realizada")
        return

    # Criar diretório temporário para as imagens
    temp_dir = tempfile.mkdtemp()

    try:
        # Criar writer Excel
        with pd.ExcelWriter(output_filename, engine='xlsxwriter') as writer:
            # 1. Dados Limpos
            df.to_excel(writer, sheet_name='Dados_Limpos', index=False)

            # 2. Estatísticas Descritivas
            desc_stats = df.describe(include='all')
            desc_stats.to_excel(writer, sheet_name='Estatisticas_Descritivas')

            # 3. Análise por Estado
            if 'SG_UF_IES' in df.columns:
                # 3.1 Acesso tecnológico por estado
                tech_by_state = df.groupby('SG_UF_IES')[
                    ['IN_ACESSO_PORTAL_CAPES', 'IN_REPOSITORIO_INSTITUCIONAL', 'IN_SERVICO_INTERNET']
                ].mean()
                tech_by_state.to_excel(writer, sheet_name='Acesso_Tec_Estado')

                # 3.2 Qualificação docente por estado
                qualif_by_state = df.groupby('SG_UF_IES').agg({
                    'QT_DOC_EX_DOUT': 'mean',
                    'QT_DOC_EX_MEST': 'mean',
                    'QT_DOC_TOTAL': 'mean'
                })
                qualif_by_state['%_Doutores'] = qualif_by_state['QT_DOC_EX_DOUT'] / qualif_by_state['QT_DOC_TOTAL']
                qualif_by_state['%_Mestres'] = qualif_by_state['QT_DOC_EX_MEST'] / qualif_by_state['QT_DOC_TOTAL']
                qualif_by_state.to_excel(writer, sheet_name='Qualificacao_Docente_Estado')

            # 4. Análise por Categoria Administrativa
            if 'TP_CATEGORIA_ADMINISTRATIVA' in df.columns:
                category_analysis = df.groupby('TP_CATEGORIA_ADMINISTRATIVA').agg({
                    'QT_TEC_TOTAL': 'mean',
                    'QT_DOC_TOTAL': 'mean',
                    'QT_DOC_EX_DOUT': 'mean',
                    'QT_PERIODICO_ELETRONICO': 'median'
                })
                category_analysis.to_excel(writer, sheet_name='Analise_Categoria')

            # 5. Correlações
            numeric_df = df.select_dtypes(include=np.number)
            if len(numeric_df.columns) > 1:
                corr_matrix = numeric_df.corr()
                corr_matrix.to_excel(writer, sheet_name='Matriz_Correlacao')

            # 6. Top Instituições
            if 'QT_DOC_EX_DOUT' in df.columns and 'NO_IES' in df.columns:
                top_instituicoes = df.nlargest(10, 'QT_DOC_EX_DOUT')[['NO_IES', 'SG_UF_IES', 'QT_DOC_EX_DOUT']]
                top_instituicoes.to_excel(writer, sheet_name='Top slight_Instituicoes', index=False)

            # Acessar o workbook e worksheet para adicionar gráficos
            workbook = writer.book

            # Adicionar gráficos como imagens em abas separadas
            if 'SG_UF_IES' in df.columns:
                # Gráfico 1: Acesso tecnológico por estado
                plt.figure(figsize=(12, 8))
                tech_by_state.plot(kind='bar', stacked=True)
                plt.title('Acesso a Recursos Tecnológicos por Estado')
                plt.ylabel('Proporção de Instituições')
                plt.xticks(rotation=45)
                plt.tight_layout()

                tech_chart_path = os.path.join(temp_dir, 'temp_tech_chart.png')
                plt.savefig(tech_chart_path)
                plt.close()

                worksheet = workbook.add_worksheet('Grafico_Acesso_Tec')
                worksheet.insert_image('A1', tech_chart_path)

                # Gráfico 2: % de doutores por estado
                plt.figure(figsize=(12, 8))
                qualif_by_state['%_Doutores'].sort_values().plot(kind='barh')
                plt.title('Porcentagem de Docentes Doutores por Estado')
                plt.xlabel('Proporção de Doutores')
                plt.tight_layout()

                qualif_chart_path = os.path.join(temp_dir, 'temp_qualif_chart.png')
                plt.savefig(qualif_chart_path)
                plt.close()

                worksheet = workbook.add_worksheet('Grafico_Qualificacao')
                worksheet.insert_image('A1', qualif_chart_path)

            print(f"Análise concluída! Arquivo salvo em: {os.path.abspath(output_filename)}")

    finally:
        # Limpar arquivos temporários
        for filename in os.listdir(temp_dir):
            file_path = os.path.join(temp_dir, filename)
            try:
                if os.path.isfile(file_path):
                    os.unlink(file_path)
            except Exception as e:
                print(f"Erro ao deletar arquivo temporário {file_path}: {e}")

        try:
            os.rmdir(temp_dir)
        except Exception as e:
            print(f"Erro ao remover diretório temporário {temp_dir}: {e}")

def main():
    # Verificar e instalar dependências
    try:
        import xlsxwriter
    except ImportError:
        print("Instalando xlsxwriter...")
        import subprocess
        subprocess.check_call([sys.executable, "-m", "pip", "install", "xlsxwriter"])
        import xlsxwriter

    # Carregar dados
    file_path = 'MICRODADOS_ED_SUP_IES_2023.CSV'
    if not os.path.exists(file_path):
        print(f"Arquivo não encontrado: {file_path}")
        print("Por favor, verifique se o arquivo está no diretório correto.")
        return

    df = load_and_process_data(file_path)

    if df.empty:
        print("Não foi possível carregar os dados.")
        return

    # Realizar análise e salvar
    output_file = 'Analise_Ensino_Superior_Consolidada.xlsx'
    perform_analysis_and_save(df, output_file)

if __name__ == "__main__":
    import sys
    main()

```

# Análise Exploratória de Microdados do Ensino Superior 2023 pt2

## Código

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats

# Configuração inicial
pd.set_option('display.max_columns', 50)
plt.style.use('ggplot')  # Alterado de 'seaborn' para 'ggplot' que é um estilo disponível

## 1. Carregamento e Limpeza dos Dados
def load_and_clean_data(filepath):
    try:
        # Carrega os dados
        df = pd.read_csv(filepath, sep=';', encoding='latin-1', low_memory=False)

        # Limpeza básica
        df.replace('', np.nan, inplace=True)

        # Seleciona colunas relevantes para análise
        cols = [
            'NO_IES', 'TP_CATEGORIA_ADMINISTRATIVA', 'QT_TEC_TOTAL',
            'QT_DOC_TOTAL', 'QT_DOC_EX_DOUT', 'QT_DOC_EX_MEST',
            'QT_PERIODICO_ELETRONICO', 'QT_LIVRO_ELETRONICO',
            'IN_ACESSO_PORTAL_CAPES', 'IN_REPOSITORIO_INSTITUCIONAL',
            'IN_SERVICO_INTERNET', 'QT_DOC_EX_30_34', 'QT_DOC_EX_60_MAIS'
        ]

        # Verifica se as colunas existem no DataFrame
        available_cols = [col for col in cols if col in df.columns]
        df = df[available_cols].copy()

        # Converte colunas para numérico
        numeric_cols = df.select_dtypes(include=['object']).columns
        for col in numeric_cols:
            if col not in ['NO_IES', 'TP_CATEGORIA_ADMINISTRATIVA']:
                df[col] = pd.to_numeric(df[col], errors='coerce')

        # Remove outliers usando Z-score apenas para colunas numéricas
        numeric_df = df.select_dtypes(include=np.number)
        if not numeric_df.empty:
            z_scores = np.abs(stats.zscore(numeric_df))
            df = df[(z_scores < 3).all(axis=1)]

        return df

    except FileNotFoundError:
        print(f"Erro: Arquivo não encontrado no caminho {filepath}")
        return pd.DataFrame()  # Retorna DataFrame vazio em caso de erro
    except Exception as e:
        print(f"Erro ao carregar dados: {str(e)}")
        return pd.DataFrame()

# Carrega os dados (substitua pelo caminho correto)
file_path = 'MICRODADOS_ED_SUP_IES_2023.CSV'
df = load_and_clean_data(file_path)

if df.empty:
    print("Não foi possível carregar os dados. Verifique o caminho do arquivo.")
else:
    ## 2. Análise Descritiva
    def descriptive_analysis(df):
        # Estatísticas básicas
        print("\nEstatísticas Descritivas:\n")
        print(df.describe())

        # Correlações apenas se houver colunas numéricas suficientes
        numeric_df = df.select_dtypes(include=np.number)
        if len(numeric_df.columns) > 1:
            print("\nMatriz de Correlação:\n")
            corr_matrix = numeric_df.corr()
            print(corr_matrix)

            # Visualização
            plt.figure(figsize=(12, 8))
            sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', center=0)
            plt.title('Matriz de Correlação entre Variáveis')
            plt.show()
        else:
            print("\nNão há colunas numéricas suficientes para análise de correlação.")

    descriptive_analysis(df)

    ## 3. Análise por Categoria Administrativa
    def analysis_by_category(df):
        if 'TP_CATEGORIA_ADMINISTRATIVA' in df.columns:
            # Agrupa por categoria administrativa
            category_groups = df.groupby('TP_CATEGORIA_ADMINISTRATIVA')

            # Calcula médias por grupo
            means = category_groups.mean(numeric_only=True)

            # Visualização
            plt.figure(figsize=(12, 6))
            means[['QT_DOC_EX_DOUT', 'QT_DOC_EX_MEST']].plot(kind='bar')
            plt.title('Qualificação Docente por Categoria Administrativa')
            plt.ylabel('Quantidade Média')
            plt.xlabel('Categoria Administrativa')
            plt.xticks(rotation=0)
            plt.legend(['Doutores', 'Mestres'])
            plt.show()

            return means
        else:
            print("Coluna 'TP_CATEGORIA_ADMINISTRATIVA' não encontrada no DataFrame.")
            return None

    category_means = analysis_by_category(df)

    ## 4. Análise de Acesso a Tecnologia
    def technology_access_analysis(df):
        tech_cols = ['IN_ACESSO_PORTAL_CAPES', 'IN_REPOSITORIO_INSTITUCIONAL', 'IN_SERVICO_INTERNET']
        available_cols = [col for col in tech_cols if col in df.columns]

        if available_cols:
            # Calcula proporções
            tech_access = df[available_cols].mean() * 100

            # Visualização
            plt.figure(figsize=(8, 5))
            tech_access.plot(kind='bar', color=['blue', 'green', 'red'])
            plt.title('Acesso a Recursos Tecnológicos (%)')
            plt.ylabel('Percentual de Instituições')
            plt.ylim(0, 100)
            plt.show()

            # Relação entre tecnologia e qualificação docente
            if 'QT_PERIODICO_ELETRONICO' in df.columns and 'QT_DOC_EX_DOUT' in df.columns:
                plt.figure(figsize=(10, 6))
                sns.scatterplot(data=df, x='QT_PERIODICO_ELETRONICO', y='QT_DOC_EX_DOUT',
                                hue='TP_CATEGORIA_ADMINISTRATIVA' if 'TP_CATEGORIA_ADMINISTRATIVA' in df.columns else None)
                plt.title('Relação entre Acesso a Periódicos e Docentes Doutores')
                plt.xscale('log')
                plt.show()
        else:
            print("Colunas de acesso a tecnologia não encontradas no DataFrame.")

    technology_access_analysis(df)
