# Análise de Microdados do Ensino Superior 2023

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
