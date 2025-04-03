# Analise Exploratoria de Dados do Between-country AI skills migration.md
Código em python para extração de dados e criação de graficos

```
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Carregar os dados
df_migration = pd.read_csv('Between-country AI skills migration.csv')

# Verificar as primeiras linhas
print(df_migration.head())

# Informações básicas sobre os dados
print(df_migration.info())

# Estatísticas descritivas
print(df_migration.describe())
```
```
plt.figure(figsize=(14, 8))
sns.lineplot(data=df_migration, x='Year', y='AI skills migration (per 10 000 LinkedIn members)',
             hue='country_name', estimator=None, legend=False)
plt.title('Evolução da Migração de Habilidades em IA por País (2019-2023)')
plt.ylabel('Migração líquida (por 10.000 membros LinkedIn)')
plt.xlabel('Ano')
plt.grid(True)
plt.show()
```
```
# Filtrar dados de 2023 e ordenar
df_2023 = df_migration[df_migration['Year'] == 2023].sort_values('AI skills migration (per 10 000 LinkedIn members)', ascending=False)

# Top 10 países
top_10_2023 = df_2023.head(10)

plt.figure(figsize=(12, 6))
sns.barplot(data=top_10_2023, x='country_name', y='AI skills migration (per 10 000 LinkedIn members)')
plt.title('Top 10 Países que Mais Atraem Talentos em IA (2023)')
plt.ylabel('Migração líquida (por 10.000 membros LinkedIn)')
plt.xlabel('País')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
```
# Bottom 10 países
bottom_10_2023 = df_2023.tail(10)

plt.figure(figsize=(12, 6))
sns.barplot(data=bottom_10_2023, x='country_name', y='AI skills migration (per 10 000 LinkedIn members)')
plt.title('Top 10 Países que Mais Perdem Talentos em IA (2023)')
plt.ylabel('Migração líquida (por 10.000 membros LinkedIn)')
plt.xlabel('País')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
```
df_bra = df_migration[df_migration['country_name'] == 'Brazil']

plt.figure(figsize=(10, 5))
plt.plot(df_bra['Year'], df_bra['AI skills migration (per 10 000 LinkedIn members)'], marker='o')
plt.title('Evolução da Migração de Habilidades em IA no Brasil (2019-2023)')
plt.ylabel('Migração líquida (por 10.000 membros LinkedIn)')
plt.xlabel('Ano')
plt.grid(True)
plt.show()
```
```
# Pivotar os dados para o heatmap
df_pivot = df_migration.pivot(index='country_name', columns='Year',
                              values='AI skills migration (per 10 000 LinkedIn members)')

plt.figure(figsize=(12, 20))
sns.heatmap(df_pivot, annot=True, fmt=".2f", cmap='coolwarm', center=0)
plt.title('Heatmap de Migração de Habilidades em IA por País e Ano')
plt.xlabel('Ano')
plt.ylabel('País')
plt.tight_layout()
plt.show()
```
