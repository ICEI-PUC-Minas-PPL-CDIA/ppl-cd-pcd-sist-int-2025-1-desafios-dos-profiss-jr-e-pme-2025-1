# 🧠 Explicação Codigo Modelo1 Teste
---
## Sumario:
[1. Pergunta](#1pergunta)  

[2. Pergunta](#2pergunta)  

---
<div id='1pergunta'/> 
  
# 1.Pergunta:
[Codigo em Python](/src/PrimeiroModeloPreliminar/Pergunta1.ipynb)

# 📊 Análise de Satisfação com Dados de Ensino Superior e Mercado de Dados

## 📦 Importações de Bibliotecas

```python
import pandas as pd 
import numpy as np
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.tree import DecisionTreeClassifier
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import classification_report
from sklearn.feature_extraction.text import TfidfVectorizer
from nltk.corpus import stopwords
import nltk
import matplotlib.pyplot as plt
import seaborn as sns
from wordcloud import WordCloud
```

### Descrição
- Bibliotecas como `pandas`, `numpy`, `matplotlib` e `seaborn` são usadas para manipulação e visualização de dados.
- `scikit-learn` fornece ferramentas de machine learning e avaliação de modelos.
- `nltk` é usado para processamento de linguagem natural.
- `WordCloud` é usada para criar nuvens de palavras com termos importantes.

---

## 🧠 Preparação de Recursos Linguísticos

```python
nltk.download('stopwords')
stop_words = stopwords.words('portuguese')
```

- Baixa e define a lista de **palavras irrelevantes (stopwords)** em português para ignorar na análise de texto.

---

## 📥 Carregamento de Dados

```python
dados = pd.read_csv('dados_processados.csv')
ensino = pd.read_excel('Analise_Ensino_Superior_Consolidada.xlsx')
```

- Carrega dois conjuntos de dados:
  - `dados_processados.csv`: dados de profissionais da área de dados.
  - `Analise_Ensino_Superior_Consolidada.xlsx`: informações sobre instituições de ensino superior.

---

## 🔍 Verificar colunas

```python
print("Colunas disponíveis em ensino:", ensino.columns.tolist())
```

- Mostra as colunas do DataFrame `ensino` para inspeção.

---

## 🧹 Pré-processamento e Enriquecimento de Dados

```python
# Calcula a porcentagem de doutores por estado
if '%_Doutores' not in ensino.columns:
    ensino['pct_doutores'] = (ensino['QT_DOC_EX_DOUT'] / ensino['QT_DOC_TOTAL'] * 100).fillna(0)
else:
    ensino['pct_doutores'] = ensino['%_Doutores']
```

- Calcula a porcentagem de doutores nas IES (caso a coluna não exista).

```python
estado_doutores = ensino.groupby('SG_UF_IES')['pct_doutores'].mean().reset_index()
dados = dados.merge(estado_doutores, left_on='estado', right_on='SG_UF_IES', how='left')
```

- Adiciona a média de doutores por estado ao DataFrame `dados`.

```python
# Tratamento de valores ausentes
dados['salario_medio'].fillna(dados['salario_medio'].median(), inplace=True)
dados['exp_dados_num'].fillna(0, inplace=True)
dados['motivo_insatisfacao'].fillna('', inplace=True)
dados['pct_doutores'].fillna(dados['pct_doutores'].median(), inplace=True)
```

- Substitui valores ausentes com valores apropriados (mediana, zero ou string vazia).

---

## 🎯 Seleção e Preparação de Variáveis

```python
features = ['salario_medio', 'exp_dados_num', 'pct_doutores', 'modelo_trabalho', 'nivel_cargo']
X = dados[features]
y = dados['satisfacao_binaria']
```

- Define os **features (X)** e o **alvo (y)** para modelagem.

```python
X = pd.get_dummies(X, columns=['modelo_trabalho', 'nivel_cargo'], drop_first=True)
```

- Transforma variáveis categóricas em **variáveis dummies (one-hot encoding)**.

```python
scaler = StandardScaler()
X[['salario_medio', 'exp_dados_num', 'pct_doutores']] = scaler.fit_transform(X[['salario_medio', 'exp_dados_num', 'pct_doutores']])
```

- Normaliza as variáveis numéricas.

---

## 🧪 Divisão de Dados

```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, stratify=y, random_state=42)
```

- Divide os dados em treino e teste (80/20), mantendo a proporção de classes.

---

## 🌳 Treinamento de Modelo

```python
clf = DecisionTreeClassifier(max_depth=5, min_samples_split=5, criterion='gini', random_state=42)
clf.fit(X_train, y_train)
```

- Treina uma árvore de decisão com profundidade e critérios definidos.

---

## 📈 Avaliação do Modelo

```python
y_pred = clf.predict(X_test)
print("Relatório de Classificação:\n", classification_report(y_test, y_pred))
```

- Gera um relatório de desempenho (precisão, recall, F1-score).

```python
scores = cross_val_score(clf, X, y, cv=5)
print("Acurácia média (validação cruzada):", scores.mean())
```

- Realiza **validação cruzada** (5 folds) e mostra a acurácia média.

---

## 🔍 Importância das Features

```python
importances = pd.Series(clf.feature_importances_, index=X.columns)
importances.sort_values(ascending=False).plot(kind='bar', figsize=(10, 6))
plt.title('Importância das Features para Satisfação')
plt.show()
```

- Visualiza a **importância das variáveis** no modelo de decisão.

---

## 📝 Análise de Texto: Motivos de Insatisfação

```python
tfidf = TfidfVectorizer(max_features=100, stop_words=stop_words)
tfidf_matrix = tfidf.fit_transform(dados['motivo_insatisfacao'])
```

- Aplica **TF-IDF** para extrair os termos mais relevantes dos textos.

```python
terms = tfidf.get_feature_names_out()
word_scores = tfidf_matrix.sum(axis=0).A1
word_importance = pd.Series(word_scores, index=terms).sort_values(ascending=False)
```

- Calcula a importância dos termos.

---

## ☁️ Nuvem de Palavras

```python
wordcloud = WordCloud(width=800, height=400, background_color='white').generate_from_frequencies(word_importance)
plt.figure(figsize=(10, 5))
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis('off')
plt.title('Nuvem de Palavras - Motivos de Insatisfação')
plt.savefig('wordcloud_insatisfacao.png')
```

- Gera e salva uma **nuvem de palavras** com os principais motivos de insatisfação.

---


<div id='2pergunta'/> 


  
# 2. Pergunta:
[Codigo em Python](/src/PrimeiroModeloPreliminar/Pergunta_2.ipynb)

---

# 🤖 Classificação do Nível de Acesso à IA com Random Forest

Este pipeline realiza a classificação do nível de envolvimento com IA usando algoritmos de aprendizado supervisionado, com foco em habilidades técnicas e dados de ensino superior.

---

## 📦 Importações

```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.ensemble import RandomForestClassifier
from sklearn.preprocessing import LabelEncoder
from sklearn.metrics import classification_report
import matplotlib.pyplot as plt
import seaborn as sns
```

- Importa bibliotecas para manipulação de dados, modelagem, avaliação e visualização.

---

## 📥 Carregamento de Dados

```python
dados = pd.read_csv('dados_processados.csv')
ensino = pd.read_excel('Analise_Ensino_Superior_Consolidada.xlsx')
```

- Carrega os dados principais (`dados_processados.csv`) e os dados de ensino superior (`Analise_Ensino_Superior_Consolidada.xlsx`).

---

## 🧬 Enriquecimento dos Dados

```python
estado_doutores = ensino.groupby('SG_UF_IES')['QT_DOC_EX_DOUT'].mean().reset_index()
dados = dados.merge(estado_doutores, left_on='estado', right_on='SG_UF_IES', how='left')
```

- Adiciona ao dataset principal a média de doutores por estado, cruzando com o código da unidade federativa (`SG_UF_IES`).

---

## 🧹 Pré-processamento

```python
dados['nivel_ia'] = dados['nivel_ia'].fillna('Outros')
dados['QT_DOC_EX_DOUT'] = dados['QT_DOC_EX_DOUT'].fillna(dados['QT_DOC_EX_DOUT'].median())
```

- Preenche valores ausentes com estratégias adequadas (ex: "Outros", mediana).

---

## 🏷️ Codificação das Classes

```python
le = LabelEncoder()
dados['nivel_ia_encoded'] = le.fit_transform(dados['nivel_ia'])
```

- Transforma a variável `nivel_ia` (categórica) em valores numéricos codificados.

```python
# Filtrar classes com menos de 2 amostras
valid_classes = class_counts[class_counts >= 2].index
dados = dados[dados['nivel_ia_encoded'].isin(valid_classes)]
```

- Remove classes muito pequenas (com menos de 2 amostras) para evitar problemas de treino.

---

## 🧠 Seleção de Features

```python
habilidades = ['sql', 'python', 'powerbi', 'aws', 'nivel_ensino', 'QT_DOC_EX_DOUT']
X = dados[habilidades]
y = dados['nivel_ia_encoded']
```

- Define os atributos que serão usados para prever o nível de envolvimento com IA.

```python
X = pd.get_dummies(X, columns=['nivel_ensino'], drop_first=True)
```

- Codifica a variável `nivel_ensino` com one-hot encoding.

---

## 📊 Divisão dos Dados

```python
# Tenta usar stratify para manter proporções; se falhar, divide sem stratificação
try:
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, stratify=y, random_state=42)
except ValueError:
    print("Stratificação falhou. Usando divisão sem estratificação.")
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

---

## 🌳 Treinamento com Random Forest

```python
rf = RandomForestClassifier(n_estimators=100, max_depth=10, min_samples_split=5, random_state=42)
rf.fit(X_train, y_train)
```

- Modelo Random Forest com 100 árvores, profundidade máxima de 10 e no mínimo 5 amostras para split.

---

## 📈 Avaliação do Modelo

```python
y_pred = rf.predict(X_test)
print("Relatório de Classificação:\n", classification_report(y_test, y_pred, target_names=le.classes_[valid_classes]))
```

- Mostra métricas de desempenho (precisão, recall, F1-score) por classe.

```python
scores = cross_val_score(rf, X, y, cv=5)
print("Acurácia média (validação cruzada):", scores.mean())
```

- Validação cruzada para medir robustez do modelo.

---

## 🔍 Importância das Features

```python
importances = pd.Series(rf.feature_importances_, index=X.columns)
importances.sort_values(ascending=False).plot(kind='bar', figsize=(10, 6))
plt.title('Importância das Habilidades para IA Generativa')
plt.show()
```

- Visualiza a influência de cada variável no modelo.

---

## 🔥 Análise de Correlação

```python
corr_data = X.copy()
corr_data['nivel_ia_encoded'] = y
correlacoes = corr_data.corr(method='spearman')
sns.heatmap(correlacoes, annot=True, cmap='coolwarm', center=0)
plt.title('Correlação entre Habilidades e Nível de IA')
plt.savefig('heatmap_correlacao.png')
plt.show()
```

- Gera um **heatmap** com correlações de Spearman entre as variáveis e o nível de IA.

---
