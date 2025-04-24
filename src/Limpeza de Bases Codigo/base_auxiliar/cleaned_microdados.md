

# 🧼 Explicação Limpeza de Dados – MICRODADOS (State of Data Brasil 2023)

Este notebook trata da **limpeza, padronização e preparação dos microdados** da pesquisa *State of Data Brasil 2023*. O foco está em garantir que os dados estejam prontos para análises refinadas, especialmente voltadas para recortes demográficos, socioeconômicos e regionais.

[Codigo Python](LimpezaMICRODADOS.ipynb)

---

## 📦 1. Bibliotecas Importadas

```python
import pandas as pd
import numpy as np
```

Bibliotecas essenciais para:
- Manipulação de dados tabulares (`pandas`)
- Operações matemáticas e de array (`numpy`)

---

## 📥 2. Carregando os Dados

```python
df_microdados = pd.read_csv('MICRODADOS.csv')
```

Importa o arquivo contendo os microdados da pesquisa.

---

## 👀 3. Primeira Visão Geral

```python
df_microdados.head()
```

Mostra os primeiros registros do dataset, ajudando a identificar colunas, tipos de dados e possíveis ruídos.

---

## 🧾 4. Listando as Colunas

```python
df_microdados.columns
```

Lista todas as colunas presentes no dataset. Útil para identificar variáveis que:
- Precisam ser renomeadas
- Devem ser removidas
- Contêm dados repetitivos ou não padronizados

---

## 🧹 5. Limpeza e Redução

```python
df_microdados = df_microdados.drop(columns=[...])
```

Remove colunas irrelevantes ou redundantes. Isso:
- Reduz o ruído
- Facilita a análise posterior
- Elimina dados não essenciais (ex: colunas de timestamp ou ID que não serão usadas)

---

## 🔁 6. Renomeando Colunas com Dicionário

```python
dic_renomear = {...}
df_microdados = df_microdados.rename(columns=dic_renomear)
```

Aplica um dicionário de renomeação para tornar os nomes das colunas mais legíveis e padronizados:
- `'Qual sua idade?'` → `'idade'`
- `'Você se considera uma pessoa negra?'` → `'identidade_etnica'`

---

## 🧠 7. Padronizações de Conteúdo

Essa etapa realiza:
- Normalização de texto (minúsculas, remoção de espaços, acentos)
- Agrupamento de respostas similares
- Substituição de categorias incoerentes por valores válidos

---

## 🔢 8. Conversões e Filtros Numéricos

```python
df_microdados['idade'] = pd.to_numeric(df_microdados['idade'], errors='coerce')
```

Converte campos como `'idade'` para tipos numéricos, eliminando registros inválidos ou não numéricos.

---

## 🕳️ 9. Tratamento de Nulos

```python
df_microdados = df_microdados.dropna(subset=['idade', 'genero'])
```

Remove linhas com valores ausentes em colunas-chave, como idade e gênero. Isso garante que as análises estatísticas e segmentações sejam mais confiáveis.

---

## 🧾 10. Salvando Dataset Limpo

```python
df_microdados.to_csv('data/df_microdados_limpo.csv', index=False)
```

Salva o dataset tratado, já pronto para análises demográficas, segmentações e visualizações.

---
