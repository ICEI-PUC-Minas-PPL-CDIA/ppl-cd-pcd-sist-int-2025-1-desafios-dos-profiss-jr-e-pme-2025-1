#  Explicação dos Códigos Finais: Modelos de Árvore de Decisão e Random Forest

---

## Sumário:
[1. Modelo de Árvore de Decisão - Satisfação Binária](#1modelo-arvore)  
[2. Modelo Random Forest - Nível de IA](#2modelo-random-forest)  

---

<div id='1modelo-arvore'/> 

# 1. Modelo de Árvore de Decisão - Satisfação Binária
[Arquivo Python](/src/Modelo_Corrigido/ArvoreDeDecisao.ipynb)

Este projeto realiza uma análise de satisfação profissional com base em dados da pesquisa, usando técnicas de machine learning, visualização de dados e processamento de linguagem natural.

---

## Importação de Bibliotecas

```python
import re
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import nltk
from nltk.corpus import stopwords
from wordcloud import WordCloud
from sklearn.model_selection import train_test_split, cross_val_score, learning_curve
from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.metrics import classification_report, confusion_matrix, ConfusionMatrixDisplay, roc_curve, auc
from sklearn.preprocessing import LabelEncoder
from sklearn.feature_extraction.text import TfidfVectorizer
from imblearn.over_sampling import SMOTE
from imblearn.pipeline import make_pipeline
````

Importa bibliotecas para:

* Manipulação de dados: `pandas`, `numpy`
* Visualização: `matplotlib`, `seaborn`
* Machine Learning: `scikit-learn`, `imblearn`
* Processamento de texto: `nltk`, `TfidfVectorizer`, `WordCloud`

---

##  Download de Stopwords

```python
nltk.download('stopwords')
```

Baixa a lista de palavras irrelevantes em português (como "de", "e", "para") para serem removidas na análise textual.

---

##  Configuração de Estilo de Gráficos

```python
plt.style.use('ggplot')
sns.set_palette('pastel')
```

Define o estilo dos gráficos com aparência agradável e paleta suave.

---

##  Função: `carregar_dados(paths)`

```python
def carregar_dados(paths: list) -> pd.DataFrame:
    ...
```

* Lê um ou mais arquivos CSV.
* Limpa os nomes das colunas com expressões regulares.
* Cria a variável binária `Satisfacao_atual` com base na coluna `P2_k...` (satisfação).
* Retorna um DataFrame consolidado.

---

##  Função: `analise_exploratoria(dados)`

```python
def analise_exploratoria(dados: pd.DataFrame):
    ...
```

Cria visualizações iniciais:

* Gráfico de barras da satisfação (satisfeito vs. insatisfeito)
* Distribuição das faixas salariais, se disponível

---

##  Função: `preprocessamento(dados)`

```python
def preprocessamento(dados: pd.DataFrame):
    ...
```

* Seleciona um subconjunto de variáveis categóricas.
* Preenche valores ausentes com "Não informado".
* Codifica variáveis com `LabelEncoder`.
* Retorna `X` (features) e `y` (target binário de satisfação).

---

##  Função: `treinar_modelo(X, y)`

```python
def treinar_modelo(X, y):
    ...
```

* Divide os dados em treino e teste.
* Usa `SMOTE` para balancear as classes.
* Treina uma árvore de decisão (`DecisionTreeClassifier`) com regularização.
* Exibe:

  * Relatório de classificação
  * Matriz de confusão
  * Curva ROC
  * Gráfico de importância das variáveis

---

##  Função: `avaliacao_avancada(modelo, X, y)`

```python
def avaliacao_avancada(modelo, X, y):
    ...
```

Avalia a performance do modelo com:

* Validação cruzada (5-fold)
* Curva de aprendizado (performance vs. quantidade de dados)

---

##  Função: `gerar_nuvem_palavras(...)`

```python
def gerar_nuvem_palavras(dados: pd.DataFrame, coluna_texto: str, condicao: int, titulo: str, nome_arquivo: str):
    ...
```

* Filtra respostas textuais de acordo com a satisfação (`0` ou `1`).
* Aplica `TF-IDF` para medir a importância das palavras.
* Gera uma nuvem de palavras e salva como imagem.

---

##  Função Principal: `main()`

```python
def main():
    ...
```

Integra todas as etapas:

1. Carrega e limpa os dados
2. Realiza análise exploratória
3. Preprocessa variáveis
4. Treina modelo e plota árvore
5. Avalia com curva de aprendizado
6. Gera nuvens de palavras para satisfeitos e insatisfeitos

---

##  Tratamento de Erros

```python
except Exception as e:
    ...
```

Exibe mensagens claras em caso de falhas como:

* Caminho inválido
* Colunas inconsistentes
* Dados faltantes

---

## Execução do Script

```python
if __name__ == "__main__":
    main()
```

Garante que o script só será executado se for chamado diretamente (não quando importado como módulo).

---




<div id='2modelo-random-forest'/> 

# 2. Modelo Random Forest - Nível de IA

[Arquivo Python](/src/PrimeiroModeloCorrigido/Pergunta2.ipynb)

---

