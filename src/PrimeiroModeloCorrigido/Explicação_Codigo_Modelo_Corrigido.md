#  Explicação dos Códigos Finais: Modelos de Árvore de Decisão e Random Forest

---

## Sumário:
[1. Modelo de Árvore de Decisão - Satisfação Binária](#1modelo-arvore)  
[2. Modelo Random Forest - Nível de IA](#2modelo-random-forest)  

---

<div id='1modelo-arvore'/> 

# 1. Modelo de Árvore de Decisão - Satisfação Binária

---

## OBJETIVO PRINCIPAL DO CÓDIGO

**Responder às perguntas:**

1. Quem tende a estar satisfeito ou insatisfeito no mercado de dados?
2. Quais variáveis mais influenciam a satisfação?
3. Quais são os principais motivos de insatisfação?

---

## EXPLICAÇÃO POR BLOCO (COM JUSTIFICATIVA)

###  **Bibliotecas utilizadas**

Essenciais para cada parte da análise:

* `pandas`, `numpy`: manipulação de dados (DataFrames, cálculos, valores nulos).
* `sklearn`: tudo relacionado à modelagem (árvore de decisão, validação, pré-processamento, métricas, visualizações).
* `nltk`, `TfidfVectorizer`, `WordCloud`: análise textual dos motivos de insatisfação.
* `matplotlib`, `seaborn`, `graphviz`: visualizações para facilitar a interpretação dos resultados.

###  **Download de Stopwords**

```python
nltk.download('stopwords')
stop_words = stopwords.words('portuguese')
```

**Por quê?** Para remover palavras comuns irrelevantes ("de", "para", "com", etc.) da análise textual dos motivos de insatisfação.

---

###  **Leitura dos Dados**

```python
dados = pd.read_csv(...)
ensino = pd.read_excel(...)
```

**Por quê?**

* `dados`: informações dos profissionais (salário, experiência, satisfação, etc.).
* `ensino`: dados externos sobre percentual de doutores por estado, para enriquecer a análise (feature engineering).

---

###  **Engenharia de Variáveis**

```python
ensino['pct_doutores'] = ...
estado_doutores = ensino.groupby(...)...
dados = dados.merge(...)
```

**Por quê?**

* A **presença de doutores na região** foi usada como proxy para medir a **qualidade do ambiente educacional**, que pode influenciar oportunidades e satisfação.

---

###  **Tratamento de Valores Ausentes**

```python
.fillna(...)
```

**Por quê?**

* Impede que o modelo falhe ao encontrar dados ausentes.
* Estratégias:

  * `salario`: usa a mediana para manter tendência central.
  * `exp_dados`: assume que ausente significa zero (sem experiência).
  * `motivo_insatisfacao`: texto vazio para permitir o TF-IDF.
  * `pct_doutores`: completa com a mediana estadual.

---

###  **Seleção de Variáveis**

```python
features = [...]
y = dados['satisfacao_binaria']
```

**Por quê?**
As features foram escolhidas por **teoria e lógica de negócio**:

* `salario_medio`: remuneração impacta satisfação.
* `exp_dados_num`: mais experiência pode significar mais ou menos satisfação.
* `pct_doutores`: ambiente educacional local.
* `modelo_trabalho`: remoto, híbrido, presencial.
* `nivel_cargo`: nível hierárquico pode influenciar na satisfação.

---

###  **Dummies e Padronização**

```python
pd.get_dummies(...), StandardScaler(...)
```

**Por quê?**

* Modelos de árvore funcionam melhor com **variáveis categóricas convertidas em binárias**.
* Padronizar ajuda a manter escala semelhante entre variáveis contínuas (ex: salário vs experiência), embora árvores sejam menos sensíveis a isso.

---

###  **Separação Treino/Teste**

```python
train_test_split(..., stratify=y)
```

**Por quê?**

* Separar para **avaliar o desempenho real do modelo**.
* `stratify`: mantém a proporção original de satisfeitos e insatisfeitos (classes balanceadas).

---

###  **Criação do Modelo de Árvore**

```python
DecisionTreeClassifier(...)
```

**Por quê?**

* Árvore de decisão é **intuitiva e explicável**.
* `max_depth=5`: evita overfitting (modelo muito complexo).
* `min_samples_split=5`: evita divisões instáveis com poucos dados.
* `gini`: critério padrão de impureza.

---

###  **Predições e Métricas**

```python
y_pred = clf.predict(...)
classification_report(...)
```

**Por quê?**

* Avaliar se o modelo realmente acerta a satisfação dos respondentes.
* Métricas como precisão, recall e F1 são mais informativas que só acurácia, especialmente se as classes estiverem desequilibradas.

---

### **Visualização da Árvore**

```python
graphviz.export_graphviz(...)
```

**Por quê?**

* Facilita a interpretação da lógica do modelo.
* Mostra quais variáveis ele usou e quais caminhos levam à satisfação ou insatisfação.

---

###  **Heatmap de Correlação**

```python
sns.heatmap(...)
```

**Por quê?**

* Investigar se há correlação forte entre as variáveis numéricas (ex: salário e doutores).

---

###  **Curva de Aprendizado**

```python
learning_curve(...)
```

**Por quê?**

* Diagnóstico de overfitting ou underfitting.
* Compara acurácia no treino vs teste conforme mais dados são usados.

---

### **Matriz de Confusão**

```python
confusion_matrix(...)
```

**Por quê?**

* Entende se o modelo está errando mais em prever satisfação ou insatisfação.

---

###  **Probabilidades**

```python
clf.predict_proba(...)
```

**Por quê?**

* Permite ver **o grau de certeza** da árvore nas previsões.

---

###  **Validação Cruzada**

```python
cross_val_score(...)
```

**Por quê?**

* Verifica a **robustez do modelo em diferentes divisões dos dados**.

---

###  **Importância das Variáveis**

```python
clf.feature_importances_
```

**Por quê?**

* Identifica **o que mais influencia a satisfação** no modelo.

---

###  **TF-IDF e Nuvem de Palavras**

```python
TfidfVectorizer(...), WordCloud(...)
```

**Por quê?**

* TF-IDF mede a importância relativa de cada termo textual.
* A nuvem visualiza os **principais motivos de insatisfação** relatados em texto aberto.

---


<div id='2modelo-random-forest'/> 

# 2. Modelo Random Forest - Nível de IA

[Arquivo Python](/src/PrimeiroModeloCorrigido/Pergunta2.ipynb)

---

##  **Importação de bibliotecas**

### Por que cada biblioteca é usada?

```python
import pandas as pd 
import numpy as np
```

* `pandas` e `numpy` são a base da análise de dados em Python:

  * `pandas` permite leitura, organização e manipulação de dados em tabelas (DataFrames).
  * `numpy` oferece funções matemáticas e manipulação eficiente de arrays, importante para gráficos e cálculos.

```python
from sklearn.model_selection import train_test_split, cross_val_score, learning_curve
```

* **Modelagem com qualidade depende de avaliação cuidadosa**:

  * `train_test_split`: separa os dados em treino/teste para testar generalização do modelo.
  * `cross_val_score`: validação cruzada em K-folds (aqui, 5) para garantir robustez e reduzir viés na avaliação.
  * `learning_curve`: mostra se o modelo está sofrendo com **underfitting ou overfitting**.

```python
from sklearn.tree import DecisionTreeClassifier
```

* A **árvore de decisão** é ideal para problemas onde a **interpretação** das regras de decisão é importante. Aqui, ajuda a entender **quais fatores influenciam a satisfação**.

```python
from sklearn.preprocessing import StandardScaler
```

* Embora a árvore **não exija normalização**, você aplicou `StandardScaler` antecipando o uso de modelos futuros como SVM ou Regressão Logística, que são sensíveis à escala.

```python
from sklearn.metrics import classification_report, confusion_matrix
```

* Permite medir:

  * Precisão: quantos dos positivos previstos estavam certos.
  * Recall: quantos dos positivos reais foram capturados.
  * Matriz de confusão: como os erros estão distribuídos entre classes.

```python
from sklearn.feature_extraction.text import TfidfVectorizer
```

* Transforma o texto da coluna `motivo_insatisfacao` em uma **representação numérica vetorial**. O TF-IDF valoriza palavras que são raras no corpus geral mas frequentes em um documento, o que **ajuda a identificar termos importantes para a insatisfação**.

```python
from nltk.corpus import stopwords
import nltk
```

* **Stopwords** são palavras irrelevantes para análise textual (como “a”, “de”, “que”). O NLTK fornece uma lista específica para o português.

```python
import matplotlib.pyplot as plt
import seaborn as sns
```

* Geração de gráficos: `seaborn` facilita visualizações estatísticas como **heatmaps** e gráficos de barras, e o `matplotlib` fornece controle completo da renderização.

```python
from wordcloud import WordCloud
```

* Produz uma **nuvem de palavras visual**, onde o tamanho indica relevância. Ajuda a **comunicar visualmente os principais motivos de insatisfação**.

```python
import graphviz
from sklearn.tree import export_graphviz
```

* **Visualiza graficamente a estrutura da árvore**, mostrando regras como “Se salário > X e experiência < Y, então...”.
* Isso **torna o modelo interpretável por humanos** — essencial em estudos sociais.

---

##  **Leitura e pré-processamento dos dados**

### Enriquecimento dos dados

```python
ensino['pct_doutores'] = (ensino['QT_DOC_EX_DOUT'] / ensino['QT_DOC_TOTAL'] * 100).fillna(0)
```

* Cria uma **feature externa contextual**, o percentual de doutores por estado, que pode representar **nível de acesso à educação superior na região**.

```python
dados = dados.merge(estado_doutores, left_on='estado', right_on='SG_UF_IES', how='left')
```

* Junta os dois conjuntos de dados. Isso **aumenta o poder preditivo** ao incluir um fator regional.

### Tratamento de valores ausentes

```python
dados['salario_medio'].fillna(dados['salario_medio'].median(), inplace=True)
dados['exp_dados_num'].fillna(0, inplace=True)
dados['motivo_insatisfacao'].fillna('', inplace=True)
```

* Preenche valores ausentes com:

  * **Mediana**: boa para variáveis com distribuição assimétrica como salário.
  * **Zero**: usado em experiência como ausência da habilidade.
  * **Texto vazio**: em campos textuais para evitar erros na vetorização.

---

## **Preparação para o modelo**

### Seleção de variáveis relevantes

```python
features = ['salario_medio', 'exp_dados_num', 'pct_doutores', 'modelo_trabalho', 'nivel_cargo']
```

* Você escolheu variáveis que representam:

  * Condição econômica (salário).
  * Experiência técnica.
  * Formação regional.
  * Estrutura de trabalho (presencial/remoto).
  * Hierarquia do cargo.

### Tratamento de variáveis categóricas

```python
X = pd.get_dummies(X, columns=['modelo_trabalho', 'nivel_cargo'], drop_first=True)
```

* **Transforma categorias em colunas binárias**.
* `drop_first=True` evita multicolinearidade.

### Escalonamento

```python
scaler = StandardScaler()
```

* Escala as variáveis numéricas para **evitar que diferenças de magnitude distorçam a análise estatística ou modelos futuros**.

---

##  **Treinamento e avaliação do modelo**

```python
clf = DecisionTreeClassifier(max_depth=5, min_samples_split=5, criterion='gini', random_state=42)
```

* Parâmetros:

  * `max_depth`: limita a profundidade da árvore para **evitar overfitting**.
  * `min_samples_split`: impede que ramos muito pequenos causem divisões irrelevantes.
  * `criterion='gini'`: mede a impureza para fazer divisões (alternativa ao `entropy`).

---

## **Visualizações analíticas**

### Árvore de decisão

```python
export_graphviz(...) + graphviz.Source(...)
```

* Gera uma imagem que mostra **as regras aprendidas pelo modelo**.
* Fundamental para **explicar decisões e fazer auditoria ética do modelo**.

### Heatmap de correlação

```python
sns.heatmap(...)
```

* Permite **verificar colinearidade** entre variáveis. Correlações muito altas podem indicar redundância.

### Curva de aprendizado

```python
learning_curve(...)
```

* Diagnostica **underfitting (linha de treino baixa)** ou **overfitting (gap grande entre treino e teste)**.
* Ajuda a decidir se vale a pena adicionar mais dados.

---

##  **Avaliação dos resultados**

### Matriz de confusão

```python
confusion_matrix(...)
```

* Permite ver **erros de classificação**. Ex: o modelo erra mais ao classificar insatisfeitos?

### Probabilidades previstas

```python
clf.predict_proba(...)
```

* Mostra **nível de confiança** do modelo para cada previsão.
* Ajuda a entender quando o modelo está "em dúvida".

### Relatório de classificação

```python
classification_report(...)
```

* Mostra métricas de precisão, recall, F1 e suporte para cada classe.

### Validação cruzada

```python
cross_val_score(...)
```

* Mede **robustez do modelo** ao ser treinado/testado em várias divisões dos dados.

---

##  **Importância das variáveis**

```python
clf.feature_importances_
```

* Mostra **quais variáveis o modelo mais usou para tomar decisões**.
* Aqui, você pode descobrir se salário é mais importante que experiência, por exemplo.

---

##   **Análise textual com TF-IDF**

```python
tfidf = TfidfVectorizer(...)
```

* Extrai os termos mais relevantes dos motivos textuais de insatisfação.
* TF-IDF destaca **termos informativos** que aparecem com frequência, mas não em todo lugar.

```python
WordCloud(...).generate_from_frequencies(...)
```

* Gera uma **nuvem visual** com os termos mais fortes da insatisfação.

---




