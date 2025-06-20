# Resultados



## **Análise das Visualizações do Modelo LightGBM**


### **Desempenho do Modelo LightGBM: Tabela de Resultados**

| Métrica | Classe | Conjunto de Treino | Conjunto de Teste |
| :--- | :--- | :--- | :--- |
| **Acurácia Geral** | N/A | 97% | 96% |
| **AUC-ROC** | N/A | 0.982 | 0.955 |
| **Precisão** | Insatisfeito | 1.00 | 1.00 |
| | Satisfeito | 0.96 | 0.95 |
| **Recall** | Insatisfeito | 0.90 | 0.87 |
| | Satisfeito | 1.00 | 1.00 |
| **F1-Score** | Insatisfeito | 0.95 | 0.93 |
| | Satisfeito | 0.98 | 0.98 |
| **F1-Score (Macro Avg)**| N/A | 0.97 | 0.95 |
### **1. Matrizes de Confusão Comparativas**

**Objetivo:**
A matriz de confusão é uma tabela que permite a visualização do desempenho de um algoritmo de classificação. Ela compara os valores reais com os valores previstos pelo modelo, dividindo as previsões em Verdadeiros Positivos (VP), Verdadeiros Negativos (VN), Falsos Positivos (FP) e Falsos Negativos (FN). O objetivo deste gráfico é avaliar a acurácia do modelo nos dados de treino (o que ele aprendeu) e nos dados de teste (sua capacidade de generalizar).

