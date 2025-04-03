# Analise Exploratoria de dados Latest Data
Código em python para extração de dados e criação de graficos

```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import matplotlib.ticker as ticker

# Configuração inicial
plt.style.use('seaborn-v0_8-whitegrid')
sns.set_palette("husl")

# Carregamento e preparação dos dados
df = pd.read_csv('Latest_Data_Science_Salaries.csv')

# Padronização dos níveis de experiência
df['Experience Level'] = df['Experience Level'].replace({
    'Entry': 'Júnior',
    'Mid': 'Pleno',
    'Senior': 'Sênior',
    'Executive': 'Diretor'
})

# Filtro e ordenação
plot_data = df[df['Experience Level'].isin(['Júnior', 'Sênior'])]
order = ['Júnior', 'Sênior']

# Criação da figura
plt.figure(figsize=(10, 6), dpi=120)

# Gráfico boxplot principal
box = sns.boxplot(
    data=plot_data,
    x='Experience Level',
    y='Salary in USD',
    order=order,
    width=0.6,
    linewidth=1.5,
    fliersize=3
)

# Adição de swarmplot para mostrar distribuição real
swarm = sns.swarmplot(
    data=plot_data,
    x='Experience Level',
    y='Salary in USD',
    order=order,
    size=3,
    alpha=0.4,
    color='.25'
)

# Cálculo e plotagem das médias
means = plot_data.groupby('Experience Level')['Salary in USD'].mean()
for i, level in enumerate(order):
    plt.scatter(i, means[level], color='red', s=100, zorder=5, label='Média' if i == 0 else "")
    plt.text(i, means[level]*1.1, f'${means[level]:,.0f}',
             ha='center', va='bottom', fontweight='bold')

# Formatação do eixo Y
plt.gca().yaxis.set_major_formatter(ticker.StrMethodFormatter('${x:,.0f}'))
plt.ylim(0, plot_data['Salary in USD'].max()*1.2)

# Labels e título
plt.title('Distribuição Salarial em IA/Data Science: Júnior vs Sênior', pad=20, fontsize=14)
plt.xlabel('Nível de Experiência', labelpad=10)
plt.ylabel('Salário Anual (USD)', labelpad=10)

# Legendas e ajustes finais
plt.legend()
plt.grid(axis='y', alpha=0.3)
sns.despine(left=True)
plt.tight_layout()

# Exibição
plt.show()

```

```

# Preparação dos dados
size_counts = df['Company Size'].value_counts().sort_index()

# Plot
plt.figure(figsize=(10,6))
plt.pie(size_counts,
        labels=size_counts.index,
        autopct='%1.1f%%',
        startangle=90,
        colors=sns.color_palette("pastel"),
        wedgeprops={'linewidth': 1, 'edgecolor': 'white'})

plt.title('Distribuição de Profissionais por Tamanho de Empresa', pad=20)
plt.tight_layout()
plt.show()

```

```
# Filtrar e agrupar
top_jobs = ['Data Scientist', 'Machine Learning Engineer', 'Data Engineer']
plot_data = df[df['Job Title'].isin(top_jobs)]

plt.figure(figsize=(12,6))
sns.barplot(data=plot_data,
            x='Job Title',
            y='Salary in USD',
            hue='Company Size',
            estimator='median',
            errorbar=None,
            palette="viridis")

plt.gca().yaxis.set_major_formatter(ticker.StrMethodFormatter('${x:,.0f}'))
plt.title('Salários Medianos por Cargo e Tamanho de Empresa', pad=20)
plt.xticks(rotation=15)
plt.legend(title='Tamanho da Empresa')
sns.despine()
plt.show()

```


