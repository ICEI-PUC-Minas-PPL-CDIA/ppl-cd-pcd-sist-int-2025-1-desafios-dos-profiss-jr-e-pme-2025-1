import pandas as pd
import numpy as np
from scipy import stats
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.utils import resample

# Configurações iniciais
pd.set_option('display.max_columns', None)
plt.style.use('ggplot')

# Função para corrigir erros de digitação e padronizar nomes
def corrigir_e_padronizar(df):
    # Correções de digitação e padronização
    correcoes = {
        'Preta': 'Preto',  # Padronizando gênero
        'Parda': 'Pardo',  # Padronizando gênero
        'Amarela': 'Amarelo',  # Padronizando gênero
        'Masculino': 'Masculino',
        'Feminino': 'Feminino',
        'Prefiro não informar': 'Não informado',
        'Não': 'Não',
        'Sim': 'Sim',
        'Não acredito que minha experiência profissional seja afetada': 'Não',
        'Sim, acredito que a minha a experiência profissional seja afetada': 'Sim',
        'de R$ 1.001/mês a R$ 2.000/mês': '1001-2000',
        'de R$ 2.001/mês a R$ 3.000/mês': '2001-3000',
        'de R$ 3.001/mês a R$ 4.000/mês': '3001-4000',
        'de R$ 4.001/mês a R$ 6.000/mês': '4001-6000',
        'de R$ 6.001/mês a R$ 8.000/mês': '6001-8000',
        'de R$ 8.001/mês a R$ 12.000/mês': '8001-12000',
        'de R$ 12.001/mês a R$ 16.000/mês': '12001-16000',
        'de R$ 16.001/mês a R$ 20.000/mês': '16001-20000',
        'de R$ 20.001/mês a R$ 25.000/mês': '20001-25000',
        'de R$ 25.001/mês a R$ 30.000/mês': '25001-30000',
        'Acima de R$ 40.001/mês': '40000+',
        'Menos de 1 ano': '0-1',
        'de 1 a 2 anos': '1-2',
        'de 3 a 4 anos': '3-4',
        'de 5 a 6 anos': '5-6',
        'de 7 a 10 anos': '7-10',
        'Mais de 10 anos': '10+',
        'Modelo 100% presencial': 'Presencial',
        'Modelo 100% remoto': 'Remoto',
        'Modelo híbrido com dias fixos de trabalho presencial': 'Híbrido fixo',
        'Modelo híbrido flexível (o funcionário tem liberdade para escolher quando estar no escritório presencialmente)': 'Híbrido flexível',
        'Não ocorreram layoffs/demissões em massa na empresa em que trabalho': 'Não',
        'Sim, ocorreram layoffs/demissões em massa na empresa em que trabalho mas não fui afetado': 'Sim não afetado',
        'Sim, ocorreram layoffs/demissões em massa na empresa em que trabalhava e eu fui afetado': 'Sim afetado',
        'Não sei opinar sobre o uso de IA Generativa e LLMs na empresa': 'Não sabe',
        'IA Generativa e LLMs não é prioridade': 'Não é prioridade',
        'Não tenho visto soluções de IA Generatica e LLMs sendo tradadas como prioridade pela empresa e pessoas, os poucos casos de uso são isolados ou ainda estão muito no início.': 'Baixa prioridade',
        'Colaboradores usando AI generativa de forma independente e descentralizada': 'Uso independente',
        'Direcionamento centralizado do uso de AI generativa': 'Uso centralizado',
        'Desenvolvedores utilizando Copilots': 'Uso de Copilots',
        'AI Generativa e LLMs para melhorar produtos externos': 'Produtos externos',
        'AI Generativa e LLMs para melhorar produtos internos para os colaboradores': 'Produtos internos',
        'IA Generativa e LLMs como principal frente do negócio': 'Principal negócio',
        'Empregado (CLT)': 'CLT',
        'Empreendedor ou Empregado (CNPJ)': 'CNPJ',
        'Servidor Público': 'Servidor público',
        'Desempregado, buscando recolocação': 'Desempregado',
        'Trabalho na área Acadêmica/Pesquisador': 'Acadêmico'
    }

    # Aplicar correções às colunas relevantes
    for col in df.columns:
        if df[col].dtype == 'object':
            df[col] = df[col].replace(correcoes)

    # Padronizar nomes de estados
    estados = {
        'AC': 'Acre', 'AL': 'Alagoas', 'AP': 'Amapá', 'AM': 'Amazonas',
        'BA': 'Bahia', 'CE': 'Ceará', 'DF': 'Distrito Federal', 'ES': 'Espírito Santo',
        'GO': 'Goiás', 'MA': 'Maranhão', 'MT': 'Mato Grosso', 'MS': 'Mato Grosso do Sul',
        'MG': 'Minas Gerais', 'PA': 'Pará', 'PB': 'Paraíba', 'PR': 'Paraná',
        'PE': 'Pernambuco', 'PI': 'Piauí', 'RJ': 'Rio de Janeiro', 'RN': 'Rio Grande do Norte',
        'RS': 'Rio Grande do Sul', 'RO': 'Rondônia', 'RR': 'Roraima', 'SC': 'Santa Catarina',
        'SP': 'São Paulo', 'SE': 'Sergipe', 'TO': 'Tocantins'
    }

    if "('P1_i_1 ', 'uf onde mora')" in df.columns:
        df["('P1_i_1 ', 'uf onde mora')"] = df["('P1_i_1 ', 'uf onde mora')"].map(estados).fillna(df["('P1_i_1 ', 'uf onde mora')"])

    return df

