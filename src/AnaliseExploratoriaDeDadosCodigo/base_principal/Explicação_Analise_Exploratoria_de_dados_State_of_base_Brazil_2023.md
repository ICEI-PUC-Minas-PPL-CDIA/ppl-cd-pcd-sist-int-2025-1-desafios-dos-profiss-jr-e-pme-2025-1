

#  Análise Exploratória State of Data - Brasil 2023

A seguir, realizamos uma análise exploratória dos dados da pesquisa, abordando informações demográficas, profissionais e o uso de IA generativa no mercado de dados.

[Codigo Python](/src/AnaliseExploratoriaDeDadosCodigo/base_principal/Analise_Exploratoria_de_Dados_State_of_Data.ipynb)

---

##  Setup Inicial

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Estilo dos gráficos
sns.set(style="whitegrid")
```

- **Importação de bibliotecas:** Carregamos `matplotlib.pyplot` e `seaborn` para visualização de dados.
- **Estilo:** O estilo `whitegrid` do Seaborn melhora a legibilidade dos gráficos com uma grade leve de fundo.

---

##  Q1: Distribuição por Faixa Etária

```python
idade_series = df_tratado['faixa_idade'].value_counts(normalize=True).sort_values(ascending=False) * 100

plt.figure(figsize=(10, 5))
sns.barplot(x=idade_series.index, y=idade_series.values, palette="Blues_d")
plt.title('Distribuição por Faixa Etária (%)')
plt.xlabel('Faixa Etária')
plt.ylabel('Porcentagem')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

- **`value_counts(normalize=True)`**: calcula a proporção de respostas por faixa etária.
- **Multiplicação por 100**: converte os valores em porcentagem.
- **Gráfico de barras**: mostra a distribuição percentual de idade entre os respondentes.

---

##  Q2: Gênero dos Respondentes

```python
genero_series = df_tratado['genero'].explode().value_counts(normalize=True) * 100

plt.figure(figsize=(10, 5))
sns.barplot(x=genero_series.index, y=genero_series.values, palette="muted")
plt.title('Distribuição por Gênero (%)')
plt.xlabel('Gênero')
plt.ylabel('Porcentagem')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

- **`explode()`**: transforma listas de múltiplas respostas em linhas individuais.
- **`value_counts(normalize=True)`**: obtém a proporção de cada gênero.
- **Visualização:** gráfico de barras colorido com paleta "muted".

---

##  Q3: Cargos Atuais

```python
cargo_series = df_tratado['cargo_atual'].explode().value_counts(normalize=True) * 100

plt.figure(figsize=(10, 6))
sns.barplot(y=cargo_series.index, x=cargo_series.values, palette="Spectral")
plt.title('Distribuição por Cargo Atual (%)')
plt.xlabel('Porcentagem')
plt.ylabel('Cargo')
plt.tight_layout()
plt.show()
```

- **Gráfico de barras horizontal:** ideal para categorias com nomes longos (como cargos).
- **Paleta "Spectral"**: usada para destacar variações.

---

##  Q4: Nível de Experiência

```python
experiencia_series = df_tratado['nivel_experiencia'].value_counts(normalize=True).sort_values(ascending=False) * 100

plt.figure(figsize=(10, 5))
sns.barplot(x=experiencia_series.index, y=experiencia_series.values, palette="coolwarm")
plt.title('Distribuição por Nível de Experiência (%)')
plt.xlabel('Nível de Experiência')
plt.ylabel('Porcentagem')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

- **Distribuição de níveis de experiência**, como Júnior, Pleno, Sênior etc.
- A paleta de cor "coolwarm" facilita a diferenciação visual dos níveis.

---

##  Q5: Faixa Salarial

```python
salario_series = df_tratado['faixa_salarial'].value_counts(normalize=True).sort_values(ascending=False) * 100

plt.figure(figsize=(10, 5))
sns.barplot(x=salario_series.index, y=salario_series.values, palette="YlGnBu")
plt.title('Distribuição por Faixa Salarial (%)')
plt.xlabel('Faixa Salarial')
plt.ylabel('Porcentagem')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

- **Análise salarial:** mostra a concentração dos salários dos profissionais de dados no Brasil.
- **Ordenação decrescente**: facilita a identificação das faixas mais comuns.

---

##  Q6: Acesso à IA Generativa

```python
ia_series = df_tratado['uso_ia_generativa'].value_counts(normalize=True) * 100

