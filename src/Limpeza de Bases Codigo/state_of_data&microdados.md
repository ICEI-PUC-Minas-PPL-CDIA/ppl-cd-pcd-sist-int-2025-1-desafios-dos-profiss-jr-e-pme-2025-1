import pandas as pd

# Leitura dos arquivos
df_excel = pd.read_excel('Analise_Ensino_Superior_Consolidada.xlsx')
df_csv = pd.read_csv('dados_processados.csv')

# Verifica as primeiras linhas de cada DataFrame
print("Dados do Excel:")
print(df_excel.head())
print("\nDados do CSV:")
print(df_csv.head())

# Identifica colunas comuns entre os DataFrames
colunas_comuns = list(set(df_excel.columns) & set(df_csv.columns))
print("\nColunas em comum:", colunas_comuns)

# Se existir uma coluna comum (ex.: 'ID'), realiza merge; senão, concatena os DataFrames
if 'ID' in colunas_comuns:
    # Merge com base na coluna 'ID'
    df_unido = pd.merge(df_excel, df_csv, on='ID', how='outer')
else:
    # Concatenação horizontal, alinhando os DataFrames por índice
    df_unido = pd.concat([df_excel, df_csv], axis=1)

# Adiciona coluna de contextualização conforme a análise dos desafios e oportunidades
contextualizacao = (
    "IA Generativa: Análise dos desafios enfrentados por profissionais juniores e microempresas, "
    "incluindo barreiras financeiras, estruturais e a exigência de experiência para a adoção de "
    "tecnologias disruptivas no mercado."
)
df_unido['Contextualizacao'] = contextualizacao

# Salva o DataFrame resultante em um novo arquivo CSV
df_unido.to_csv('dados_unidos.csv', index=False)
print("\nDados unidos salvos em 'dados_unidos.csv'")