# Função para limpeza e preparação dos dados
def limpar_e_preparar_dados(df):
    # Selecionar apenas as colunas relevantes para as perguntas de pesquisa
    colunas_relevantes = [
        # Dados demográficos
        "('P1_a ', 'Idade')", "('P1_b ', 'Genero')", "('P1_c ', 'Cor/raca/etnia')",
        "('P1_i_1 ', 'uf onde mora')", "('P1_l ', 'Nivel de Ensino')",

        # Situação profissional
        "('P2_a ', 'Qual sua situação atual de trabalho?')",
        "('P2_b ', 'Setor')", "('P2_c ', 'Numero de Funcionarios')",
        "('P2_f ', 'Cargo Atual')", "('P2_g ', 'Nivel')",
        "('P2_h ', 'Faixa salarial')", "('P2_i ', 'Quanto tempo de experiência na área de dados você tem?')",
        "('P2_j ', 'Quanto tempo de experiência na área de TI/Engenharia de Software você teve antes de começar a trabalhar na área de dados?')",
        "('P2_k ', 'Você está satisfeito na sua empresa atual?')",
        "('P2_l ', 'Qual o principal motivo da sua insatisfação com a empresa atual?')",
        "('P2_r ', 'Atualmente qual a sua forma de trabalho?')",
        "('P2_s ', 'Qual a forma de trabalho ideal para você?')",
        "('P2_q ', 'Empresa que trabaha passou por layoff em 2023')",

        # Tecnologias e ferramentas
        "('P4_d_1 ', 'SQL')", "('P4_d_2 ', 'R ')", "('P4_d_3 ', 'Python')",
        "('P4_d_4 ', 'C/C++/C#')", "('P4_d_5 ', '.NET')", "('P4_d_6 ', 'Java')",
        "('P4_d_14 ', 'JavaScript')", "('P4_e ', 'Entre as linguagens listadas abaixo, qual é a que você mais utiliza no trabalho?')",
        "('P4_g_1 ', 'MySQL')", "('P4_g_3 ', 'SQL SERVER')", "('P4_g_12 ', 'PostgreSQL')",
        "('P4_g_22 ', 'Google BigQuery')", "('P4_g_26 ', 'Snowflake')",
        "('P4_g_27 ', 'Databricks')", "('P4_h_1 ', 'Azure (Microsoft)')",
        "('P4_h_2 ', 'Amazon Web Services (AWS)')", "('P4_h_3 ', 'Google Cloud (GCP)')",
        "('P4_j_1 ', 'Microsoft PowerBI')", "('P4_j_3 ', 'Tableau')",
        "('P4_j_7 ', 'Looker')", "('P4_j_8 ', 'Looker Studio(Google Data Studio)')",
        "('P4_j_22 ', 'Fazemos todas as análises utilizando apenas Excel ou planilhas do google')",

        # IA Generativa
        "('P3_e ', 'AI Generativa é uma prioridade em sua empresa?')",
        "('P3_f_1 ', 'Colaboradores usando AI generativa de forma independente e descentralizada')",
        "('P3_f_2 ', 'Direcionamento centralizado do uso de AI generativa')",
        "('P3_f_3 ', 'Desenvolvedores utilizando Copilots')",
        "('P3_f_4 ', 'AI Generativa e LLMs para melhorar produtos externos')",
        "('P3_f_5 ', 'AI Generativa e LLMs para melhorar produtos internos para os colaboradores')",
        "('P3_f_6 ', 'IA Generativa e LLMs como principal frente do negócio')",
        "('P3_f_7 ', 'IA Generativa e LLMs não é prioridade')",
        "('P3_f_8 ', 'Não sei opinar sobre o uso de IA Generativa e LLMs na empresa')",
        "('P4_m_1 ', 'Não uso soluções de AI Generativa com foco em produtividade')",
        "('P4_m_2 ', 'Uso soluções gratuitas de AI Generativa com foco em produtividade')",
        "('P4_m_3 ', 'Uso e pago pelas soluções de AI Generativa com foco em produtividade')",
        "('P4_m_4 ', 'A empresa que trabalho paga pelas soluções de AI Generativa com foco em produtividade')",
        "('P4_m_5 ', 'Uso soluções do tipo Copilot')"
    ]

    # Filtrar apenas colunas relevantes
    df = df[colunas_relevantes]

    # Renomear colunas para nomes mais simples
    novos_nomes = {
        "('P1_a ', 'Idade')": 'idade',
        "('P1_b ', 'Genero')": 'genero',
        "('P1_c ', 'Cor/raca/etnia')": 'cor_raca',
        "('P1_i_1 ', 'uf onde mora')": 'estado',
        "('P1_l ', 'Nivel de Ensino')": 'nivel_ensino',
        "('P2_a ', 'Qual sua situação atual de trabalho?')": 'situacao_trabalho',
        "('P2_b ', 'Setor')": 'setor',
        "('P2_c ', 'Numero de Funcionarios')": 'tamanho_empresa',
        "('P2_f ', 'Cargo Atual')": 'cargo',
        "('P2_g ', 'Nivel')": 'nivel_cargo',
        "('P2_h ', 'Faixa salarial')": 'faixa_salarial',
        "('P2_i ', 'Quanto tempo de experiência na área de dados você tem?')": 'exp_dados',
        "('P2_j ', 'Quanto tempo de experiência na área de TI/Engenharia de Software você teve antes de começar a trabalhar na área de dados?')": 'exp_ti',
        "('P2_k ', 'Você está satisfeito na sua empresa atual?')": 'satisfacao',
        "('P2_l ', 'Qual o principal motivo da sua insatisfação com a empresa atual?')": 'motivo_insatisfacao',
        "('P2_r ', 'Atualmente qual a sua forma de trabalho?')": 'modelo_trabalho',
        "('P2_s ', 'Qual a forma de trabalho ideal para você?')": 'modelo_ideal',
        "('P2_q ', 'Empresa que trabaha passou por layoff em 2023')": 'layoff',
        "('P4_d_1 ', 'SQL')": 'sql',
        "('P4_d_2 ', 'R ')": 'r',
        "('P4_d_3 ', 'Python')": 'python',
        "('P4_d_4 ', 'C/C++/C#')": 'c_cpp_csharp',
        "('P4_d_5 ', '.NET')": 'dotnet',
        "('P4_d_6 ', 'Java')": 'java',
        "('P4_d_14 ', 'JavaScript')": 'javascript',
        "('P4_e ', 'Entre as linguagens listadas abaixo, qual é a que você mais utiliza no trabalho?')": 'linguagem_principal',
        "('P4_g_1 ', 'MySQL')": 'mysql',
        "('P4_g_3 ', 'SQL SERVER')": 'sql_server',
        "('P4_g_12 ', 'PostgreSQL')": 'postgresql',
        "('P4_g_22 ', 'Google BigQuery')": 'bigquery',
        "('P4_g_26 ', 'Snowflake')": 'snowflake',
        "('P4_g_27 ', 'Databricks')": 'databricks',
        "('P4_h_1 ', 'Azure (Microsoft)')": 'azure',
        "('P4_h_2 ', 'Amazon Web Services (AWS)')": 'aws',
        "('P4_h_3 ', 'Google Cloud (GCP)')": 'gcp',
        "('P4_j_1 ', 'Microsoft PowerBI')": 'powerbi',
        "('P4_j_3 ', 'Tableau')": 'tableau',
        "('P4_j_7 ', 'Looker')": 'looker',
        "('P4_j_8 ', 'Looker Studio(Google Data Studio)')": 'looker_studio',
        "('P4_j_22 ', 'Fazemos todas as análises utilizando apenas Excel ou planilhas do google')": 'excel_planilhas',
        "('P3_e ', 'AI Generativa é uma prioridade em sua empresa?')": 'ia_prioridade',
        "('P3_f_1 ', 'Colaboradores usando AI generativa de forma independente e descentralizada')": 'ia_uso_independente',
        "('P3_f_2 ', 'Direcionamento centralizado do uso de AI generativa')": 'ia_uso_centralizado',
        "('P3_f_3 ', 'Desenvolvedores utilizando Copilots')": 'ia_copilots',
        "('P3_f_4 ', 'AI Generativa e LLMs para melhorar produtos externos')": 'ia_produtos_externos',
        "('P3_f_5 ', 'AI Generativa e LLMs para melhorar produtos internos para os colaboradores')": 'ia_produtos_internos',
        "('P3_f_6 ', 'IA Generativa e LLMs como principal frente do negócio')": 'ia_principal_negocio',
        "('P3_f_7 ', 'IA Generativa e LLMs não é prioridade')": 'ia_nao_prioridade',
        "('P3_f_8 ', 'Não sei opinar sobre o uso de IA Generativa e LLMs na empresa')": 'ia_nao_sabe',
        "('P4_m_1 ', 'Não uso soluções de AI Generativa com foco em produtividade')": 'ia_nao_usa',
        "('P4_m_2 ', 'Uso soluções gratuitas de AI Generativa com foco em produtividade')": 'ia_gratuita',
        "('P4_m_3 ', 'Uso e pago pelas soluções de AI Generativa com foco em produtividade')": 'ia_paga_pessoal',
        "('P4_m_4 ', 'A empresa que trabalho paga pelas soluções de AI Generativa com foco em produtividade')": 'ia_paga_empresa',
        "('P4_m_5 ', 'Uso soluções do tipo Copilot')": 'ia_usa_copilot'
    }

    df = df.rename(columns=novos_nomes)

    # Converter colunas de tecnologia para binário (1=usa, 0=não usa)
    tech_cols = ['sql', 'r', 'python', 'c_cpp_csharp', 'dotnet', 'java', 'javascript',
                 'mysql', 'sql_server', 'postgresql', 'bigquery', 'snowflake', 'databricks',
                 'azure', 'aws', 'gcp', 'powerbi', 'tableau', 'looker', 'looker_studio', 'excel_planilhas',
                 'ia_uso_independente', 'ia_uso_centralizado', 'ia_copilots', 'ia_produtos_externos',
                 'ia_produtos_internos', 'ia_principal_negocio', 'ia_nao_prioridade', 'ia_nao_sabe',
                 'ia_nao_usa', 'ia_gratuita', 'ia_paga_pessoal', 'ia_paga_empresa', 'ia_usa_copilot']

    for col in tech_cols:
        if col in df.columns:
            df[col] = df[col].apply(lambda x: 1 if x == 1 else 0)

    # Criar variável de tamanho da empresa (pequena, média, grande)
    def categorizar_tamanho_empresa(tamanho):
        if pd.isna(tamanho):
            return np.nan
        if isinstance(tamanho, str):
            if 'de 1 a 10' in tamanho or 'de 11 a 50' in tamanho:
                return 'Pequena'
            elif 'de 51 a 100' in tamanho or 'de 101 a 500' in tamanho:
                return 'Média'
            elif 'de 501 a 1.000' in tamanho or 'Acima de 3.000' in tamanho:
                return 'Grande'
        return np.nan

    if 'tamanho_empresa' in df.columns:
        df['tamanho_empresa_cat'] = df['tamanho_empresa'].apply(categorizar_tamanho_empresa)

    # Criar variável binária para satisfação (1=satisfeito, 0=insatisfeito)
    if 'satisfacao' in df.columns:
        df['satisfacao_binaria'] = df['satisfacao'].apply(lambda x: 1 if x == 1 else 0)

    # Converter faixa salarial para valores numéricos (média da faixa)
    def faixa_salarial_para_numero(faixa):
        if pd.isna(faixa):
            return np.nan
        if isinstance(faixa, str):
            if '1001-2000' in faixa:
                return 1500
            elif '2001-3000' in faixa:
                return 2500
            elif '3001-4000' in faixa:
                return 3500
            elif '4001-6000' in faixa:
                return 5000
            elif '6001-8000' in faixa:
                return 7000
            elif '8001-12000' in faixa:
                return 10000
            elif '12001-16000' in faixa:
                return 14000
            elif '16001-20000' in faixa:
                return 18000
            elif '20001-25000' in faixa:
                return 22500
            elif '25001-30000' in faixa:
                return 27500
            elif '40000+' in faixa:
                return 40000
        return np.nan

    if 'faixa_salarial' in df.columns:
        df['salario_medio'] = df['faixa_salarial'].apply(faixa_salarial_para_numero)

    # Converter experiência em dados para valores numéricos (média do intervalo)
    def experiencia_para_numero(exp):
        if pd.isna(exp):
            return np.nan
        if isinstance(exp, str):
            if '0-1' in exp:
                return 0.5
            elif '1-2' in exp:
                return 1.5
            elif '3-4' in exp:
                return 3.5
            elif '5-6' in exp:
                return 5.5
            elif '7-10' in exp:
                return 8.5
            elif '10+' in exp:
                return 10
        return np.nan

    if 'exp_dados' in df.columns:
        df['exp_dados_num'] = df['exp_dados'].apply(experiencia_para_numero)

    if 'exp_ti' in df.columns:
        df['exp_ti_num'] = df['exp_ti'].apply(experiencia_para_numero)

    return df

