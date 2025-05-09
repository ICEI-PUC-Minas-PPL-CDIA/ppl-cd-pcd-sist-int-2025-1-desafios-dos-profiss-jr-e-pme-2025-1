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

