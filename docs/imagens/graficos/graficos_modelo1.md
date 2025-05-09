# Graficos de Resultados do Primeiro Modelo: 

---

# Primeria Pergunta:


## Heatmap de Correlação 
**Objetivo: Verificar o grau de correlação entre variáveis numéricas.**
![download](https://github.com/user-attachments/assets/7de1413e-8f38-41d7-bfd2-3a3d6b9f1e35)


 Mostra as correlações entre: salario_medio, exp_dados_num e pct_doutores.
 
 O valor varia de -1 a 1:
* 1 = correlação positiva perfeita
* -1 = correlação negativa perfeita
* 0 = sem correlação
  
 É útil para entender relações lineares que podem afetar o modelo.

## Curva de Aprendizado 
**Objetivo: Avaliar se o modelo sofre de overfitting ou underfitting**
![download](https://github.com/user-attachments/assets/eebb020b-89d8-448a-bce0-0750ddb03298)

 Eixos:
* X = tamanho do conjunto de treino
* Y = acurácia
 Duas curvas:

*Acurácia de treino: desempenho do modelo no próprio treino
*Acurácia de teste: desempenho em dados nunca vistos
 
 Interpretação:
* Grande diferença entre treino e teste → overfitting
* Acurácias muito baixas e próximas → underfitting
* Curvas altas e próximas → bom desempenho


## Curva ROC
**Objetivo: Avaliar a capacidade do modelo em distinguir entre as classes positiva e negativa.**

![curva_roc](https://github.com/user-attachments/assets/c89ee173-2138-40c9-b990-05ecf2e9a11b)

Eixos:

X = Taxa de Falsos Positivos (FPR)

Y = Taxa de Verdadeiros Positivos (TPR)

Curva:

Mostra o desempenho do modelo em diferentes limiares de classificação.

A diagonal representa um modelo aleatório (sem poder de discriminação).

Interpretação:

Curva próxima do canto superior esquerdo → ótimo desempenho

Curva próxima da diagonal → desempenho ruim

AUC (Área sob a curva) perto de 1 → modelo excelente

AUC ≈ 0.5 → modelo aleatório.


## Matriz de Confusão
**Objetivo: Avaliar os acertos e erros do modelo em cada classe.**

![matriz_de_confusao](https://github.com/user-attachments/assets/94e7143f-555e-4db3-8e71-7cddca3f7d11)



Eixos:
 * X = valor previsto
 * Y = valor real
 
 Cada célula mostra quantas vezes o modelo acertou ou errou:
  * Diagonal = acertos    * Fora da diagonal = erros

Importante para ver onde o modelo mais erra (ex: mais falsos positivos ou negativos?).


## Gráfico de TOP 15 features mias importantes
**Objetivo: Avaliar a capacidade de cada feature em ser considerada importante.

![top15_features_+importantes](https://github.com/user-attachments/assets/05e742f4-a98d-4900-8f79-8fc45ad982c9)

Eixos:

X (análogo a FPR): Uma medida de "falsa importância" (uma feature que aparece no top 15, mas talvez não seja tão crucial?). Isso é mais difícil de definir diretamente a partir da imagem.
Y (análogo a TPR): A "taxa de verdadeira importância" (o quão importante a feature realmente é, refletida pelo seu valor no gráfico).
Curva:

Aqui, não temos uma curva, mas sim os valores das barras. Uma "boa" feature estaria mais para o topo (maior "TPR" - maior importância). Uma feature "ruim" (menos importante) estaria mais para baixo.
Uma linha "diagonal" aqui seria mais como uma distribuição uniforme de importância, onde todas as features tivessem valores semelhantes. Claramente, não é o caso.

Interpretação:

Features com barras mais altas (próximas ao "topo esquerdo" se imaginarmos um gráfico onde o eixo Y é a importância) seriam análogas a um "ótimo desempenho" em termos de importância para o modelo. 'Databricks' seria um exemplo.
Features com barras mais baixas (mais próximas de uma "base") seriam análogas a um "desempenho ruim" em termos de importância relativa dentro desse conjunto das top 15. 'nivel_ensino_Graduação/Bacharelado' seria um exemplo.
Não temos um AUC aqui, mas poderíamos dizer que a distribuição geral dos comprimentos das barras nos dá uma ideia da "capacidade" do conjunto de features de ter algumas realmente dominantes. Uma grande diferença entre a barra mais alta e as mais baixas sugere uma forte distinção na importância.



## Matriz de Probabilidades 
**Objetivo: Mostrar a probabilidade prevista para cada classe, e não só a previsão binária.**

![image](https://github.com/user-attachments/assets/96b6046e-1d9e-46ef-beea-2973e59d7434)


Cada linha representa um exemplo no teste.

Mostra: 
* Probabilidade de ser “insatisfeito”
* Probabilidade de ser “satisfeito”
* Classe real
* Classe prevista

Útil para:
* Avaliar confiança do modelo
* Analisar classificações ambíguas (ex: 49% vs 51%)

 ## Importância das Features
**Objetivo: Medir o impacto de cada variável na previsão de satisfação.**

![download](https://github.com/user-attachments/assets/d3ce6a45-74bc-454d-89c8-dda436706f1c)


Gráfico de barras com as variáveis do modelo.

A importância é baseada em quanto cada feature reduziu a impureza em toda a árvore

Ajuda a responder: “O que mais influencia a satisfação?”



## Nuvem de Palavras - Motivos de Insatisfação
**Objetivo: Visualizar os principais termos citados por pessoas insatisfeitas.**

![download](https://github.com/user-attachments/assets/22293fb9-d2bb-490b-93a4-a9f43db45861)


 As palavras maiores são as mais frequentes e relevantes, segundo o TF-IDF.
 
 Essa análise é feita a partir da variável de texto motivo_insatisfacao.
 
 Mostra de forma visual os temas mais citados: por exemplo, “salário”, “gestão”, “empresa”, etc.

---
# Segunda Pergunta:

## Curva de Aprendizado
**Objetivo: Verificar se o modelo está sofrendo com overfitting ou underfitting.**

 ![download](https://github.com/user-attachments/assets/52ca93a9-b9d4-4668-ad61-700ad385e00a)
Eixos:
* X: Tamanho do conjunto de treino.
* Y: Acurácia média (tanto no treino quanto no teste).

Interpretação:
* Se as linhas de treino e teste convergem: modelo está aprendendo bem.
* Se houver um grande espaço entre elas: pode haver overfitting.
* Essa curva mostra como a performance muda à medida que mais dados de treino são usado

//$$$


## Heatmap de Correlação
![download](https://github.com/user-attachments/assets/10d2a5d3-f159-4036-8c98-83985fc743f4)

Eixos: Todas as features numéricas + nivel_ia_encoded.

Objetivo: Medir a correlação (Spearman) entre variáveis.

Interpretação:
* Cores vermelhas = correlação positiva.
* Cores azuis = correlação negativa
  
Pode mostrar, por exemplo, que quanto maior o uso de aws, maior o nivel_ia_encoded.