# Função para identificar e remover outliers
def remover_outliers(df):
    # Apenas para colunas numéricas
    numeric_cols = df.select_dtypes(include=[np.number]).columns

    for col in numeric_cols:
        if col in ['salario_medio', 'exp_dados_num', 'exp_ti_num']:
            # Calcular Z-scores
            z_scores = np.abs(stats.zscore(df[col].dropna()))

            # Identificar outliers (Z-score > 3)
            outliers = z_scores > 3

            # Remover outliers
            if outliers.any():
                print(f"Removendo {outliers.sum()} outliers da coluna {col}")
                df = df[~df.index.isin(outliers[outliers].index)]

    return df

# Função para balancear os dados por estado
def balancear_por_estado(df):
    if 'estado' not in df.columns:
        return df

    # Contar ocorrências por estado
    contagem_estados = df['estado'].value_counts()

    # Encontrar o estado com menor contagem
    min_contagem = contagem_estados.min()

    # Balancear os dados
    estados_balanceados = []
    for estado in df['estado'].unique():
        estado_df = df[df['estado'] == estado]
        if len(estado_df) > min_contagem:
            estado_df = resample(estado_df, replace=False, n_samples=min_contagem, random_state=42)
        estados_balanceados.append(estado_df)

    df_balanceado = pd.concat(estados_balanceados)

    return df_balanceado

