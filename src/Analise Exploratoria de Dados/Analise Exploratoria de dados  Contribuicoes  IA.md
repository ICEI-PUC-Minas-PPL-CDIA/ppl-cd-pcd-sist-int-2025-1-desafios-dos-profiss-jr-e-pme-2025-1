# Analise Exploratoria de dados  Contribuicoes  IA
Código em python para extração de dados e criação de gráficos


```
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Carregar os dados
df = pd.read_csv('Contributions_to_AI_projects_by_country_and_project_impact.csv')

# Verificar as primeiras linhas
print(df.head())

# Informações básicas sobre os dados
print(df.info())

# Estatísticas descritivas
print(df.describe())
```
```
plt.figure(figsize=(14, 8))
sns.lineplot(data=df, x='Date', y='AI_projects_fractional_count_based_on_contributions', hue='Country')
plt.title('Evolução das Contribuições para Projetos de IA por País (2020-2023)')
plt.ylabel('Fração de Contribuições')
plt.xlabel('Ano')
plt.legend(bbox_to_anchor=(1.05, 1), loc='upper left')
plt.tight_layout()
plt.show()
```

```
# Filtrar dados de 2023 e ordenar
df_2023 = df[df['Date'] == 2023].sort_values('AI_projects_fractional_count_based_on_contributions', ascending=False)

plt.figure(figsize=(12, 6))
sns.barplot(data=df_2023, x='Country', y='AI_projects_fractional_count_based_on_contributions')
plt.title('Contribuições para Projetos de IA por País em 2023')
plt.ylabel('Fração de Contribuições')
plt.xlabel('País')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

```
selected_countries = ['BRA', 'USA', 'IND', 'EU27', 'CHN', 'PAK']
df_selected = df[df['Country'].isin(selected_countries)]

plt.figure(figsize=(14, 7))
sns.lineplot(data=df_selected, x='Date', y='AI_projects_fractional_count_based_on_contributions', hue='Country',
             style='Country', markers=True, dashes=False)
plt.title('Comparação das Contribuições para Projetos de IA (2020-2023)')
plt.ylabel('Fração de Contribuições')
plt.xlabel('Ano')
plt.grid(True)
plt.legend(bbox_to_anchor=(1.05, 1), loc='upper left')
plt.tight_layout()
plt.show()
```

```
df_bra = df[df['Country'] == 'BRA']

plt.figure(figsize=(10, 5))
plt.plot(df_bra['Date'], df_bra['AI_projects_fractional_count_based_on_contributions'], marker='o')
plt.title('Evolução das Contribuições Brasileiras para Projetos de IA (2020-2023)')
plt.ylabel('Fração de Contribuições')
plt.xlabel('Ano')
plt.ylim(0, 0.05)
plt.grid(True)
plt.show()
```
```
# Pivotar os dados para o heatmap
df_pivot = df.pivot(index='Country', columns='Date', values='AI_projects_fractional_count_based_on_contributions')

plt.figure(figsize=(12, 8))
sns.heatmap(df_pivot, annot=True, fmt=".3f", cmap='YlGnBu')
plt.title('Heatmap de Contribuições para Projetos de IA por País e Ano')
plt.xlabel('Ano')
plt.ylabel('País')
plt.tight_layout()
plt.show()
```
