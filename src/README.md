# Código do projeto


## 1. [Árvore de Decisão](/src/Modelos_Corrigidos/ArvoreDeDecisao.ipynb)
A Árvore de Decisão é um modelo de aprendizado supervisionado utilizado para classificação. Ele funciona criando uma estrutura de "árvore" onde cada nó interno representa um teste em um atributo (ex: "Qual a forma de trabalho atual?") e cada folha representa uma classe final (satisfeito ou insatisfeito).

* **Objetivo no Projeto:** Criar um modelo preditivo para classificar a satisfação dos profissionais de dados, com a vantagem de ser facilmente interpretável (um modelo "caixa branca"), permitindo entender as regras de decisão.
* **Como Funciona:** O algoritmo divide recursivamente os dados em subconjuntos cada vez mais puros, com base em critérios como o Índice Gini ou Entropia, para maximizar a homogeneidade em relação à variável alvo (satisfação).
* **Resultados Principais:**
    * **Acurácia:** 72%
    * **AUC (Curva ROC):** 0.73
    * **Principais Fatores:** Forma de trabalho atual e oportunidades para novos talentos.
    * **Ponto Fraco:** Teve dificuldade em prever corretamente os profissionais insatisfeitos (recall de 49%).

---

## 2. [Random Forest](/src/Modelos_Corrigidos/RandonFlorest.ipynb)

O Random Forest é um modelo de conjunto (*ensemble*) que aprimora a Árvore de Decisão. Em vez de criar uma única árvore, ele constrói várias árvores de decisão independentes em subconjuntos aleatórios dos dados e das features. A previsão final é feita por uma "votação" majoritária entre todas as árvores.

* **Objetivo no Projeto:** Alcançar uma classificação com maior precisão e capacidade de generalização, mitigando o *overfitting* (sobreajuste) que pode ocorrer em uma única Árvore de Decisão.
* **Como Funciona:** Combina a aleatoriedade na seleção de amostras de dados (técnica de *bagging*) e na seleção de features em cada nó. Isso garante que as árvores sejam diversas, resultando em um modelo final mais robusto e estável.
* **Resultados Principais:**
    * **Acurácia:** 77%
    * **AUC (Curva ROC):** 0.79
    * **Principais Fatores:** Faixa salarial, tempo na área de dados e forma de trabalho atual.
    * **Ponto Forte:** Superou a Árvore de Decisão em todas as métricas, mostrando uma melhor capacidade de prever tanto os profissionais satisfeitos (recall de 89%) quanto os insatisfeitos (recall de 55%).

### Comparação e Conclusão

| Métrica | Árvore de Decisão | Random Forest | Vantagem |
| :--- | :--- | :--- | :--- |
| **Acurácia** | 72% | **77%** | **Random Forest** |
| **AUC** | 0.73 | **0.79** | **Random Forest** |
| **Interpretabilidade**| Alta ("caixa branca") | Baixa ("caixa preta") | **Árvore de Decisão** |
| **Robustez** | Menor | **Maior** | **Random Forest** |

Em resumo, o **Random Forest foi o modelo superior em termos de desempenho preditivo**, oferecendo maior acurácia e sendo mais eficaz na identificação de profissionais insatisfeitos. A **Árvore de Decisão**, embora menos precisa, oferece a vantagem de ser mais fácil de interpretar. Para uma aplicação prática que busca a máxima precisão, o **Random Forest é a escolha preferível**.
