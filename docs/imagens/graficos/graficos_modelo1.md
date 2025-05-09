# Graficos de Resultados do Primeiro Modelo: 

---
# Modelo 1.


## Curva ROC.

**Objetivo: Avaliar a capacidade do modelo em distinguir entre as classes positiva e negativa.**

![curva_roc_modelo1](https://github.com/user-attachments/assets/55dd85e2-b373-4032-a3a3-1f99632ef774)
Eixos:

X = Taxa de Falsos Positivos (FPR)

Y = Taxa de Verdadeiros Positivos (TPR)

Curva:

Mostra o desempenho do modelo em diferentes limiares.

A diagonal representa um modelo aleatório.

Interpretação:

Curva superior esquerda → ótimo desempenho

Curva próxima à diagonal → desempenho ruim

AUC perto de 1 → modelo excelente

AUC ≈ 0.5 → modelo aleatório.

Análise da imagem (AUC = 0.72):

O modelo tem capacidade razoável de distinguir as classes.



## Distribuição da Satisfação.
**Objetivo: Mostrar a contagem de clientes insatisfeitos e satisfeitos.**

![image](https://github.com/user-attachments/assets/a6a6b92a-7fcb-4ba8-8667-44aed9847eb9)
Eixos:

X = Satisfação (0=Insatisfeito, 1=Satisfeito)

Y = Contagem

Barras:

Representam a quantidade de clientes em cada categoria de satisfação.

Interpretação:

Barras mais altas indicam uma maior quantidade de clientes naquela categoria.

Análise da imagem fornecida:

A barra para "1 (Satisfeito)" é significativamente mais alta (contagem de 3420) do que a barra para "0 (Insatisfeito)" (contagem de 1873).
Interpretação:

Há mais clientes satisfeitos do que insatisfeitos no conjunto de dados.



## Distribuição por Faixa Salarial (P2_h).
**Objetivo: Mostrar a contagem de pessoas em diferentes faixas salariais.**
![distribuicao_faixa_salarial](https://github.com/user-attachments/assets/22c92a89-60b9-4b13-8433-79dffb9ae177)

Eixos:

X = Contagem

Y = Faixa Salarial

Barras:

Representam a quantidade de pessoas em cada faixa salarial. Barras mais longas indicam maior número de pessoas.

Interpretação:

As faixas salariais com as barras mais longas concentram o maior número de pessoas.

Análise da imagem fornecida:

A faixa salarial com a maior contagem é "de R$ 8.001/mês a R$ 12.000/mês".
As faixas salariais com as menores contagens estão nas extremidades inferiores ("Menos de R$ 1.000/mês") e superiores ("de R$ 25.001/mês a R$ 30.000/mês", "de R$ 30.001/mês a R$ 40.000/mês", "Acima de R$ 40.001/mês", "de R$ 101/mês a R$ 2.000/mês").
Interpretação:

A maior parte das pessoas nesta amostra se concentra na faixa salarial de R$ 8.001 a R$ 12.000 por mês. Há relativamente poucas pessoas nas faixas salariais mais baixas e mais altas.


## Matriz de Confusão
**Objetivo: Avaliar o desempenho de um modelo de classificação, mostrando o número de previsões corretas e incorretas para cada classe.**

![matriz_convusao-mod1](https://github.com/user-attachments/assets/25adea4d-332b-4503-8828-713b62c5bcf8)

Eixos:

X = Predicted label (Rótulo Previsto)
Y = True label (Rótulo Verdadeiro)

Células:

Cada célula contém a contagem de amostras que pertencem a uma determinada classe verdadeira e foram classificadas como uma determinada classe prevista.

VP: Acerto da classe 1.
VN: Acerto da classe 0.
FP: Erro: previu 1, era 0.
FN: Erro: previu 0, era 1.

Interpretação:

Valores mais altos na diagonal principal (VP e VN) indicam um bom desempenho do modelo.

Análise da imagem fornecida:

Verdadeiros Negativos (VN): 260 amostras foram corretamente classificadas como classe 0.
Falsos Positivos (FP): 209 amostras que eram da classe 0 foram incorretamente classificadas como classe 1.
Falsos Negativos (FN): 230 amostras que eram da classe 1 foram incorretamente classificadas como classe 0.
Verdadeiros Positivos (VP): 625 amostras foram corretamente classificadas como classe 1.
Interpretação:

O modelo teve um bom desempenho na identificação da classe 1 (maior número de Verdadeiros Positivos). No entanto, houve um número considerável de Falsos Positivos e Falsos Negativos, indicando que o modelo cometeu erros ao classificar ambas as classes.

Em resumo, o modelo é melhor em prever a classe 1 do que a classe 0 nesta amostra.


## Top 15 Features por Importância
**Objetivo: Visualizar a importância relativa das 15 principais features para um determinado modelo preditivo.**

![top15_features_+importante_mod1](https://github.com/user-attachments/assets/5e9c4d09-461d-4f8d-b726-94838041e6fe)

Análise:

Este gráfico de barras horizontais exibe as 15 features mais importantes, ordenadas da maior para a menor importância. O comprimento de cada barra representa a magnitude da importância daquela feature.

Interpretação:

A feature 'P2_r' demonstra ser significativamente mais importante do que todas as outras, com um valor de importância em torno de 0.65. A segunda feature mais importante, 'P4_d_1', tem uma importância consideravelmente menor, aproximadamente 0.14. A partir daí, a importância das features subsequentes diminui progressivamente, com as últimas features na lista ('P3_a_', 'P4_j_3', 'P4_j_1') apresentando uma importância muito baixa em comparação com a primeira.

Isso sugere que o modelo preditivo é fortemente influenciado pela feature 'P2_r', enquanto as demais features do top 15 têm um impacto relativamente menor no resultado da predição.

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

