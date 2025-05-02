
#  Explicação Limpeza de Dados – State of Data Brasil 2023

Este notebook é responsável por realizar a **limpeza, tratamento e pré-processamento** dos dados brutos da pesquisa, preparando o dataset para análises exploratórias e estatísticas. A seguir, está uma explicação passo a passo das células e transformações aplicadas:

[Codigo Pthon](LimpezaStateOfData.ipynb)

---

##  1. Imports e Leitura de Dados

```python
import pandas as pd
import numpy as np
```

Importa bibliotecas essenciais:
- `pandas` para manipulação de dados tabulares.
- `numpy` para operações numéricas.

---

##  2. Leitura do CSV bruto

```python
df = pd.read_csv('State of Data 2023.csv')
```

Lê o dataset original da pesquisa em formato CSV. A variável `df` agora contém os dados brutos.

---

##  3. Exibição Inicial

```python
df.head()
```

Mostra as 5 primeiras linhas do dataset para uma inspeção visual inicial dos dados.

---

##  4. Verificando Colunas

```python
df.columns
```

Lista todas as colunas presentes no dataset original. Importante para entender a estrutura dos dados e identificar variáveis irrelevantes ou mal nomeadas.

---

##  5. Remoção de Colunas Irrelevantes

```python
df = df.drop(columns=[...])
```

Remove colunas que não serão utilizadas na análise. Isso inclui:
- Informações pessoais ou sensíveis.
- Identificadores únicos.
- Comentários abertos (caso não usados).
  
Objetivo: **reduzir a dimensionalidade** do dataset e manter apenas variáveis relevantes.

---

##  6. Renomeando Colunas com Base em Dicionário

```python
dic_renomear = {...}
df = df.rename(columns=dic_renomear)
```

Renomeia as colunas para nomes mais limpos, consistentes e descritivos com base em um dicionário de mapeamento. Por exemplo:
- `'Qual seu estado?'` → `'estado'`
- `'Quanto você ganha por mês?'` → `'salario_mensal'`

---

##  7. Normalização de Dados

Inclui várias transformações para padronizar valores nas colunas:
- Remover acentos e capitalizações inconsistentes.
- Corrigir erros de digitação.
- Agrupar respostas semelhantes (ex: “Pleno” e “pleno” → “Pleno”).

---

##  8. Filtragem e Conversão de Tipos

```python
df['salario_mensal'] = pd.to_numeric(df['salario_mensal'], errors='coerce')
```

Converte a coluna de salário para tipo numérico e força a conversão de strings ou valores inválidos em `NaN`. Isso prepara o campo para análise estatística.

---

##  9. Tratamento de Valores Nulos

```python
df = df.dropna(subset=['salario_mensal', 'tempo_experiencia'])
```

Remove registros onde os campos mais importantes (como salário e tempo de experiência) estão vazios. Fundamental para garantir integridade nas análises.

---

##  10. Salvando o Dataset Tratado

```python
df.to_csv('data/df_tratado.csv', index=False)
```

Exporta o dataframe limpo para um novo arquivo CSV. Esse arquivo será utilizado no pipeline analítico.

---