# Função para análise estatística por grupo
def analisar_por_grupo(df, grupo):
    if grupo not in df.columns:
        print(f"Coluna {grupo} não encontrada no DataFrame")
        return

    resultados = {}

    # Para cada valor único na coluna de grupo
    for valor in df[grupo].unique():
        grupo_df = df[df[grupo] == valor]

        # Estatísticas descritivas para colunas numéricas
        stats = {}

        if 'salario_medio' in grupo_df.columns:
            stats['media_salario'] = grupo_df['salario_medio'].mean()
            stats['mediana_salario'] = grupo_df['salario_medio'].median()
            stats['desvio_padrao_salario'] = grupo_df['salario_medio'].std()

        if 'exp_dados_num' in grupo_df.columns:
            stats['media_exp_dados'] = grupo_df['exp_dados_num'].mean()
            stats['mediana_exp_dados'] = grupo_df['exp_dados_num'].median()
            stats['desvio_padrao_exp_dados'] = grupo_df['exp_dados_num'].std()

        if 'satisfacao_binaria' in grupo_df.columns:
            stats['taxa_satisfacao'] = grupo_df['satisfacao_binaria'].mean()

        # Adicionar ao dicionário de resultados
        resultados[valor] = stats

    return resultados

# Função para visualizar os resultados
def visualizar_resultados(resultados, titulo):
    # Converter para DataFrame para visualização
    df_resultados = pd.DataFrame(resultados).T

    # Plotar gráficos
    fig, axes = plt.subplots(nrows=2, ncols=2, figsize=(15, 10))
    fig.suptitle(titulo, fontsize=16)

    if 'media_salario' in df_resultados.columns:
        df_resultados['media_salario'].sort_values().plot(kind='bar', ax=axes[0,0], color='skyblue')
        axes[0,0].set_title('Média Salarial por Grupo')
        axes[0,0].set_ylabel('Salário Médio')

    if 'taxa_satisfacao' in df_resultados.columns:
        df_resultados['taxa_satisfacao'].sort_values().plot(kind='bar', ax=axes[0,1], color='lightgreen')
        axes[0,1].set_title('Taxa de Satisfação por Grupo')
        axes[0,1].set_ylabel('Proporção Satisfeitos')

    if 'media_exp_dados' in df_resultados.columns:
        df_resultados['media_exp_dados'].sort_values().plot(kind='bar', ax=axes[1,0], color='salmon')
        axes[1,0].set_title('Experiência Média em Dados por Grupo')
        axes[1,0].set_ylabel('Anos de Experiência')

    if 'desvio_padrao_salario' in df_resultados.columns:
        df_resultados['desvio_padrao_salario'].sort_values().plot(kind='bar', ax=axes[1,1], color='gold')
        axes[1,1].set_title('Variabilidade Salarial por Grupo')
        axes[1,1].set_ylabel('Desvio Padrão do Salário')

    plt.tight_layout()
    plt.show()

    return df_resultados

