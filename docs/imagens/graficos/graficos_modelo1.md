# Graficos de Resultados do Primeiro Modelo: 

---
Curva ROC
Objetivo: Avaliar a capacidade do modelo em distinguir entre as classes positiva e negativa.

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