```
# Top 10 países
top_countries = df['Company Location'].value_counts().head(10).index

plt.figure(figsize=(12,6))
sns.boxplot(data=df[df['Company Location'].isin(top_countries)],
            x='Company Location',
            y='Salary in USD',
            order=top_countries,
            palette="rocket")

plt.yscale('log')
plt.gca().yaxis.set_major_formatter(ticker.StrMethodFormatter('${x:,.0f}'))
plt.title('Distribuição Salarial por País (Escala Logarítmica)', pad=20)
plt.xticks(rotation=45)
sns.despine()
plt.show()

```

```
# Identificar cargos de IA Generativa
ai_jobs = ['AI Engineer', 'NLP Engineer', 'Machine Learning Engineer', 'AI Researcher']
df['AI Role'] = df['Job Title'].isin(ai_jobs)

plt.figure(figsize=(10,6))
sns.countplot(data=df,
              x='Experience Level',
              hue='AI Role',
              palette=['#808080', '#4CAF50'])

plt.title('Distribuição de Cargos em IA Generativa por Nível de Experiência', pad=20)
plt.xlabel('Nível de Experiência')
plt.ylabel('Contagem')
plt.legend(['Outros Cargos', 'IA Generativa'], title='Tipo de Cargo')
plt.tight_layout()
plt.show()
```

```
# Identificar cargos de IA Generativa
ai_jobs = ['AI Engineer', 'NLP Engineer', 'Machine Learning Engineer', 'AI Researcher']
df['AI Role'] = df['Job Title'].isin(ai_jobs)

plt.figure(figsize=(10,6))
sns.countplot(data=df,
              x='Experience Level',
              hue='AI Role',
              palette=['#808080', '#4CAF50'])

plt.title('Distribuição de Cargos em IA Generativa por Nível de Experiência', pad=20)
plt.xlabel('Nível de Experiência')
plt.ylabel('Contagem')
plt.legend(['Outros Cargos', 'IA Generativa'], title='Tipo de Cargo')
plt.tight_layout()
plt.show()
```

```
# Criar categoria para Brasil
df['Country Group'] = df['Company Location'].apply(
    lambda x: 'Brasil' if x == 'Brazil' else 'Global')

plt.figure(figsize=(10,6))
sns.violinplot(data=df,
               x='Country Group',
               y='Salary in USD',
               palette=['#FFD700', '#4682B4'])

plt.yscale('log')
plt.title('Distribuição Salarial: Brasil vs Mercado Global', pad=20)
plt.gca().yaxis.set_major_formatter(ticker.StrMethodFormatter('${x:,.0f}'))
sns.despine()
plt.show()
```
```
# Criar flags para habilidades (simulação)
skills = {
    'Python': df['Job Title'].str.contains('Python|Data Scientist|Engineer'),
    'TensorFlow': df['Job Title'].str.contains('TensorFlow|ML Engineer')
}
df_skills = pd.DataFrame(skills)

plt.figure(figsize=(10,6))
sns.boxplot(data=pd.melt(df_skills.join(df['Salary in USD']), id_vars='Salary in USD'),
            x='variable',
            y='Salary in USD',
            palette='muted')
plt.title('Impacto de Habilidades Técnicas no Salário', pad=20)
plt.gca().yaxis.set_major_formatter(ticker.StrMethodFormatter('${x:,.0f}'))
plt.xlabel('Habilidade')
plt.ylabel('Salário (USD)')
plt.ylim(0, 250000)
sns.despine()
plt.show()
```

```


# Matriz de habilidades (exemplo simplificado)
skills_matrix = pd.DataFrame({
    'Python': [0.9, 0.7, 0.4],
    'TensorFlow': [0.3, 0.6, 0.8],
    'LLMs': [0.1, 0.4, 0.7]
}, index=['Júnior', 'Pleno', 'Sênior'])

plt.figure(figsize=(8,4))
sns.heatmap(skills_matrix,
            annot=True,
            cmap='YlGnBu',
            cbar_kws={'label': 'Relevância'})
plt.title('Relevância de Competências por Nível de Experiência', pad=20)
plt.xlabel('Tecnologias')
plt.ylabel('Nível')
plt.tight_layout()
plt.show()
```
