# Graficos de Resultados dos  Modelos: 

---



# Modelo 1:

# Resultado dos Modelos

# Pergunta 1

## Modelo Árvore de Decisão

Este relatório tem como objetivo fornecer uma análise aprofundada de um conjunto de dados e a avaliação de um modelo de machine learning desenvolvido para prever a satisfação. Serão detalhados nove gráficos distintos, cada um com seu objetivo, o que ele representa, os resultados obtidos e sua importância para a compreensão do fenômeno estudado e para a otimização do modelo preditivo. A análise abrange desde a exploração inicial dos dados até a interpretabilidade do modelo e a identificação de fatores qualitativos de insatisfação, buscando extrair informações que possam informar decisões estratégicas.

## 2. Análise Exploratória de Dados (AED)

### 2.1. Distribuição da Satisfação (Imagem 1)

O gráfico de barras intitulado **"Distribuição da Satisfação"** foi concebido para visualizar a proporção de indivíduos satisfeitos e insatisfeitos no conjunto de dados. Ele quantifica a variável alvo, "Satisfação", que é binária, onde o valor 0 representa "Insatisfeito" e 1 representa "Satisfeito".

O gráfico exibe duas barras distintas, cada uma correspondendo a uma categoria de satisfação. A altura de cada barra indica a "Contagem" de indivíduos pertencentes a essa categoria.

- Indivíduos insatisfeitos (0): 1.873
- Indivíduos satisfeitos (1): 3.420

Este gráfico é fundamental para compreender a composição da variável que o modelo tenta prever e identificar um possível **desbalanceamento de classes**. A classe "Satisfeito" (1) é significativamente mais numerosa, o que pode induzir o modelo a prever mais frequentemente esta classe, gerando viés.

> **Impacto no Modelo:**  
> Um modelo treinado com dados desbalanceados pode apresentar alta acurácia geral, mas desempenho ruim para a classe minoritária (insatisfeitos). Para mitigar isso, recomenda-se:
>
> - Oversampling da classe minoritária
> - Undersampling da classe majoritária
> - Aplicação de pesos de classe
> - Avaliação baseada em *Recall* e *F1-score*

---

### 2.2. Distribuição por Faixa Salarial (P2_h) (Imagem 2)

O gráfico de barras horizontais **"Distribuição por Faixa Salarial (P2_h)"** apresenta a distribuição dos participantes por faixa de renda.

- Faixa mais comum: **R$8.001/mês a R$12.000/mês** (mais de 1000 indivíduos)
- Faixas com menor representatividade: **Menos de R$1.000/mês** e **R$101/mês a R$2.000/mês**

> **Importância:**  
> A análise da faixa salarial ajuda a entender o perfil econômico dos indivíduos. A concentração nas faixas intermediárias sugere que a percepção de justiça salarial pode ser um fator relevante para a satisfação. Recomenda-se análise bivariada entre faixa salarial e satisfação.

---

## 3. Avaliação do Modelo de Machine Learning

### 3.1. Matriz de Confusão (Imagem 3)

A matriz de confusão é uma tabela 2x2 que mostra as classificações corretas e incorretas feitas pelo modelo:

| Real \ Previsto | Satisfeito (1) | Insatisfeito (0) |
|-----------------|----------------|------------------|
| Satisfeito (1)  | TP = 730       | FN = 125         |
| Insatisfeito (0)| FP = 241       | TN = 228         |

> **Interpretação:**
>
> - **Falsos Positivos (241):** Indivíduos insatisfeitos previstos como satisfeitos.
> - **Falsos Negativos (125):** Indivíduos satisfeitos previstos como insatisfeitos.
>
> O modelo tem **viés para prever "Satisfeito"**, devido ao desbalanceamento. Isso é crítico se o objetivo for identificar insatisfeitos. O custo de um Falso Positivo (ignorar um insatisfeito) é maior do que o de um Falso Negativo (abordar um satisfeito indevidamente).

> **Recomendações:**
>
> - Ajustar o limiar de decisão
> - Rebalancear as classes
> - Otimizar o *recall* da classe insatisfeito

---

### 3.2. Relatório de Classificação (Imagem 4)

Métricas detalhadas por classe:

| Métrica     | Classe 0 (Insatisfeito) | Classe 1 (Satisfeito) |
|-------------|--------------------------|------------------------|
| Precision   | 0.65                     | 0.75                   |
| Recall      | 0.49                     | 0.85                   |
| F1-score    | 0.55                     | 0.80                   |
| Support     | 469                      | 855                    |

Métricas gerais:

- **Accuracy:** 0.72
- **Macro Avg (F1):** 0.68
- **Weighted Avg (F1):** 0.71

> **Análise:**
>
> A performance é muito melhor para a classe "Satisfeito" do que para "Insatisfeito":
>
> - Apenas **49%** dos insatisfeitos foram corretamente identificados (Recall)
> - Quando o modelo prevê insatisfação, está correto em **65%** das vezes (Precisão)


# Pergunta 2
## Conclusões Gerais

- **Desbalanceamento de Classes:** Afeta negativamente a performance do modelo na classe minoritária.
- **Desempenho Global:** Acurácia razoável (0.72), mas com recall baixo para insatisfeitos (0.49).
- **Principais Fatores de Satisfação:** A variável mais importante foi a **Forma de Trabalho Atual**, seguida por **Novos Talentos**.
- **Overfitting Moderado:** Sugerido pela curva de aprendizado. Há espaço para melhorias com regularização ou novos dados.

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
