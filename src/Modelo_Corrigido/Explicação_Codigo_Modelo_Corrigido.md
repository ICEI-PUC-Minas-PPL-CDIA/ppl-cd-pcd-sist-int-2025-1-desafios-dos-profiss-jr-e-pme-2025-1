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

[Arquivo Python](/src/Modelo_Corrigido/RandonFlorest.ipynb)


##   Importação de Bibliotecas

Importa bibliotecas para:

* Manipulação de dados: `pandas`, `numpy`
* Pré-processamento e modelagem: `scikit-learn`
* Visualização: `matplotlib`, `seaborn`
* Interpretação do modelo: `shap`

---

## Carregamento e Preparação dos Dados

```python
df = pd.read_csv('dados_selecionados.csv')
```

Lê os dados do arquivo `.csv` contendo respostas da pesquisa.

---

##  Criação da Variável-Alvo

```python
conditions = (
    df['python'] &
    (df['aws'] | df['azure'] | df['gcp']) &
    (df['powerbi'] | df['tableau'])
)
df['target_ia_generativa'] = np.where(conditions, 1, 0)
```

Define a variável `target_ia_generativa` como 1 para quem:

* Sabe Python **e**
* Sabe pelo menos uma das clouds (AWS, Azure, GCP) **e**
* Sabe Power BI **ou** Tableau

---

##  Seleção e Engenharia de Features

Seleciona features “seguras” que não causam vazamento de informação.

Cria duas novas variáveis:

* `total_linguagens`: número de linguagens que a pessoa conhece
* `exp_total`: soma da experiência em dados e em TI

Converte experiência para valores numéricos com mapeamento.

---

## Pré-processamento dos Dados

Cria um `ColumnTransformer` com:

* **OneHotEncoder** para a coluna `nivel_ensino`
* **StandardScaler** para colunas numéricas

Esse passo padroniza os dados e transforma variáveis categóricas.

---

##   Modelagem com Random Forest

Cria um `Pipeline` que junta:

* O pré-processamento
* Um `RandomForestClassifier` com balanceamento de classes e `n_jobs=-1`

Aplica `GridSearchCV` com validação cruzada (5-fold), otimizando a métrica `f1`.

```python
params = {
    'classifier__n_estimators': [100, 200],
    'classifier__max_depth': [None, 10],
    'classifier__min_samples_split': [2, 5]
}
```

---

##  Avaliação do Modelo

Após o ajuste com `GridSearchCV`, o modelo é avaliado com:

* **Acurácia** no treino e no teste
* **Relatório de Classificação** (`precision`, `recall`, `f1-score`)
* **Matriz de Confusão**
* **Curva ROC** comparando treino vs. teste
* **Curva Precision-Recall**
* **Histograma** da distribuição das probabilidades de classe positiva

---

##  Importância das Features

O modelo Random Forest permite extrair as **features mais importantes** para a predição.

É exibido um gráfico com as **15 variáveis mais influentes** no modelo final.

---

## Curva de Aprendizado

A curva de aprendizado mostra o desempenho (F1 Score) do modelo em diferentes tamanhos de conjunto de treino:

* Detecta **overfitting** (quando a linha de treino está bem acima da de validação)
* Verifica se mais dados poderiam melhorar o modelo

---

## Interpretação com SHAP

O SHAP permite interpretar a contribuição de cada variável para as predições individuais.

```python
explainer = shap.Explainer(best_model.named_steps['classifier'])
shap_values = explainer(X_transformed)
shap.summary_plot(shap_values, X_transformed, feature_names=feature_names)
```

Exibe um **summary plot** com as features que mais impactam as predições.

---

##  Resumo Final

* Leitura e limpeza de dados reais
* Criação de variável alvo com base em lógica analítica
* Engenharia de variáveis relevantes
* Pré-processamento robusto (normalização + codificação)
* Modelagem com Random Forest + tuning de hiperparâmetros
* Avaliação rigorosa com múltiplas métricas
* Interpretação dos resultados com SHAP e importância de features

---



