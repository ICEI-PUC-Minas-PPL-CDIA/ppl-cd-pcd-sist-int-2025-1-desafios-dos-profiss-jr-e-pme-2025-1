

#  Análise Exploratória State of Data - Brasil 2023

A seguir, realizamos uma análise exploratória dos dados da pesquisa, abordando informações demográficas, profissionais e o uso de IA generativa no mercado de dados.

[Codigo Python](/src/AnaliseExploratoriaDeDadosCodigo/base_principal/Analise_Exploratoria_de_Dados_State_of_Data.ipynb)
Claro, Thiago! Aqui está uma explicação detalhada **em Markdown** do seu código, dividido por seções:

---

##  **Importação de bibliotecas**

```python
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
from wordcloud import WordCloud
from sklearn.feature_extraction.text import TfidfVectorizer
import re
import numpy as np
```

Essas bibliotecas são usadas para:

* `pandas`: manipulação de dados
* `matplotlib.pyplot` e `seaborn`: criação de gráficos
* `WordCloud`: geração de nuvens de palavras
* `TfidfVectorizer`: análise de texto com TF-IDF
* `re`: expressões regulares (para limpeza de texto)
* `numpy`: operações numéricas

---

##  **Carregamento e inspeção inicial do dataset**

```python
df = pd.read_csv('State_of_data_BR_2023_Kaggle - df_survey_2023.csv')
df.info()
df.describe()
```

* Lê o arquivo CSV com os dados da pesquisa.
* `df.info()` mostra as colunas, tipos de dados e valores nulos.
* `df.describe()` gera estatísticas descritivas básicas.

---

##  **Distribuição etária dos profissionais**

```python
coluna_faixa = [col for col in df.columns if 'Faixa idade' in col][0]
faixa_etaria_order = [ '22-24', '25-29', '30-34', '35-39', '40-44', '45-49', '50-54', '55+']
df['Faixa idade ordenada'] = pd.Categorical(df[coluna_faixa], categories=faixa_etaria_order, ordered=True)
contagem = df['Faixa idade ordenada'].value_counts().sort_index()
```

* Localiza a coluna correta de faixa etária.
* Define uma ordem específica para as faixas.
* Cria uma variável categórica ordenada para facilitar visualizações.

### Gráfico de barras:

```python
plt.figure(figsize=(12, 6))
ax = sns.barplot(x=contagem.index, y=contagem.values, palette='Blues_d')
...
```

Cria o gráfico de distribuição etária com rótulos e ajustes visuais.

---

##  **Distribuição de gênero**

```python
distribuicao_genero = df["('P1_b ', 'Genero')"].value_counts()
...
```

* Conta a quantidade de respondentes por gênero.
* Agrupa categorias com poucos respondentes como "Outros".
* Plota um gráfico de **pizza** com percentual.

---

##  **Distribuição de cargos por nível de experiência**

```python
df['Role'] = df["('P2_f ', 'Cargo Atual')"].apply(lambda x: x.split('/')[0] if pd.notnull(x) else x)
df['Role'] = df['Role'].map(role_mapping).fillna('Other')
df = df[df['Role'].isin(main_roles)]
df['Experience'] = df["('P2_g ', 'Nivel')"].str.strip()
cross_tab = pd.crosstab(df['Role'], df['Experience'])
...
```

* Normaliza os nomes dos cargos.
* Agrupa e reordena por níveis de experiência (Júnior, Pleno, Sênior).
* Gera gráfico de **barras agrupadas** com anotação numérica.

---

## **Pré-processamento e análise salarial**

```python
salario_map = {
    'de R$ 1.001/mês a R$ 2.000/mês': 1500,
    ...
}
df['Salario_medio'] = df["('P2_h ', 'Faixa salarial')"].map(salario_map)
```

* Mapeia faixas salariais para valores médios numéricos.
* Filtra os cargos principais.
* Cria gráfico de **barra horizontal** com distribuição salarial.

---

##  **Uso de IA generativa**

```python
colunas_uso_ia = [
    "('P4_m_1 ', 'Não uso soluções de AI Generativa com foco em produtividade')",
    ...
]
uso_ia_counts = df[colunas_uso_ia].sum().sort_values(ascending=False)
...
```

* Soma respostas binárias para saber quem usa ou não IA generativa.
* Traduz os nomes para categorias simplificadas.
* Cria um gráfico de **barras verticais com percentuais**.

---

## **Motivos de insatisfação e satisfação**

```python
cols_insatisfacao = [col for col in df.columns if 'P2_l_' in col]
insatisfacao_counts = df[cols_insatisfacao].sum().sort_values(ascending=False)
...
```

* Conta quantos marcaram cada motivo de insatisfação.
* Plota um **gráfico de barras horizontais** em vermelho.

---

##  **Boxplots de salário por experiência e cargo**

```python
plt.subplot(1, 2, 1)
sns.boxplot(x='Experiencia', y='Salario_medio', ...)
...
plt.subplot(1, 2, 2)
sns.boxplot(x='Cargo', y='Salario_medio', ...)
```

* Gera dois **boxplots lado a lado**:

  * Salário por nível de experiência.
  * Salário por cargo.

---
Claro! Vamos continuar explicando o restante do seu código em **Markdown**, mantendo o mesmo estilo didático e detalhado:

---

###  Boxplot Combinado: Salário por Cargo e Experiência

```python
# Boxplot combinado (cargo x experiência)
plt.figure(figsize=(16, 8))
sns.boxplot(x='Cargo', y='Salario_medio', hue='Experiencia', data=df,
            order=principais_cargos, hue_order=['Júnior', 'Pleno', 'Sênior'],
            palette='pastel')

plt.title('Variação Salarial por Cargo e Nível de Experiência')
plt.xlabel('Cargo')
plt.ylabel('Salário Médio (R$)')
plt.xticks(rotation=45)
plt.legend(title='Nível de Experiência')
plt.tight_layout()
plt.show()
```

#### O que este bloco faz:

* **`plt.figure(figsize=(16, 8))`**: define o tamanho do gráfico.
* **`sns.boxplot(...)`**: cria um boxplot com `Cargo` no eixo x e `Salario_medio` no eixo y, diferenciando as caixas pelo `Nível de Experiência`.

  * `hue='Experiencia'` separa os dados em diferentes cores de acordo com o nível de experiência.
  * `order` e `hue_order` garantem que as categorias apareçam na ordem desejada.
  * `palette='pastel'` define uma paleta de cores suaves.
* **`plt.title()`**, **`plt.xlabel()`**, **`plt.ylabel()`**: adicionam título e rótulos aos eixos.
* **`plt.xticks(rotation=45)`**: rotaciona os nomes dos cargos para melhorar a leitura.
* **`plt.legend()`**: exibe legenda com os níveis de experiência.
* **`plt.tight_layout()`**: organiza os elementos visuais para não sobrepor.
* **`plt.show()`**: exibe o gráfico.

---

Este gráfico é especialmente útil para **comparar variações salariais por cargo e experiência** ao mesmo tempo, permitindo observar padrões como:

* Se há progressão salarial clara entre os níveis.
* Quais cargos oferecem maior remuneração.
* Se há sobreposição entre níveis em certos cargos.


