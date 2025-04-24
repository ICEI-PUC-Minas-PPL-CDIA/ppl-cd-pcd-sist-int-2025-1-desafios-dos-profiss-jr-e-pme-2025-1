

# 📊 Análise Exploratória de Dados do MEC (2023)

Este script em Python realiza uma análise exploratória utilizando os microdados de Instituições de Ensino Superior (IES) fornecidos pelo MEC. Os dados são extraídos, processados e visualizados por meio de gráficos:

[Codigo Python](/src/AnaliseExploratoriaDeDadosCodigo/base_auxiliar/Analise_Exploratoria_de_Dados_Microdados.ipynb)

## 🧩 1. Importação de Bibliotecas

```python
import pandas as pd
import matplotlib.pyplot as plt
```

- `pandas`: usado para manipulação de dados em formato de tabela (DataFrame).
- `matplotlib.pyplot`: biblioteca para criação de gráficos.

---

## 📥 2. Carregamento dos Dados

```python
try:
    df = pd.read_csv('MICRODADOS_ED_SUP_IES_2023.CSV', sep=';', encoding='ISO-8859-1')
except:
    df = pd.read_csv('MICRODADOS_ED_SUP_IES_2023.CSV', sep=';', encoding='latin1')
```

- Lê o arquivo CSV com os microdados das IES de 2023.
- Usa a codificação `ISO-8859-1` (com fallback para `latin1`) para garantir a leitura correta dos caracteres acentuados.
- O separador é `;` (padrão em arquivos CSV do MEC).

---

## 📍 3. Distribuição de IES por Região

```python
plt.figure(figsize=(10, 6))
df['NO_REGIAO_IES'].value_counts().plot(kind='bar', color='skyblue')
plt.title('Distribuição de IES por Região (2023)')
plt.xlabel('Região')
plt.ylabel('Número de IES')
plt.xticks(rotation=45)
plt.show()
```

- Cria um **gráfico de barras** mostrando quantas IES existem em cada região do Brasil.
- A coluna `NO_REGIAO_IES` contém o nome da região (Norte, Sul, Sudeste etc).

---

## 🎓 4. Total de Docentes com Doutorado

```python
if 'QT_DOC_EX_DOUT' in df.columns:
    docentes_doutores = df['QT_DOC_EX_DOUT'].sum()
    print(f"Total de docentes com doutorado: {docentes_doutores}")
else:
    print("Coluna 'QT_DOC_EX_DOUT' não encontrada.")
```

- Verifica se a coluna `QT_DOC_EX_DOUT` existe.
- Se sim, calcula o **total de docentes com doutorado** nas instituições.

---

## 🏛️ 5. Distribuição de Docentes com Doutorado por Tipo de Instituição

```python
docentes_doutores = df.groupby('TP_CATEGORIA_ADMINISTRATIVA')['QT_DOC_EX_DOUT'].sum()

labels = {
    1: 'Pública Federal',
    2: 'Pública Estadual',
    3: 'Pública Municipal',
    4: 'Privada com fins lucrativos',
    5: 'Privada sem fins lucrativos'
}
docentes_doutores.index = docentes_doutores.index.map(labels)

plt.figure(figsize=(8, 8))
docentes_doutores.plot(kind='pie', autopct='%1.1f%%', startangle=90)
plt.title('Distribuição de Docentes com Doutorado por Tipo de Instituição (2023)')
plt.ylabel('')
plt.show()
```

- Agrupa os dados por `TP_CATEGORIA_ADMINISTRATIVA`, que indica o tipo de instituição.
- Soma os docentes com doutorado por categoria.
- Plota um **gráfico de pizza** com a porcentagem por tipo de instituição.
- Os códigos das categorias são mapeados para rótulos legíveis.

---

## 🗂️ 6. Acesso a Repositórios Institucionais

```python
repo_acesso = df['IN_REPOSITORIO_INSTITUCIONAL'].value_counts(normalize=True) * 100

plt.figure(figsize=(8, 4))
repo_acesso.plot(kind='barh', color=['green', 'red'])
plt.title('Acesso a Repositórios Institucionais nas IES (2023)')
plt.xlabel('Porcentagem (%)')
plt.ylabel('Possui repositório?')
plt.xticks([0, 20, 40, 60, 80, 100])
plt.gca().set_yticklabels(['Não', 'Sim'])
plt.grid(axis='x', linestyle='--', alpha=0.7)
plt.show()
```

- Analisa a coluna `IN_REPOSITORIO_INSTITUCIONAL`, que indica se a IES possui repositório institucional.
- Calcula a porcentagem de IES que têm ou não repositório.
- Plota um **gráfico de barras horizontais** com essas porcentagens.

---