![download](https://github.com/user-attachments/assets/c4977e77-b62f-4e26-bdeb-2bdb86849dc7)

**Resultado e Análise:**

  * **Conjunto de Treino (Verde):** O modelo demonstrou um ajuste muito forte aos dados de treino, classificando corretamente 842 profissionais como "Insatisfeitos" (VN) e 2394 como "Satisfeitos" (VP). Cometeu apenas 91 erros do tipo Falso Negativo e 0 erros do tipo Falso Positivo.
  * **Conjunto de Teste (Azul):** Em dados não vistos, o modelo identificou corretamente 348 "Insatisfeitos" (VN) e 1026 "Satisfeitos" (VP). Cometeu 52 erros do tipo Falso Negativo, ou seja, previu "Insatisfeito" para profissionais que estavam "Satisfeitos". Notavelmente, assim como no treino, não houve Falsos Positivos.

A performance no teste é extremamente robusta e muito próxima à do treino. O fato de não haver Falsos Positivos para a classe "Insatisfeito" é um resultado excelente, indicando que quando o modelo identifica um profissional como insatisfeito, a confiança nessa previsão é máxima.

-----

### **2. Curva de Aprendizagem do Modelo**

**Objetivo:**
A curva de aprendizado é uma ferramenta de diagnóstico que plota o desempenho do modelo (neste caso, a pontuação F1-Macro) em relação ao número de amostras de treinamento. Ela ajuda a entender se o modelo se beneficia de mais dados e se está sofrendo de sobreajuste (overfitting) ou subajuste (underfitting).

![download](https://github.com/user-attachments/assets/ed1473bf-f9ef-45eb-ad82-d5ff0acd3d69)

**Resultado e Análise:**

  * **Score de Treino (Laranja):** A pontuação nos dados de treino começa muito alta e diminui ligeiramente à medida que mais dados são apresentados, o que é um comportamento esperado.
  * **Score de Validação Cruzada (Azul):** A pontuação em dados de validação aumenta com o volume de dados e se estabiliza em um platô, indicando que o modelo atinge seu desempenho máximo com a quantidade de dados disponível.

O aspecto mais importante é que as duas curvas **convergem** para um ponto onde a diferença (gap) entre elas é pequena. Isso significa que o modelo aprendeu os padrões dos dados de forma eficaz e consegue generalizar esse conhecimento para novos dados, sem estar sobreajustado aos dados de treino.

-----

### **3. Curva ROC Comparativa**

**Objetivo:**
A curva ROC (Receiver Operating Characteristic) avalia a capacidade de um modelo de classificação em distinguir entre as classes. Ela plota a Taxa de Verdadeiros Positivos (sensibilidade) contra a Taxa de Falsos Positivos (1 - especificidade). Um modelo ideal teria uma curva que se aproxima do canto superior esquerdo. A Área sob a Curva (AUC) quantifica essa capacidade: 1.0 é um classificador perfeito e 0.5 é um modelo sem capacidade de discriminação.
![download](https://github.com/user-attachments/assets/b15b2647-f76e-4c9d-9f56-93d03b34f5ed)

**Resultado e Análise:**

  * **Curva de Treino (Azul tracejado):** O AUC de **0.982** é extremamente alto, quase perfeito, mostrando o excelente ajuste do modelo aos dados de treinamento.
  * **Curva de Teste (Laranja):** O AUC no conjunto de teste é de **0.955**, um valor excepcional que indica um alto poder de discriminação do modelo em dados que ele nunca viu antes.
  * **Classificador Aleatório (Cinza pontilhado):** Representa a linha de base (AUC = 0.5), onde o modelo não teria poder preditivo.

A proximidade entre as curvas de treino e teste e os altos valores de AUC reforçam a conclusão de que o modelo LightGBM é robusto, preciso e generaliza muito bem.

-----

### **4. Top 20 Features Mais Importantes**

**Objetivo:**
Este gráfico de barras mostra quais variáveis (features) o modelo LightGBM considerou mais influentes ao tomar suas decisões de classificação. A importância de uma feature é uma medida de quão útil ela foi na construção das árvores de decisão que compõem o modelo.

![download](https://github.com/user-attachments/assets/d5b50986-49f2-4a91-b883-38d5a6112b36)

**Resultado e Análise:**
O gráfico fornece insights valiosos sobre os principais fatores que impulsionam a satisfação profissional:

1.  **Experiencia\_anos:** A variável mais importante, sugerindo que o tempo de experiência é um forte indicador da satisfação ou das expectativas do profissional.
2.  **Falta de oportunidade de crescimento no emprego atual:** O segundo fator mais relevante, destacando que a percepção de desenvolvimento na carreira é crucial para a satisfação.
3.  **Salário atual não corresponde ao mercado:** A questão da remuneração aparece como o terceiro fator mais importante.
4.  **Outros Fatores:** Variáveis como a "falta de maturidade analítica na empresa", "forma de trabalho 100% remoto" e o "clima de trabalho" também são preditores significativos, embora com menor peso que os três primeiros.

Esses resultados são fundamentais para direcionar ações estratégicas, pois indicam que, para reter talentos, uma empresa deve focar não apenas em salário, mas também, e principalmente, em oferecer planos de carreira claros e um ambiente de trabalho estimulante.

---

## **Análise das Visualizações do Modelo XGBoost**

### **Desempenho do Modelo XGBoost: Tabela de Resultados**

A tabela a seguir resume as principais métricas de desempenho do modelo XGBoost, tanto no conjunto de dados utilizado para o seu treinamento quanto no conjunto de teste, que simula dados novos.

| Métrica | Classe | Conjunto de Treino | Conjunto de Teste |
| :--- | :--- | :--- | :--- |
| **Acurácia Geral** | N/A | 97% | 96% |
| **AUC-ROC** | N/A | 0.988 | 0.961 |
| **Precisão** | Insatisfeito | 1.00 | 1.00 |
| | Satisfeito | 0.97 | 0.95 |
| **Recall** | Insatisfeito | 0.91 | 0.87 |
| | Satisfeito | 1.00 | 1.00 |
| **F1-Score** | Insatisfeito | 0.95 | 0.93 |
| | Satisfeito | 0.98 | 0.98 |
| **F1-Score (Macro Avg)**| N/A | 0.97 | 0.95 |

### Análise da Tabela

* **Acurácia e AUC-ROC:** O modelo demonstra uma performance excepcional, com uma acurácia de **96%** e uma Área sob a Curva ROC (AUC-ROC) de **0.961** no conjunto de teste. Estes valores indicam que o modelo é extremamente preciso em suas previsões gerais e possui uma excelente capacidade de distinguir entre profissionais satisfeitos e insatisfeitos.
* **Foco na Classe "Insatisfeito":** Para o problema de negócio (identificar e reter talentos), a performance na classe "Insatisfeito" é crucial. O modelo alcançou:
    * **Precisão de 1.00:** Este é um resultado notável. Significa que, quando o modelo prevê que um profissional está insatisfeito, ele está **100% correto**. Não há falsos positivos para esta classe, o que confere grande confiança às suas previsões.
    * **Recall de 0.87:** O modelo foi capaz de identificar **87%** de todos os profissionais que estavam, de fato, insatisfeitos. Este é um valor muito alto, mostrando que poucos "insatisfeitos" passam despercebidos.
* **Generalização:** A pequena queda de performance entre os conjuntos de treino e teste é um indicativo positivo, mostrando que o modelo não está apenas "decorando" os dados de treino (overfitting), mas sim aprendendo os padrões subjacentes e aplicando-os com sucesso a dados novos.

---

### **Análise dos Melhores Parâmetros Encontrados**

O processo de otimização `RandomizedSearchCV` encontrou a seguinte combinação de hiperparâmetros como a ideal para este problema:

```
{'classifier__subsample': 1.0, 'classifier__reg_lambda': 1, 'classifier__reg_alpha': 0.5, 'classifier__n_estimators': 200, 'classifier__max_depth': 10, 'classifier__learning_rate': 0.05, 'classifier__gamma': 0.25, 'classifier__colsample_bytree': 0.7}
```

A seguir, uma descrição do papel de cada um destes parâmetros no modelo XGBoost:

* **`n_estimators: 200`**: Define que o modelo final é um conjunto (ensemble) composto por 200 árvores de decisão. Cada árvore é construída para corrigir os erros da anterior.
* **`max_depth: 10`**: A profundidade máxima de cada árvore é limitada a 10 níveis. Isso ajuda a controlar a complexidade do modelo e a evitar o sobreajuste, impedindo que as árvores se tornem excessivamente específicas para os dados de treino.
* **`learning_rate: 0.05`**: Esta é a "taxa de aprendizado". Um valor baixo como 0.05 faz com que o modelo dê passos menores e mais cautelosos a cada iteração, tornando o processo de aprendizado mais robusto e menos propenso a erros.
* **`subsample: 1.0`**: Indica que 100% das amostras de dados de treino foram usadas para construir cada árvore.
* **`colsample_bytree: 0.7`**: Para cada árvore construída, apenas uma amostra aleatória de 70% das features (colunas) foi utilizada. Esta técnica ajuda a diversificar as árvores e melhora a capacidade de generalização do modelo.
* **`gamma: 0.25`**: Parâmetro de regularização. Uma nova divisão em um nó da árvore só é feita se a melhoria na função de perda for maior que 0.25. Isso ajuda a "podar" a árvore, evitando a criação de divisões que não agregam valor preditivo significativo.
* **`reg_alpha: 0.5` (Regularização L1)**: Aplica uma penalidade sobre os pesos absolutos das features, o que pode levar alguns pesos a se tornarem zero, efetivamente realizando uma forma de seleção de features.
* **`reg_lambda: 1` (Regularização L2)**: Aplica uma penalidade sobre os pesos ao quadrado das features, o que ajuda a suavizar o modelo e a prevenir o sobreajuste sem necessariamente zerar os pesos.

Em conjunto, esses parâmetros criaram um modelo que é ao mesmo tempo complexo o suficiente para capturar os padrões nos dados (`max_depth=10`, `n_estimators=200`) e robusto o suficiente para evitar o sobreajuste, graças ao uso de múltiplas técnicas de regularização (`gamma`, `reg_alpha`, `reg_lambda`) e amostragem (`colsample_bytree`).

### **1. Matrizes de Confusão Comparativas**

**Objetivo:**
A matriz de confusão é uma ferramenta essencial para visualizar o desempenho de um modelo de classificação. Ela detalha os acertos e erros do modelo, dividindo as previsões em quatro categorias: Verdadeiros Positivos (VP), Verdadeiros Negativos (VN), Falsos Positivos (FP) e Falsos Negativos (FN). O objetivo deste gráfico é comparar lado a lado a performance do modelo nos dados que ele usou para aprender (Treino) e nos dados que ele nunca viu antes (Teste).

![download](https://github.com/user-attachments/assets/bedc4585-2c9e-4c4e-bf8c-2bca37dcd588)

**Resultado e Análise:**

  * **Conjunto de Treino (Verde):** O modelo classificou corretamente 851 profissionais como "Insatisfeitos" (VN) e 2392 como "Satisfeitos" (VP). Ele cometeu apenas 2 erros do tipo Falso Positivo (previu "Satisfeito" para quem estava "Insatisfeito") e 82 erros do tipo Falso Negativo (previu "Insatisfeito" para quem estava "Satisfeito"). Isso demonstra um ajuste muito bom aos dados de treino.
  * **Conjunto de Teste (Azul):** Nos dados de teste, o modelo identificou corretamente 349 "Insatisfeitos" (VN) e 1026 "Satisfeitos" (VP). Os erros foram de 0 Falsos Positivos e 51 Falsos Negativos.

A performance no teste é excelente e muito próxima à do treino, indicando que o modelo tem uma ótima capacidade de **generalização** e não está sofrendo de sobreajuste (overfitting). O número zero de Falsos Positivos no teste é um resultado notável, significando que quando o modelo aponta alguém como "Insatisfeito", ele tem 100% de certeza.

-----

### **2. Curva de Aprendizagem do Modelo**

**Objetivo:**
A curva de aprendizado avalia como a performance de um modelo se comporta à medida que mais dados de treinamento são adicionados. Ela plota a pontuação do modelo (neste caso, F1-Macro) tanto para o conjunto de treino quanto para um conjunto de validação cruzada. O objetivo é diagnosticar problemas como sobreajuste (overfitting) ou subajuste (underfitting).

**Resultado e Análise:**

  * **Score de Treino (Laranja):** A linha laranja mostra que, com poucos dados, o modelo se ajusta perfeitamente a eles (alta pontuação), e essa pontuação diminui ligeiramente e se estabiliza à medida que mais dados são adicionados.
  * **Score de Validação Cruzada (Azul):** A linha azul mostra que a performance do modelo em dados não vistos aumenta significativamente com mais dados, até atingir um platô.
  * 
![download](https://github.com/user-attachments/assets/d84c32b5-8519-429d-87c6-1aed55bce78f)

O resultado mais importante é a **convergência** das duas curvas. Elas terminam próximas uma da outra, com uma pequena diferença (gap) entre elas. Isso indica que o modelo é robusto e não está nem sobreajustado (gap muito grande) nem subajustado (ambas as pontuações baixas). Em outras palavras, o modelo aprendeu bem os padrões dos dados e consegue aplicar esse aprendizado a novos dados com eficácia.

-----

### **3. Curva ROC Comparativa**

**Objetivo:**
A curva ROC (Receiver Operating Characteristic) é uma visualização que mede a capacidade de um modelo em distinguir entre as classes (neste caso, "Satisfeito" e "Insatisfeito"). Ela plota a Taxa de Verdadeiros Positivos (TPR) contra a Taxa de Falsos Positivos (FPR). Quanto mais a curva se aproxima do canto superior esquerdo, melhor é o desempenho do modelo. A área sob a curva (AUC) é uma métrica que resume essa capacidade: um valor de 1.0 representa um classificador perfeito, e 0![download](https://github.com/user-attachments/assets/17dbd4df-f001-4533-a3d7-19ef6bbee6ec)
.5, um classificador aleatório.

**Resultado e Análise:**

![download](https://github.com/user-attachments/assets/6b29ae98-59af-43eb-9c9e-ce12a18ffe47)

  * **Curva de Treino (Azul tracejado):** Apresenta um AUC de **0.988**, o que é quase perfeito, indicando um excelente ajuste aos dados de treinamento.
  * **Curva de Teste (Laranja):** O AUC no conjunto de teste é de **0.961**, um valor extremamente alto.
  * **Classificador Aleatório (Cinza pontilhado):** A linha diagonal representa um modelo sem poder preditivo algum.

A pequena diferença entre o AUC de treino e o de teste reforça a conclusão da curva de aprendizado: o modelo XGBoost é altamente discriminativo e generaliza muito bem seu aprendizado para dados novos.

-----

### **4. Top 20 Features Mais Importantes**

**Objetivo:**
Este gráfico tem como objetivo identificar quais variáveis (features) o modelo XGBoost considerou mais importantes para fazer suas previsões. A "importância" é calculada com base em quantas vezes uma feature foi utilizada para dividir os dados nas árvores de decisão do modelo e o quanto essa divisão melhorou a performance.

![download](https://github.com/user-attachments/assets/117a541a-a1b3-4014-938f-1702b5449bbc)


**Resultado e Análise:**
O gráfico revela de forma clara os principais fatores que influenciam a satisfação profissional, segundo o modelo:

1.  **Falta de oportunidade de crescimento no emprego atual:** É, de longe, a variável mais importante. Isso sugere que a percepção de estagnação na carreira é o principal motivo de insatisfação.
2.  **Falta de maturidade analítica na empresa:** Este fator aparece em segundo lugar, indicando que profissionais de dados valorizam um ambiente onde seu trabalho é bem compreendido e utilizado de forma estratégica.
3.  **Salário atual não corresponde ao mercado:** A remuneração é o terceiro fator mais relevante, confirmando sua importância, mas ficando atrás de questões de carreira e cultura de dados.
4.  **Fatores Relacionais e Benefícios:** Variáveis como "clima de trabalho", "gostaria de receber mais benefícios" e "não tenho uma boa relação com meu líder" também aparecem com importância significativa, embora menor que os três primeiros.

Este gráfico é fundamental para gerar insights acionáveis, pois aponta exatamente onde uma empresa deve focar seus esforços para melhorar a retenção e satisfação de seus profissionais.
-----

