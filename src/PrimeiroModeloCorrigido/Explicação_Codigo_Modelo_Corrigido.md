# 🧠 Explicação dos Códigos Finais: Modelos de Árvore de Decisão e Random Forest

---

## Sumário:
[1. Modelo de Árvore de Decisão - Satisfação Binária](#1modelo-arvore)  
[2. Modelo Random Forest - Nível de IA](#2modelo-random-forest)  

---

<div id='1modelo-arvore'/> 

# 1. Modelo de Árvore de Decisão - Satisfação Binária

[Arquivo Python](/src/PrimeiroModeloCorrigido/Pergunta1.ipynb)

---

## 📊 Análise de Satisfação com Dados de Ensino Superior e Mercado de Dados

Este pipeline utiliza uma **Árvore de Decisão** para prever a satisfação binária (`satisfacao_binaria`) de profissionais da área de dados, com base em variáveis como salário, experiência, percentual de doutores, modelo de trabalho e nível de cargo. Inclui análise de texto para motivos de insatisfação e visualizações adicionais para explorar o modelo.

---

## 📦 Importações de Bibliotecas

```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split, cross_val_score, learning_curve
from sklearn.tree import DecisionTreeClassifier
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import classification_report, confusion_matrix
from sklearn.feature_extraction.text import TfidfVectorizer
from nltk.corpus import stopwords
import nltk
import matplotlib.pyplot as plt
import seaborn as sns
from wordcloud import WordCloud
import graphviz
from sklearn.tree import export_graphviz
```

### Descrição
- Bibliotecas como `pandas`, `numpy`, `matplotlib` e `seaborn` são usadas para manipulação e visualização de dados.
- `scikit-learn` fornece ferramentas de machine learning e avaliação de modelos.
- `nltk` e `TfidfVectorizer` são usados para processamento de linguagem natural.
- `WordCloud` cria nuvens de palavras com termos relevantes.
- `graphviz` visualiza a estrutura da árvore de decisão.

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
  - `dados_processados.csv`: Dados de profissionais (salário, experiência, etc.).
  - `Analise_Ensino_Superior_Consolidada.xlsx`: Informações sobre instituições de ensino superior (doutores por IES).

---

## 🔍 Verificar Colunas

```python
print("Colunas disponíveis em ensino:", ensino.columns.tolist())
```

- Mostra as colunas do DataFrame `ensino` para inspeção.

---

## 🧹 Pré-processamento e Enriquecimento de Dados

```python
if '%_Doutores' not in ensino.columns:
    ensino['pct_doutores'] = (ensino['QT_DOC_EX_DOUT'] / ensino['QT_DOC_TOTAL'] * 100).fillna(0)
else:
    ensino['pct_doutores'] = ensino['%_Doutores']
estado_doutores = ensino.groupby('SG_UF_IES')['pct_doutores'].mean().reset_index()
dados = dados.merge(estado_doutores, left_on='estado', right_on='SG_UF_IES', how='left')
```

- Calcula a **porcentagem de doutores** por IES, se não existir, e agrega por estado.
- Faz o **merge** com `dados` para adicionar `pct_doutores` por estado.

```python
dados['salario_medio'].fillna(dados['salario_medio'].median(), inplace=True)
dados['exp_dados_num'].fillna(0, inplace=True)
dados['motivo_insatisfacao'].fillna('', inplace=True)
dados['pct_doutores'].fillna(dados['pct_doutores'].median(), inplace=True)
```

- Substitui valores ausentes com **mediana** (para numéricos), **zero** (experiência) ou **string vazia** (texto).

---

## 🎯 Seleção e Preparação de Variáveis

```python
features = ['salario_medio', 'exp_dados_num', 'pct_doutores', 'modelo_trabalho', 'nivel_cargo']
X = dados[features]
y = dados['satisfacao_binaria']
X = pd.get_dummies(X, columns=['modelo_trabalho', 'nivel_cargo'], drop_first=True)
scaler = StandardScaler()
X[['salario_medio', 'exp_dados_num', 'pct_doutores']] = scaler.fit_transform(X[['salario_medio', 'exp_dados_num', 'pct_doutores']])
```

- Define os **features (X)** e o **alvo (y)** para modelagem.
- Transforma variáveis categóricas (`modelo_trabalho`, `nivel_cargo`) em **variáveis dummies**.
- Normaliza variáveis numéricas com `StandardScaler`.

---

## 🧪 Divisão de Dados

```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, stratify=y, random_state=42)
```

- Divide os dados em **80% treino** e **20% teste**, mantendo a proporção de classes com `stratify`.

---

## 🌳 Treinamento de Modelo

```python
clf = DecisionTreeClassifier(max_depth=5, min_samples_split=5, criterion='gini', random_state=42)
clf.fit(X_train, y_train)
```

- Treina uma **Árvore de Decisão** com profundidade máxima 5, mínimo de 5 amostras por split e critério Gini.

---

## 📈 Avaliação do Modelo

```python
y_pred = clf.predict(X_test)
print("\nRelatório de Classificação:\n", classification_report(y_test, y_pred))
scores = cross_val_score(clf, X, y, cv=5)
print("Acurácia média (validação cruzada):", scores.mean())
```

- Gera um **relatório de classificação** com precisão, recall e F1-score.
- Realiza **validação cruzada** (5 folds) para calcular a acurácia média.

---

## 🔍 Visualizações e Análises

### Visualização da Árvore

```python
dot_data = export_graphviz(clf, out_file=None, feature_names=X.columns, 
                           class_names=['Insatisfeito', 'Satisfeito'], filled=True, rounded=True)
graph = graphviz.Source(dot_data)
graph.render("arvore_decisao_satisfacao", format="png", view=False)
```

- Gera uma imagem PNG (`arvore_decisao_satisfacao.png`) da estrutura da árvore.

### Heatmap de Correlação

```python
plt.figure(figsize=(8, 6))
sns.heatmap(X[['salario_medio', 'exp_dados_num', 'pct_doutores']].corr(), annot=True, cmap='coolwarm', fmt='.2f')
plt.title('Correlação entre Features Numéricas')
plt.savefig('heatmap_correlacao.png')
plt.show()
```

- Plota a **correlação** entre variáveis numéricas, salva como `heatmap_correlacao.png`.

### Curva de Aprendizado

```python
train_sizes, train_scores, test_scores = learning_curve(clf, X, y, cv=5, train_sizes=np.linspace(0.1, 1.0, 10))
plt.figure(figsize=(8, 6))
plt.plot(train_sizes, train_scores.mean(axis=1), label='Acurácia Treino')
plt.plot(train_sizes, test_scores.mean(axis=1), label='Acurácia Teste')
plt.xlabel('Tamanho do Conjunto de Treino')
plt.ylabel('Acurácia')
plt.title('Curva de Aprendizado da Árvore de Decisão')
plt.legend()
plt.savefig('curva_aprendizado.png')
plt.show()
```

- Mostra a variação da acurácia com o tamanho do conjunto de treino, salva como `curva_aprendizado.png`.

### Importância das Features

```python
importances = pd.Series(clf.feature_importances_, index=X.columns)
importances.sort_values(ascending=False).plot(kind='bar', figsize=(10, 6))
plt.title('Importância das Features para Satisfação')
plt.savefig('importancia_features.png')
plt.show()
```

- Visualiza a **importância das variáveis** no modelo, salva como `importancia_features.png`.

### Matriz de Confusão

```python
cm = confusion_matrix(y_test, y_pred)
plt.figure(figsize=(6, 5))
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues', xticklabels=['Insatisfeito', 'Satisfeito'], 
            yticklabels=['Insatisfeito', 'Satisfeito'])
plt.xlabel('Previsto')
plt.ylabel('Real')
plt.title('Matriz de Confusão')
plt.savefig('matriz_confusao.png')
plt.show()
```

- Mostra previsões corretas e incorretas, salva como `matriz_confusao.png`.

### Matriz de Probabilidades

```python
probs = clf.predict_proba(X_test)
matriz_probs = pd.DataFrame(probs, columns=['Prob_Insatisfeito', 'Prob_Satisfeito'])
matriz_probs['Real'] = y_test.values
matriz_probs['Previsto'] = y_pred
print("\nMatriz de Probabilidades (primeiras 10 linhas):")
print(matriz_probs.head(10))
matriz_probs.to_csv('matriz_probabilidades.csv', index=False)
```

- Gera uma tabela com **probabilidades previstas**, valores reais e previstos, salva como `matriz_probabilidades.csv`.

### Análise de Texto: Motivos de Insatisfação

```python
tfidf = TfidfVectorizer(max_features=100, stop_words=stop_words)
tfidf_matrix = tfidf.fit_transform(dados['motivo_insatisfacao'])
terms = tfidf.get_feature_names_out()
word_scores = tfidf_matrix.sum(axis=0).A1
word_importance = pd.Series(word_scores, index=terms).sort_values(ascending=False)
```

- Aplica **TF-IDF** para extrair termos relevantes de `motivo_insatisfacao`.

### Nuvem de Palavras

```python
wordcloud = WordCloud(width=800, height=400, background_color='white').generate_from_frequencies(word_importance)
plt.figure(figsize=(10, 5))
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis('off')
plt.title('Nuvem de Palavras - Motivos de Insatisfação')
plt.savefig('wordcloud_insatisfacao.png')
plt.show()
```

- Gera e salva uma **nuvem de palavras** com os principais motivos de insatisfação.

---

<div id='2modelo-random-forest'/> 

# 2. Modelo Random Forest - Nível de IA

[Arquivo Python](/src/PrimeiroModeloCorrigido/Pergunta2.ipynb)

---

## 🤖 Classificação do Nível de Acesso à IA com Random Forest

Este pipeline realiza a classificação do nível de envolvimento com IA (`nivel_ia_encoded`) com base em habilidades técnicas (`sql`, `python`, `powerbi`, `aws`), nível de ensino e quantidade de doutores, utilizando um **Random Forest Classifier**.

---

## 📦 Importações

```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split, cross_val_score, learning_curve
from sklearn.ensemble import RandomForestClassifier
from sklearn.preprocessing import LabelEncoder
from sklearn.metrics import classification_report, confusion_matrix
import matplotlib.pyplot as plt
import seaborn as sns
import graphviz
from sklearn.tree import export_graphviz
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

- Adiciona a **média de doutores por estado** ao DataFrame principal.

---

## 🧹 Pré-processamento

```python
dados['nivel_ia'] = dados['nivel_ia'].fillna('Outros')
dados['QT_DOC_EX_DOUT'] = dados['QT_DOC_EX_DOUT'].fillna(dados['QT_DOC_EX_DOUT'].median())
le = LabelEncoder()
dados['nivel_ia_encoded'] = le.fit_transform(dados['nivel_ia'])
class_counts = dados['nivel_ia_encoded'].value_counts()
valid_classes = class_counts[class_counts >= 2].index
dados = dados[dados['nivel_ia_encoded'].isin(valid_classes)]
```

- Preenche valores ausentes com **"Outros"** (nível de IA) ou **mediana** (doutores).
- Codifica `nivel_ia` com **LabelEncoder**.
- Filtra classes com menos de 2 amostras para evitar erros no treinamento.

---

## 🧠 Seleção de Features

```python
habilidades = ['sql', 'python', 'powerbi', 'aws', 'nivel_ensino', 'QT_DOC_EX_DOUT']
X = dados[habilidades]
y = dados['nivel_ia_encoded']
X = pd.get_dummies(X, columns=['nivel_ensino'], drop_first=True)
```

- Define os **features (X)** e o **alvo (y)** para prever o nível de envolvimento com IA.
- Aplica **one-hot encoding** em `nivel_ensino`.

---

## 📊 Divisão dos Dados

```python
try:
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, stratify=y, random_state=42)
except ValueError:
    print("Stratificação falhou. Usando divisão sem estratificação.")
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

- Divide em **80% treino** e **20% teste**, com tentativa de estratificação. Se falhar, usa divisão simples.

---

## 🌳 Treinamento com Random Forest

```python
rf = RandomForestClassifier(n_estimators=100, max_depth=10, min_samples_split=5, random_state=42)
rf.fit(X_train, y_train)
```

- Treina um **Random Forest** com 100 árvores, profundidade máxima 10 e mínimo de 5 amostras por split.

---

## 📈 Avaliação do Modelo

```python
y_pred = rf.predict(X_test)
print("\nRelatório de Classificação:\n", classification_report(y_test, y_pred, target_names=le.classes_[valid_classes]))
scores = cross_val_score(rf, X, y, cv=5)
print("Acurácia média (validação cruzada):", scores.mean())
```

- Gera **métricas de desempenho** (precisão, recall, F1-score) por classe.
- Calcula **acurácia média** com validação cruzada (5 folds).

---

## 🔍 Visualizações e Análises

### Visualização de uma Árvore

```python
tree = rf.estimators_[0]
dot_data = export_graphviz(tree, out_file=None, feature_names=X.columns, 
                           class_names=[str(cls) for cls in le.classes_[valid_classes]], 
                           filled=True, rounded=True)
graph = graphviz.Source(dot_data)
graph.render("arvore_random_forest", format="png", view=False)
```

- Plota uma única árvore do Random Forest, salva como `arvore_random_forest.png`.

### Curva de Aprendizado

```python
train_sizes, train_scores, test_scores = learning_curve(rf, X, y, cv=5, train_sizes=np.linspace(0.1, 1.0, 10))
plt.figure(figsize=(8, 6))
plt.plot(train_sizes, train_scores.mean(axis=1), label='Acurácia Treino')
plt.plot(train_sizes, test_scores.mean(axis=1), label='Acurácia Teste')
plt.xlabel('Tamanho do Conjunto de Treino')
plt.ylabel('Acurácia')
plt.title('Curva de Aprendizado da Random Forest')
plt.legend()
plt.savefig('curva_aprendizado_rf.png')
plt.show()
```

- Mostra a **acurácia** em função do tamanho do conjunto de treino, salva como `curva_aprendizado_rf.png`.

### Importância das Features

```python
importances = pd.Series(rf.feature_importances_, index=X.columns)
importances.sort_values(ascending=False).plot(kind='bar', figsize=(10, 6))
plt.title('Importância das Habilidades para IA Generativa')
plt.savefig('importancia_features_rf.png')
plt.show()
```

- Visualiza a **importância de cada feature**, salva como `importancia_features_rf.png`.

### Análise de Correlação

```python
corr_data = X.copy()
corr_data['nivel_ia_encoded'] = y
correlacoes = corr_data.corr(method='spearman')
plt.figure(figsize=(8, 6))
sns.heatmap(correlacoes, annot=True, cmap='coolwarm', center=0)
plt.title('Correlação entre Habilidades e Nível de IA')
plt.savefig('heatmap_correlacao_rf.png')
plt.show()
```

- Gera um **heatmap** com correlações de Spearman, salva como `heatmap_correlacao_rf.png`.

### Matriz de Confusão

```python
cm = confusion_matrix(y_test, y_pred)
plt.figure(figsize=(8, 6))
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues', 
            xticklabels=le.classes_[valid_classes], yticklabels=le.classes_[valid_classes])
plt.xlabel('Previsto')
plt.ylabel('Real')
plt.title('Matriz de Confusão - Random Forest')
plt.savefig('matriz_confusao_rf.png')
plt.show()
```

- Visualiza previsões corretas e incorretas, salva como `matriz_confusao_rf.png`.

### Matriz de Probabilidades

```python
probs = rf.predict_proba(X_test)
matriz_probs = pd.DataFrame(probs, columns=[f'Prob_{cls}' for cls in le.classes_[valid_classes]])
matriz_probs['Real'] = [le.classes_[i] for i in y_test]
matriz_probs['Previsto'] = [le.classes_[i] for i in y_pred]
print("\nMatriz de Probabilidades (primeiras 10 linhas):")
print(matriz_probs.head(10))
matriz_probs.to_csv('matriz_probabilidades_rf.csv', index=False)
```

- Gera uma tabela com **probabilidades previstas**, valores reais e previstos, salva como `matriz_probabilidades_rf.csv`.

---

## 🔍 Notas Adicionais
- **Modelo de Árvore**: Focado em satisfação binária, com análise de texto para motivos de insatisfação. Ideal para interpretabilidade.
- **Modelo Random Forest**: Focado em nível de IA (multiclasse), com ênfase em habilidades técnicas. Mais robusto, mas menos interpretável diretamente.
- **Gráficos adicionais**: Curvas de aprendizado e matrizes de confusão ajudam a avaliar a generalização e erros dos modelos.
- **Matrizes de solução**: Fornecem insights detalhados sobre previsões e incertezas.
- **Dependências**: Instale `graphviz` no sistema e bibliotecas Python (`pip install pandas numpy scikit-learn matplotlib seaborn nltk wordcloud graphviz`).

---