# Função principal
def main():
    # Carregar os dados
    df = pd.read_csv('State_of_data_BR_2023_Kaggle - df_survey_2023.csv')

    # 1. Corrigir erros de digitação e padronizar nomes
    df = corrigir_e_padronizar(df)

    # 2. Limpar e preparar os dados
    df = limpar_e_preparar_dados(df)

    # 3. Remover outliers
    df = remover_outliers(df)

    # 4. Balancear por estado
    df_balanceado = balancear_por_estado(df)

    # 5. Análise por grupos relevantes
    print("\n=== Análise por Tamanho da Empresa ===")
    resultados_tamanho = analisar_por_grupo(df_balanceado, 'tamanho_empresa_cat')
    df_tamanho = visualizar_resultados(resultados_tamanho, 'Análise por Tamanho da Empresa')
    print(df_tamanho)

    print("\n=== Análise por Estado ===")
    resultados_estado = analisar_por_grupo(df_balanceado, 'estado')
    df_estado = visualizar_resultados(resultados_estado, 'Análise por Estado')
    print(df_estado)

    print("\n=== Análise por Nível de Cargo ===")
    resultados_nivel = analisar_por_grupo(df_balanceado, 'nivel_cargo')
    df_nivel = visualizar_resultados(resultados_nivel, 'Análise por Nível de Cargo')
    print(df_nivel)

    # 6. Análise específica para responder às perguntas de pesquisa

    # Pergunta 1: Quais são as principais satisfações dos profissionais boas ou ruins?
    print("\n=== Análise de Satisfação ===")
    if 'satisfacao_binaria' in df_balanceado.columns and 'motivo_insatisfacao' in df_balanceado.columns:
        # Taxa geral de satisfação
        taxa_satisfacao = df_balanceado['satisfacao_binaria'].mean()
        print(f"Taxa geral de satisfação: {taxa_satisfacao:.2%}")

        # Motivos de insatisfação
        motivos_insatisfacao = df_balanceado[df_balanceado['satisfacao_binaria'] == 0]['motivo_insatisfacao'].value_counts(normalize=True)
        print("\nPrincipais motivos de insatisfação:")
        print(motivos_insatisfacao.head(5))

        # Satisfação por tamanho da empresa
        satisfacao_por_tamanho = df_balanceado.groupby('tamanho_empresa_cat')['satisfacao_binaria'].mean()
        print("\nSatisfação por tamanho da empresa:")
        print(satisfacao_por_tamanho.sort_values(ascending=False))

    # Pergunta 2: Quais fatores influenciam as inserções profissionais?
    print("\n=== Fatores que Influenciam Inserção Profissional ===")
    if 'salario_medio' in df_balanceado.columns and 'exp_dados_num' in df_balanceado.columns and 'nivel_cargo' in df_balanceado.columns:
        # Correlação entre salário e experiência
        correlacao = df_balanceado[['salario_medio', 'exp_dados_num', 'exp_ti_num']].corr()
        print("\nCorrelação entre salário e experiência:")
        print(correlacao)

        # Salário por nível de cargo
        salario_por_nivel = df_balanceado.groupby('nivel_cargo')['salario_medio'].agg(['mean', 'median', 'std'])
        print("\nSalário por nível de cargo:")
        print(salario_por_nivel)

        # Tecnologias mais usadas por nível salarial
        tech_cols = ['python', 'sql', 'r', 'java', 'javascript', 'powerbi', 'tableau', 'aws', 'azure', 'gcp']
        salario_alto = df_balanceado[df_balanceado['salario_medio'] > df_balanceado['salario_medio'].median()]
        tech_salario_alto = salario_alto[tech_cols].mean().sort_values(ascending=False)
        print("\nTecnologias mais usadas por quem ganha acima da mediana:")
        print(tech_salario_alto.head(10))


        # Plotar comparação
        plt.title('Uso de Tecnologia por Tamanho da Empresa')
        plt.ylabel('Proporção de Uso')
        plt.xticks(rotation=45)
        plt.tight_layout()
        plt.show()

    # Pergunta 4: Impacto da IA Generativa na competitividade
    print("\n=== Impacto da IA Generativa ===")
    if 'ia_prioridade' in df_balanceado.columns and 'tamanho_empresa_cat' in df_balanceado.columns:
        # Prioridade da IA por tamanho da empresa
        ia_prioridade = df_balanceado.groupby('tamanho_empresa_cat')['ia_prioridade'].value_counts(normalize=True).unstack()
        print("\nPrioridade da IA Generativa por tamanho da empresa:")
        print(ia_prioridade)

        # Uso de IA por tamanho da empresa
        ia_cols = ['ia_uso_independente', 'ia_uso_centralizado', 'ia_copilots',
                  'ia_produtos_externos', 'ia_produtos_internos', 'ia_principal_negocio']
        ia_por_tamanho = df_balanceado.groupby('tamanho_empresa_cat')[ia_cols].mean().T
        print("\nUso de IA Generativa por tamanho da empresa:")
        print(ia_por_tamanho)

        # Plotar comparação
        ia_por_tamanho.plot(kind='bar', figsize=(12, 6))
        plt.title('Uso de IA Generativa por Tamanho da Empresa')
        plt.ylabel('Proporção de Uso')
        plt.xticks(rotation=45)
        plt.tight_layout()
        plt.show()

    # Pergunta 5: Habilidades mais valorizadas para IA Generativa
    print("\n=== Habilidades para IA Generativa ===")
    if 'linguagem_principal' in df_balanceado.columns and 'ia_prioridade' in df_balanceado.columns:
        # Linguagens mais usadas por quem trabalha com IA
        ia_users = df_balanceado[(df_balanceado['ia_prioridade'] == 'Sim') |
                                (df_balanceado['ia_uso_independente'] == 1) |
                                (df_balanceado['ia_uso_centralizado'] == 1)]

        linguagens_ia = ia_users['linguagem_principal'].value_counts(normalize=True)
        print("\nLinguagens principais entre profissionais que usam IA Generativa:")
        print(linguagens_ia.head(10))



        # Análise mais detalhada por nível de adoção de IA
        print("\n=== Análise Detalhada por Nível de Adoção de IA ===")

        # Criar categorias de adoção de IA
        def categorizar_uso_ia(row):
            if row['ia_principal_negocio'] == 1:
                return 'IA como negócio principal'
            elif row['ia_produtos_externos'] == 1 or row['ia_produtos_internos'] == 1:
                return 'IA em produtos'
            elif row['ia_uso_centralizado'] == 1:
                return 'IA centralizada'
            elif row['ia_uso_independente'] == 1:
                return 'IA independente'
            elif row['ia_nao_prioridade'] == 1 or row['ia_nao_sabe'] == 1:
                return 'Baixa adoção'
            else:
                return 'Outros'

        df_balanceado['nivel_ia'] = df_balanceado.apply(categorizar_uso_ia, axis=1)

        # Tecnologias por nível de adoção de IA

        print("\nUso de tecnologias por nível de adoção de IA:")


        # Visualização
        plt.figure(figsize=(12, 6))

        plt.title('Adoção de Tecnologias por Nível de Maturidade em IA Generativa')
        plt.ylabel('Nível de Adoção de IA')
        plt.xlabel('Tecnologias')
        plt.xticks(rotation=45)
        plt.tight_layout()
        plt.show()

        # Análise de habilidades técnicas por nível de IA
        habilidades_cols = ['python', 'sql', 'aws', 'azure', 'gcp', 'databricks']
        habilidades_por_nivel = df_balanceado.groupby('nivel_ia')[habilidades_cols].mean()

        print("\nHabilidades técnicas por nível de adoção de IA:")
        print(habilidades_por_nivel)

        # Visualização em radar chart
        def radar_chart(df, title):
            categories = list(df.columns)
            N = len(categories)

            angles = [n / float(N) * 2 * np.pi for n in range(N)]
            angles += angles[:1]

            plt.figure(figsize=(8, 8))
            ax = plt.subplot(111, polar=True)

            plt.xticks(angles[:-1], categories, color='grey', size=10)
            ax.set_rlabel_position(0)
            plt.yticks([0.25, 0.5, 0.75], ["25%", "50%", "75%"], color="grey", size=8)
            plt.ylim(0, 1)

            for idx, row in df.iterrows():
                values = row.values.flatten().tolist()
                values += values[:1]
                ax.plot(angles, values, linewidth=2, linestyle='solid', label=idx)
                ax.fill(angles, values, alpha=0.1)

            plt.title(title, size=15, y=1.1)
            plt.legend(loc='upper right', bbox_to_anchor=(1.3, 1.1))
            plt.show()

        radar_chart(habilidades_por_nivel, 'Habilidades Técnicas por Nível de Adoção de IA')

        # Análise de salário por nível de adoção de IA
        if 'salario_medio' in df_balanceado.columns:
            salario_por_ia = df_balanceado.groupby('nivel_ia')['salario_medio'].agg(['mean', 'median', 'std'])
            print("\nSalário por nível de adoção de IA:")
            print(salario_por_ia)

            plt.figure(figsize=(10, 6))
            salario_por_ia['mean'].sort_values().plot(kind='barh', color='teal')
            plt.title('Salário Médio por Nível de Adoção de IA Generativa')
            plt.xlabel('Salário Médio')
            plt.ylabel('Nível de Adoção de IA')
            plt.tight_layout()
            plt.show()

    # Salvar dados processados com a nova coluna de nível de IA
    df_balanceado.to_csv('dados_processados.csv', index=False)
    print("\nDados processados salvos em 'dados_processados.csv'")

if __name__ == "__main__":
    main()