plt.figure(figsize=(8, 5))
sns.barplot(x=ia_series.index, y=ia_series.values, palette="Set2")
plt.title('Uso de IA Generativa (%)')
plt.xlabel('Resposta')
plt.ylabel('Porcentagem')
plt.tight_layout()
plt.show()
```

- **Variável booleana/categórica** que mostra se o profissional já utilizou ferramentas de IA generativa.
- **Visualização direta** para entendimento rápido do nível de adoção da tecnologia.


##  Q7: Setores de Atuação

```python
setores_series = df_tratado['setor_empresa'].explode().value_counts(normalize=True) * 100

plt.figure(figsize=(10, 6))
sns.barplot(y=setores_series.index, x=setores_series.values, palette="viridis")
plt.title('Distribuição por Setor de Atuação (%)')
plt.xlabel('Porcentagem')
plt.ylabel('Setor')
plt.tight_layout()
plt.show()
```

- **Explode**: trata múltiplas respostas em uma única coluna.
- **Visualização horizontal**: ajuda a mostrar nomes longos de setores (ex: "Educação", "Financeiro").
- **Objetivo:** identificar em quais setores os profissionais de dados estão empregados.

---

##  Q8: Formação Acadêmica

```python
formacao_series = df_tratado['nivel_formacao'].value_counts(normalize=True).sort_values(ascending=False) * 100

plt.figure(figsize=(10, 5))
sns.barplot(x=formacao_series.index, y=formacao_series.values, palette="magma")
plt.title('Distribuição por Nível de Formação (%)')
plt.xlabel('Formação')
plt.ylabel('Porcentagem')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

- **Níveis de formação**: médio, técnico, graduação, pós-graduação, mestrado, doutorado.
- **Importante** para entender o background educacional da área de dados no Brasil.

---

##  Q9: Ferramentas mais utilizadas

```python
ferramentas_series = df_tratado['ferramentas_utilizadas'].explode().value_counts(normalize=True) * 100
top_ferramentas = ferramentas_series.head(15)

plt.figure(figsize=(10, 6))
sns.barplot(y=top_ferramentas.index, x=top_ferramentas.values, palette="cubehelix")
plt.title('Top 15 Ferramentas Utilizadas (%)')
plt.xlabel('Porcentagem')
plt.ylabel('Ferramenta')
plt.tight_layout()
plt.show()
```

- **Análise das ferramentas de BI, análise, programação ou ML utilizadas.**
- **Limitação aos top 15**: mantém o gráfico legível.
- **Ideal** para entender o panorama técnico das ferramentas de mercado.

---

##  Q10: Habilidades Mais Valorizadas

```python
habilidades_series = df_tratado['habilidades_valorizadas'].explode().value_counts(normalize=True) * 100
top_habilidades = habilidades_series.head(15)

plt.figure(figsize=(10, 6))
sns.barplot(y=top_habilidades.index, x=top_habilidades.values, palette="cool")
plt.title('Top 15 Habilidades Valorizadas (%)')
plt.xlabel('Porcentagem')
plt.ylabel('Habilidade')
plt.tight_layout()
plt.show()
```

- **Insight importante**: mostra o que o mercado valoriza — soft skills, linguagens, metodologias, etc.
- Pode embasar estratégias de aprendizado e plano de carreira.

---

##  Q11: Linguagens de Programação mais usadas

```python
linguagens_series = df_tratado['linguagens_programacao'].explode().value_counts(normalize=True) * 100
top_linguagens = linguagens_series.head(10)

plt.figure(figsize=(10, 5))
sns.barplot(x=top_linguagens.values, y=top_linguagens.index, palette="Set1")
plt.title('Top 10 Linguagens de Programação (%)')
plt.xlabel('Porcentagem')
plt.ylabel('Linguagem')
plt.tight_layout()
plt.show()
```

- Foco nas linguagens dominantes como Python, SQL, R, etc.
- Ajuda a visualizar o "stack" técnico predominante no setor.

---
