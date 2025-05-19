# Graficos de Resultados dos  Modelos: 

---



# Pergunta 1:

# Modelo 1:


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

Análise da imagem:

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

Análise da imagem:

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

Análise da imagem:

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



## Ávore de decisão treinada.
**Objetivo: Visualizar as regras de decisão aprendidas por uma árvore de decisão para classificar a satisfação.**

![arvore de decisao treinada](https://github.com/user-attachments/assets/b0c2b30d-99d1-4968-a8ac-f8813053b127)

Análise:

Cada nó da árvore representa um teste em uma feature. As ramificações representam os resultados do teste, levando a outros nós ou a nós folha. Os nós folha indicam a classe prevista (Satisfeito ou Insatisfeito).

Nós internos: Contêm a condição de teste (ex: P2_r < 3.5), o índice Gini, o número de amostras e o valor (contagem de amostras por classe).
Nós folha: Contêm o índice Gini, o número de amostras e a classe prevista.
Interpretação:

A árvore mostra como as decisões são tomadas com base nos valores das features para chegar a uma classificação de satisfação. Percorrendo a árvore a partir do nó raiz, seguindo os caminhos de "True" ou "False" de acordo com os valores das features de uma amostra, chega-se a um nó folha que indica a previsão de satisfação para essa amostra.



## Curva de aprendizado.
**Objetivo: Avaliar como o desempenho do modelo muda com o tamanho do conjunto de treinamento.**

![curva de aprendixagem](https://github.com/user-attachments/assets/7389cbba-f451-418d-9ed0-61cc2885e4fe)

Análise:

O gráfico mostra a acurácia do modelo tanto no conjunto de treino quanto no conjunto de validação para diferentes tamanhos do conjunto de treino.

Linha "Treino": Acurácia no conjunto de treino.
Linha "Validação": Acurácia no conjunto de validação (dados não vistos durante o treino).
Interpretação:

Idealmente, ambas as curvas devem convergir para um valor alto.
Uma grande lacuna entre as curvas pode indicar overfitting (bom desempenho no treino, ruim na validação) ou underfitting (desempenho ruim em ambos).


---

# Pergunta 2:  
# Modelo 1:


## Curva ROC
**Objetivo: Avaliar a capacidade do modelo em distinguir entre as classes positiva e negativa.**

![image](https://github.com/user-attachments/assets/e601699e-9191-4251-bde1-29109af90bbb)

Análise:

Eixo X: Taxa de Falsos Positivos (FPR).
Eixo Y: Taxa de Verdadeiros Positivos (TPR).
Curva: Desempenho do modelo em vários limiares.
Linha tracejada: Modelo aleatório.
AUC: Área sob a curva (0 a 1).
Interpretação:

Curva acima da linha tracejada indica melhor desempenho que aleatório.
AUC próximo de 1 é um modelo excelente.
AUC ≈ 0.5 é um modelo aleatório.
Análise da imagem fornecida:

A curva ROC (em laranja) está bem acima da linha tracejada (modelo aleatório).
O valor da Área Sob a Curva (AUC) é de 0.83.



## Matriz de confusão.
**Objetivo: Avaliar o desempenho do modelo de classificação**

![image](https://github.com/user-attachments/assets/ccf4893d-b603-49eb-8f9a-4183e46d997a)

Análise:

Verdadeiros Negativos (VN): 438 (classe 0 corretamente prevista como 0).
Falsos Positivos (FP): 92 (classe 0 incorretamente prevista como 1).
Falsos Negativos (FN): 241 (classe 1 incorretamente prevista como 0).
Verdadeiros Positivos (VP): 553 (classe 1 corretamente prevista como 1).
Interpretação:

O modelo teve um bom desempenho na identificação da classe 1 (VP alto). Houve menos erros na previsão da classe 0 (FP menor que FN).

Em resumo, o modelo classifica razoavelmente bem ambas as classes, com um desempenho ligeiramente melhor na identificação da classe positiva (1).



## Top 15 Features Mais Importantes.
**Objetivo: Mostrar a importância relativa das 15 principais características para um modelo.**

![image](https://github.com/user-attachments/assets/d9feb14d-7760-41c9-9010-747dd8afd24d)

Análise:

Barras mais longas indicam maior importância da característica.

Interpretação:

'databricks' é a característica mais importante.
A importância das características diminui ao longo da lista.
