# Desafios Para Profissionais Juniores e Microempresas no Uso de Dados e Tecnologia, IA Generativa e LLM’S.

---

**Caio César de Oliveira, caio.oliveira.1551586@sga.pucminas.br**

**Caio Baltar Souza Mayllart, caio.baltar@sga.pucminas.br**

**Gabriel Fernandes Souza , gabriel.souza@sga.pucminas.br**

**Nicolas Rodrigues Duarte email do aluno 3**

**Thiago Domingos Venturim Ribeiro dos Santos,  tdvrsantos@sga.pucminas.br**

---

**Professores:**

* **Prof. Hugo Bastos de Paula**

* **Prof. Hayala Nepomuceno Curto**

---

_Curso de Ciência de Dados, Unidade Praça da Liberdade_

_Instituto de Informática e Ciências Exatas – Pontifícia Universidade de Minas Gerais (PUC MINAS), Belo Horizonte – MG – Brasil_

---

_**Resumo**:

Este trabalho analisa os desafios enfrentados por profissionais juniores e microempresas brasileiras na adoção da Inteligência Artificial Generativa (IA Generativa) e Large Language Models (LLMs). Com base em dados do "State of Data Brazil 2023" e microdados da educação superior, o estudo investiga fatores que influenciam a satisfação profissional e a competitividade das microempresas no contexto da IA.

Para isso, foram induzidos modelos de machine learning, como a Árvore de Decisão, para identificar os principais fatores que explicam a satisfação dos profissionais da área de dados. O processo envolveu rigoroso pré-processamento dos dados, treinamento, validação e otimização dos modelos, além da comparação entre diferentes abordagens para garantir resultados confiáveis e interpretáveis.

Os resultados indicam que fatores como experiência, acesso a ferramentas avançadas e capacitação são determinantes para a inserção e satisfação no mercado de IA Generativa, especialmente para perfis juniores e pequenos negócios_


*******
   <h3 align="center"><strong> SUMARIO </strong></h3>
   
[1. Introdução](#Introdução)   

[2. Contextualização](#Contextualização)

[3. Problema](#Problema)

[4. Pergunta Direcionada a Dados](#Pergunta_Direcionada_a_Dados)

[5. Objetivos](#Objetivos)

[6.Justificativas ](#Justificativas)

[7. Público alvo](#Público_alvo)

[8. Análise exploratórida dos dados](#Análise_exploratórida_dos_dados)

[9. Preparação dosdados](#Preparação_dos_dados)

[10. Indução de modelos]
* [10.1 Indução de Modelo 1](#Indução_de_modelo_1)
* [10.2 Indução de  Modelo 2](#Indução_de_modelo_2))

[11. Resultados ]
* [11.1 Resultado Modelo 1 ](#Resultado_1)
* [11.2 Resultados Modelo 2 ](#Resultados_2)
  
[12. Comparaçôes ](#Comparacoes)



[13. Conclusão ](#Conclusão)

[14. Referências ](#REFERÊNCIAS)

[15. Apêndices](#APÊNDICES)



*******
<div id='Introdução'/>  

 <h3 align="center"><strong> Introdução </strong></h3>

A Inteligência Artificial Generativa transformou profundamente diversos setores, impulsionando a automação e a inovação na criação de conteúdo. Modelos avançados, como os Large Language Models (LLMs), vêm sendo incorporados ao cotidiano de empresas e profissionais, ampliando possibilidades e redefinindo o uso de dados no mercado de tecnologia. No entanto, apesar do avanço dessas soluções, sua adoção ainda enfrenta barreiras significativas, especialmente para profissionais juniores e microempresas no Brasil.

---

<div id='Contextualização'/>  

   <h3 align="center"><strong> Contextualização </strong></h3>

A Inteligência Artificial (IA) tem se tornado uma das tecnologias mais disruptivas da atualidade, impactando setores como saúde, finanças, indústria e educação. Dentro desse campo, a Inteligência Artificial Generativa (IA Generativa) destaca-se pela capacidade de criar conteúdos inéditos, como textos, imagens, códigos e até modelos preditivos. Ferramentas baseadas em Large Language Models (LLMs), como os ChatBots, vêm sendo amplamente adotadas por empresas para otimizar processos, melhorar a comunicação e impulsionar a inovação.

Entretanto, a adoção dessas tecnologias ainda enfrenta desafios significativos, especialmente para profissionais juniores e microempresas. De acordo com o State of Data Brasil – 2023, 72% dos profissionais iniciantes relatam dificuldades para ingressar no mercado de IA devido à exigência de experiência e acesso limitado a ferramentas avançadas. Já as microempresas, que representam cerca de 30% do PIB brasileiro (Sebrae, 2022), encontram barreiras financeiras e estruturais para implementar soluções de IA de forma competitiva.

Esse cenário reforça a necessidade de analisar as dificuldades enfrentadas por esses grupos e propor soluções que ampliem o acesso à IA Generativa. A democratização dessas tecnologias pode reduzir desigualdades no setor, facilitar a inserção de novos talentos no mercado e impulsionar o crescimento de pequenos negócios.

Diante desse contexto, este estudo busca explorar os desafios e oportunidades da IA Generativa para profissionais juniores e microempresas no Brasil. Por meio da análise de dados do mercado de trabalho e do ecossistema empreendedor, pretende-se desenvolver um sistema inteligente que forneça insights e recomendações para facilitar a adoção dessas tecnologias, promovendo um ambiente mais acessível e inclusivo.

A presente pesquisa é o resultado de um esforço conjunto da Data Hackers, a maior comunidade de dados do Brasil, e da Bain & Company, consultoria global que ajuda empresas e organizações a promover mudanças que definam o futuro dos negócios, para mapear o mercado de trabalho de dados no Brasil.

A pesquisa foi realizada entre 16 de outubro de 2023 e 6 de dezembro de 2023 através de um questionário online e contou com 5.293 respondentes em todo o Brasil, um aumento de 24% em relação ao número de respondentes da última edição. Os dados incluem indicadores relacionados a perfil demográfico, formação, atuação no setor, remuneração, rotatividade e fatores de satisfação no ambiente de trabalho, incluindo o impacto do trabalho remoto e layoffs. Uma novidade dessa edição da pesquisa foram perguntas com a intenção de medir o uso de tecnologias de IA Generativa e LLMs pelas empresas e seus profissionais. A amostra reflete a visão de variados papéis de atuação em empresas, como os de analista de dados, cientista de dados e engenheiro de dados, bem como diferentes perfis de experiência profissional, incluindo analistas júnior, pleno, sênior e gestores.

---

<div id='Problema'/>  
  <h3 align="center"><strong>  Problema </strong></h3>

As dificuldades de acesso e implementação de tecnologias de IA Generativa por profissionais juniores e microempresas no Brasil, devido a barreiras financeiras, estruturais e à exigência de experiência prévia no mercado. Esse problema destaca como a falta de recursos e a exigência de qualificação avançada dificultam a adoção dessas tecnologias por grupos com menos capital e experiência, limitando sua competitividade e crescimento no setor de Inteligência Artificial.

---
<div id='Pergunta_Direcionada_a_Dados'/>  
    <h3 align="center"><strong>  Pergunta Direcionada a Dados  </strong></h3> 

* Quais são as principais satisfações dos profissionais boas ou rins? 
* Quais fatores (salário, experiência, ferramentas utilizadas) influenciam essas inserções profissionais no mercado? 
* As microempresas têm acesso às mesmas tecnologias e recursos que as grandes empresas?
* Como a adoção da IA Generativa impacta a competitividade das microempresas? 
* Quais habilidades e conhecimentos são mais valorizados no mercado para quem deseja atuar com IA Generativa?
  
---

<div id='Objetivos'/>  
   <h3 align="center"><strong> Objetivo geral  </strong></h3> 

 Desenvolver um sistema inteligente que analise dados do mercado de trabalho e de microempresas para identificar os principais desafios enfrentados por profissionais juniores e pequenos negócios na adoção da IA ​​Generativa, propondo soluções baseadas em insights obtidos

---

   <h3 align="center"><strong> Objetivos específicos   </strong></h3> 

 Avaliar o impacto da adoção da IA ​​Generativa na competitividade de microempresas.
Investigar os fatores que influenciam a valorização profissional na área, como experiência, habilidades e acesso a ferramentas.

---

<div id='Justificativas'/>  
   <h3 align="center"><strong> Justificativas  </strong></h3> 
 A IA Generativa não é apenas uma tendência – é uma revolução que está transformando a forma como empresas inovam, automatizam processos e se destacam no mercado. No entanto, o acesso a essa tecnologia de ponta ainda é restrito para dois grupos com enorme potencial de crescimento: profissionais juniores e microempresas.
 Por isso, desenvolvemos uma Inteligência Artificial exclusiva projetada para quebrar essas barreiras e tornar a IA Generativa acessível a todos. Imagine um sistema que capacita profissionais em início de carreira com ferramentas avançadas, permitindo que eles se destaquem no mercado de trabalho, e que oferece a microempresas soluções inteligentes para automatizar processos, reduzir custos e competir de igual para igual com grandes corporações.
 Com essa IA inovadora, facilitamos o acesso a tecnologias de ponta, impulsionamos a competitividade de pequenos negócios e abrimos novas oportunidades para talentos emergentes. Estamos criando um futuro mais inclusivo, eficiente e preparado para os desafios da transformação digital no Brasil.

---

<div id='Público_alvo'/>  
    <h3 align="center"><strong>  Público alvo   </strong></h3> 
A aplicação será utilizada principalmente por dois perfis principais: profissionais juniores da área de tecnologia e inteligência artificial e microempresas que trabalham com dados e tecnologias e buscam adotar IA Generativa.

* Profissionais Juniores em IA e Tecnologia:
  
Estudantes e recém-formados em Ciência de Dados, Inteligência Artificial, Análise e Desenvolvimento de Sistemas, entre outros
Possuem conhecimentos básicos ou intermediários sobre IA, mas enfrentam barreiras como exigência de experiência prévia e acesso
Buscar informações sobre habilidades valorizadas no mercado, oportunidades de capacitação e formas de entrada no setor de IA Generativ

* Microempresas e Pequenos Negócios:
  
Pequenos empreendedores e startups que desejam incorporar IA Generativa 
Geralmente possuem conhecimento limitado sobre as tecnologias de IA e seu aplicativo
Enfrentam dificuldades financeiras e estruturais para investir em soluções de IA e capacitação da equipe.

---
<div id='Análise_exploratórida_dos_dados'/>  
  <h3 align="center"><strong>  Análise exploratórida dos dados  </strong></h3>


## Base principal: **State of Data Brazil 2023**
A base "State of Data Brazil 2023" coleta informações demográficas e sobre a carreira de profissionais de dados no Brasil, como idade, gênero, cor/raça/etnia, experiência profissional e aspectos da carreira, como oportunidades de emprego e progressão na carreira. Esses dados ajudam a analisar as dificuldades de inclusão e as barreiras enfrentadas por profissionais juniores, permitindo um foco nos desafios de inserção no mercado de IA Generativa, como a falta de acesso a oportunidades e a desigualdade em processos seletivos.

 [**Dicionário de dados - State of Data Brazil 2023**](data_dictionary/raw_database/state_of_data_dictionary.md)

 [**Descrição de dados - State of Data Brazil 2023**](imagens/graficos/graficos_state_of_data.md)

--- 

## Base auxiliar:  **Microdrados Educação Superior**
 A base "MICRODADOS_ED_SUP_IES 2023" reúne dados sobre instituições de ensino superior no Brasil, como localização geográfica, tipo de instituição e rede de ensino (pública ou privada). Ela é crucial para entender a distribuição e a oferta de cursos de educação superior, especialmente em áreas relacionadas à IA Generativa.

 [**Dicionário de dados - MICRODADOS_ED_SUP_IES**](data_dictionary/raw_database/microdados_ed_sup_ies_dictionary.md)

 [**Descrição de dados - MICRODADOS_ED_SUP_IES_2023**](imagens/graficos/graficos_microdados.md)

---

<div id='Preparação_dos_dados'/>  
 <h3 align="center"><strong> Preparação dos dados  </strong></h3> 

	
O código realiza a limpeza dos microdados removendo colunas irrelevantes, renomeando variáveis e padronizando categorias. Também trata valores nulos e converte tipos de dados para análises consistentes. Por fim, exporta o dataset limpo para uso posterior.
## Dados Processados State of Data 2023

Limpeza e Seleção de dados da base State of Data Brazil 2023, este notebook é responsável por realizar a limpeza, tratamento e pré-processamento dos dados brutos da pesquisa, preparando o dataset para análises exploratórias e estatísticas. 

[Acesse o dicionario de dados do State of Data](data_dictionary/cleaned_dictionary/state_of_data_cleaned_dictionary.md)


## Dados Processados Microdrados Educação Superior
Limpeza e Seleção de dados da base Microdrados Educação Superior 2023, este notebook trata da limpeza, padronização e preparação dos microdados da pesquisa. O foco está em garantir que os dados estejam prontos para análises refinadas, especialmente voltadas para recortes demográficos, socioeconômicos e regionais.

[Acesse o dicionario de dados da Análise do MICRODADOS_ED_SUP_IES_2023](data_dictionary/cleaned_dictionary/microdados_cleaned_dictionary.md)


## Unificação das bases
Junção das bases MICRODADOS_ED_SUP_IES_2023 e State of Data Brazil 2023 limpas e selecionadas: Análise do Ensino Superior Consolidada e Dados_processados

[Acesse o dicionario de dados da Análise dos Dados Unidos](data_dictionary/cleaned_dictionary/bases_unidas_dictionary.md)

[Acesse os gráficos da Análise dos Dados Unidos](imagens/graficos/graficos_bases_unificadas.md)


---

<div id='Indução_de_modelos'/>  
	
 <h3 align="center"><strong> Indução de modelos  </strong></h3> 

**A pergunta escolhida foi: Quais são os principais fatores que explicam a satisfação (ou insatisfação) dos profissionais da área de dados no Brasil?**

## 1\. Modelo de Árvore de Decisão

<div id='Indução_de_modelos_1'/>  
	
###  Indução do Modelo

O modelo de Árvore de Decisão é desenvolvido para lidar com problemas de classificação, conforme implementado no notebook "Pergunta1ArvoreDeDecisao.ipynb". O processo de indução (treinamento) do modelo segue as seguintes etapas rigorosas:

1.  **Importação de Bibliotecas:** Inicia-se com a importação de bibliotecas essenciais para a manipulação de dados (Pandas, NumPy), visualização de dados (Matplotlib, Seaborn), processamento de linguagem natural (NLTK, WordCloud) e, crucialmente, para o desenvolvimento de modelos de Machine Learning (Scikit-learn). A inclusão de ferramentas para balanceamento de dados (SMOTE) sugere a atenção a possíveis desequilíbrios de classe no dataset.
2.  **Carregamento e Pré-processamento de Dados:**
      * **Carregamento:** O dataset utilizado é "State\_of\_data\_BR\_2023\_Kaggle - df\_survey\_2023.csv", que serve como base para o aprendizado do modelo.
      * **Limpeza e Transformação:** Uma fase crítica de pré-processamento é executada, incluindo o tratamento de valores ausentes para garantir a integridade dos dados e a codificação de variáveis categóricas (notadamente, One-Hot Encoding) para que o algoritmo possa interpretá-las numericamente. Potenciais normalizações ou padronizações de *features* também podem ser aplicadas, dependendo da natureza dos dados.
      * **Definição de Variáveis:** São claramente definidas as variáveis independentes (*features*, representadas por $X$) e a variável dependente (*target*, representada por $y$), que é o atributo a ser previsto pelo modelo.
3.  **Divisão de Dados:** O dataset é particionado em conjuntos de treinamento e teste. Esta divisão é fundamental para avaliar a capacidade de generalização do modelo em dados não vistos, mitigando o risco de *overfitting*.
4.  **Treinamento do Modelo:** Uma instância do classificador `DecisionTreeClassifier` é criada e treinada utilizando os dados de treinamento. Este passo é o cerne da construção do modelo, onde o algoritmo aprende os padrões e as regras de decisão a partir dos dados.
5.  **Validação do Modelo:** A performance do modelo treinado é rigorosamente avaliada no conjunto de teste. São empregadas métricas de classificação padrão, tais como *accuracy score*, *precision*, *recall*, *F1-score* e a *matriz de confusão*. Estas métricas fornecem uma visão abrangente do desempenho do modelo em diversas perspectivas.
6.  **Otimização de Hiperparâmetros:** Para aprimorar o desempenho do modelo, emprega-se `GridSearchCV`. Esta técnica explora sistematicamente diferentes combinações de hiperparâmetros (e.g., `max_depth`, `min_samples_split`, `criterion`) e seleciona aquelas que resultam no melhor desempenho, geralmente medido por validação cruzada.
7.  **Visualização da Árvore:** Um aspecto distintivo do modelo de Árvore de Decisão é sua interpretabilidade. O notebook permite a visualização gráfica da árvore de decisão treinada, o que é inestimável para compreender as regras lógicas que o modelo estabelece para classificar as instâncias.

### Tipo de Problema e Modelo Escolhido

  * **Tipo de Problema:** O problema em questão é de **classificação**. A utilização de `DecisionTreeClassifier` e as métricas de avaliação empregadas confirmam que o objetivo é prever uma variável categórica.
  * **Modelo Escolhido:** **Árvore de Decisão**.

###  Funcionamento do Algoritmo: Árvore de Decisão

A Árvore de Decisão é um algoritmo de aprendizado supervisionado não-paramétrico, capaz de resolver tanto problemas de classificação quanto de regressão. Para problemas de classificação, seu funcionamento baseia-se em um processo de divisão recursiva dos dados:

1.  **Nó Raiz e Divisão Recursiva:** O processo se inicia com um nó único (a raiz) que engloba a totalidade dos dados. A cada nó, o algoritmo busca o melhor critério (ou "pergunta") para particionar os dados em subconjuntos mais homogêneos em relação à variável alvo.
2.  **Critérios de Impureza:** As divisões são determinadas pela otimização de métricas de impureza, como a **Entropia** (que mede a desordem ou incerteza em um conjunto de dados) ou o **Índice Gini** (que calcula a probabilidade de um elemento escolhido aleatoriamente ser classificado incorretamente). O algoritmo seleciona a divisão que maximiza o ganho de informação ou minimiza a impureza de cada nó.
3.  **Nós Internos e Folhas:** O processo de divisão prossegue recursivamente, formando nós internos que representam testes em atributos específicos e ramos que denotam os resultados desses testes. Quando um nó não pode ser mais dividido de forma significativa (ou atinge um critério de parada, como profundidade máxima), ele se torna um "folha", que é um nó terminal da árvore e representa a classe prevista.
4.  **Processo de Previsão:** Para classificar uma nova instância, a árvore é percorrida a partir do nó raiz, seguindo os caminhos ditados pelos valores dos atributos da instância. A classe associada à folha alcançada é a previsão do modelo.
5.  **Poda (*Pruning*):** Para combater o *overfitting*, técnicas de poda podem ser aplicadas. A poda envolve a remoção de ramos da árvore que não contribuem significativamente para a performance de generalização ou que resultam de ruído nos dados de treinamento.



<div id='Resultado_1'/>  
	
### Resultados Obtidos (Árvore de Decisão)

O notebook evidencia que a avaliação do modelo de Árvore de Decisão foi realizada por meio de `accuracy_score`, `classification_report` e `confusion_matrix`. A utilização de `GridSearchCV` para otimização de hiperparâmetros indica um esforço sistemático para encontrar a configuração ótima do modelo.

Para uma análise quantitativa completa, seria essencial a apresentação dos valores numéricos exatos das métricas de acurácia, precisão, recall, F1-score e da matriz de confusão. Contudo, a metodologia empregada sugere uma avaliação compreensiva da performance do modelo.

### 1.5. Objetivo do Modelo (Árvore de Decisão)

O objetivo primordial do modelo de Árvore de Decisão, neste contexto, é **desenvolver um sistema preditivo capaz de classificar novas instâncias com base nos padrões e regras de decisão inferidos a partir dos dados de treinamento**. Além da capacidade preditiva, a Árvore de Decisão oferece a vantagem intrínseca de ser um modelo "caixa branca", permitindo a interpretação das regras de decisão que o modelo estabelece, o que é valioso para a compreensão do domínio do problema e para a comunicação das decisões.

-----

## 2. Modelo Random Forest

<div id='Indução_de_modelo_2'/>  
	
### Indução do Modelo

O modelo Random Forest, implementado no notebook "Pergunta1RandonFlorest.ipynb", também é projetado para problemas de classificação. A indução deste modelo, um método de *ensemble*, incorpora as seguintes fases:

1.  **Importação de Bibliotecas:** Semelhante ao modelo anterior, são importadas as bibliotecas necessárias para manipulação de dados, visualização e, especificamente, para Machine Learning, com destaque para o `RandomForestClassifier`.
2.  **Carregamento e Pré-processamento de Dados:**
      * **Carregamento:** Utiliza-se o mesmo dataset ("State\_of\_data\_BR\_2023\_Kaggle - df\_survey\_2023.csv"), garantindo consistência na base de dados para comparação entre os modelos.
      * **Limpeza e Codificação:** O pré-processamento de dados é repetido, incluindo a limpeza e a codificação de variáveis categóricas, assegurando que os dados estejam em um formato adequado para o treinamento do algoritmo.
      * **Definição de Variáveis:** As *features* ($X$) e a variável *target* ($y$) são definidas de forma análoga.
3.  **Divisão de Dados:** O dataset é segmentado em conjuntos de treinamento e teste para permitir uma avaliação imparcial da generalização do modelo.
4.  **Treinamento do Modelo:** Uma instância do `RandomForestClassifier` é criada e treinada com os dados de treinamento. Diferentemente da Árvore de Decisão única, este passo envolve o treinamento de múltiplas árvores de decisão.
5.  **Validação Cruzada Estratificada:** O notebook demonstra uma prática robusta de avaliação através da utilização de `StratifiedKFold` e `cross_val_score`. A validação cruzada estratificada é crucial para garantir que as proporções das classes na variável *target* sejam preservadas em cada *fold* (subconjunto de dados), fornecendo uma estimativa mais confiável e menos enviesada do desempenho do modelo.
6.  **Otimização de Hiperparâmetros:** A otimização de hiperparâmetros para o `RandomForestClassifier` é realizada via `GridSearchCV`. Hiperparâmetros como `n_estimators` (número de árvores), `max_depth` (profundidade máxima de cada árvore), `min_samples_split` e `criterion` são ajustados para maximizar o desempenho do modelo.
7.  **Curva de Aprendizagem:** A inclusão de uma curva de aprendizagem é um diagnóstico valioso. Ela ilustra como o desempenho do modelo varia com o aumento do volume de dados de treinamento, auxiliando na identificação de problemas de viés ou variância e na determinação se mais dados seriam benéficos.

###  Tipo de Problema e Modelo Escolhido

  * **Tipo de Problema:** Assim como no caso da Árvore de Decisão, o problema abordado é de **classificação**, visando a predição de uma variável categórica.
  * **Modelo Escolhido:** **Random Forest**.

###  Funcionamento do Algoritmo: Random Forest

Random Forest é um algoritmo de *ensemble* que aprimora a robustez e a acurácia das previsões ao combinar a força de múltiplas Árvores de Decisão. Ele opera com base em dois princípios fundamentais:

1.  **Bagging (*Bootstrap Aggregating*):**

      * **Amostragem com Reposição:** Para a construção de cada árvore na "floresta", um subconjunto aleatório dos dados de treinamento é selecionado **com reposição** (amostragem *bootstrap*). Isso significa que uma mesma instância pode ser selecionada várias vezes para o treinamento de uma árvore, enquanto outras podem não ser selecionadas.
      * **Diversidade das Árvores:** O *bagging* assegura que cada árvore seja treinada em um conjunto de dados ligeiramente distinto, promovendo a diversidade entre as árvores constituintes do *ensemble*.

2.  **Seleção Aleatória de *Features*:**

      * Em cada nó de cada árvore, em vez de considerar todas as *features* disponíveis para encontrar a melhor divisão, o algoritmo considera apenas um **subconjunto aleatório** das *features*. Esta aleatoriedade adicional força as árvores a serem ainda mais distintas e independentes, prevenindo que uma única *feature* dominante monopolize as decisões em todas as árvores.

3.  **Votação Majoritária (para Classificação):**

      * Após o treinamento, quando uma nova instância precisa ser classificada, cada árvore individual na floresta faz sua própria previsão.
      * Para problemas de classificação, o Random Forest agrega as previsões de todas as árvores por meio de um processo de "votação majoritária". A classe que recebe o maior número de votos das árvores individuais é a previsão final do modelo Random Forest.

A combinação desses mecanismos permite que o Random Forest supere a propensão ao *overfitting* e à alta variância das Árvores de Decisão individuais, resultando em um modelo mais estável e com maior poder preditivo.

<div id='Resultado_2'/>  
###  Resultados Obtidos (Random Forest)

O notebook demonstra que o modelo Random Forest foi avaliado por meio de validação cruzada estratificada e otimização de hiperparâmetros via `GridSearchCV`. A inclusão de uma curva de aprendizagem oferece *insights* valiosos sobre o comportamento do modelo em relação ao volume de dados de treinamento.

Similar ao modelo de Árvore de Decisão, a ausência dos valores numéricos exatos das métricas de desempenho no resumo impede uma análise quantitativa precisa. Contudo, a metodologia de avaliação empregada é robusta e indica um esforço para otimizar e validar o modelo de forma adequada.

### 2.5. Objetivo do Modelo (Random Forest)

O objetivo do modelo Random Forest é análogo ao da Árvore de Decisão: **classificar novas instâncias com alta acurácia e capacidade de generalização**. No entanto, o Random Forest busca alcançar este objetivo de forma mais robusta e eficaz, mitigando o *overfitting* e, consequentemente, fornecendo previsões mais confiáveis em dados não vistos, graças à sua arquitetura de *ensemble*. Ele visa aproveitar a "sabedoria da multidão" de múltiplas árvores para construir um preditor mais poderoso.

-----

##  Justificativa da Escolha do Modelo

Diante da análise dos dois modelos, e considerando um cenário típico de projetos de Machine Learning onde a **robustez e a acurácia preditiva são prioritárias**, o **Random Forest** emerge como a escolha mais vantajosa para o problema de classificação em questão.

**Justificativa Detalhada:**

A **Árvore de Decisão**, embora ofereça uma notável interpretabilidade e simplicidade, é inerentemente suscetível ao *overfitting*. Uma única árvore pode se ajustar excessivamente aos detalhes e ruídos dos dados de treinamento, resultando em uma capacidade limitada de generalização para dados novos e não vistos. Pequenas variações no conjunto de treinamento podem levar a estruturas de árvore drasticamente diferentes, tornando o modelo instável.

Em contrapartida, o **Random Forest**, por ser um método de *ensemble*, endereça diretamente essas limitações através de sua arquitetura:

1.  **Redução Efetiva do *Overfitting*:** Ao construir múltiplas árvores em subconjuntos aleatórios de dados (*bagging*) e considerar apenas um subconjunto aleatório de *features* em cada nó (*random subspace method*), o Random Forest reduz significativamente a variância do modelo. Essa diversidade entre as árvores componentes minimiza o risco de que o *ensemble* como um todo se ajuste excessivamente a ruídos ou especificidades dos dados de treinamento.
2.  **Acurácia e Robustez Superior:** A agregação das previsões de múltiplas árvores por meio de votação majoritária tende a suavizar as previsões individuais e a reduzir o erro geral. Isso geralmente resulta em uma acurácia preditiva substancialmente maior e um modelo mais robusto a flutuações nos dados em comparação com uma única Árvore de Decisão.
3.  **Versatilidade no Manuseio de Dados:** O Random Forest é intrinsecamente capaz de lidar com uma ampla gama de tipos de dados, incluindo variáveis categóricas e numéricas, sem a necessidade de uma normalização ou escalonamento extensivo. Ele também é robusto a *outliers* e *missing values* (quando tratado adequadamente).
4.  **Importância de *Features*:** Embora seja considerado um modelo "caixa preta" em termos de interpretabilidade das regras de decisão individuais, o Random Forest pode fornecer uma medida da importância das *features*. Esta métrica indica quais variáveis contribuíram mais para as decisões do modelo, oferecendo *insights* valiosos sobre a relevância preditiva de cada atributo.

Para um problema de classificação onde a performance preditiva e a robustez são critérios de sucesso críticos, o Random Forest apresenta um equilíbrio otimizado entre esses fatores, justificando sua escolha como o modelo preferencial.



<div id='Comparacoes'/>  
	
##  Comparação Final entre Árvore de Decisão e Random Forest

A tabela a seguir resume as principais características e diferenças entre os modelos de Árvore de Decisão e Random Forest, consolidando os pontos abordados.

| Característica            | Árvore de Decisão                                                                | Random Forest                                                                                                     |
| :------------------------ | :------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------- |
| **Arquitetura** | Modelo preditivo único e hierárquico, baseado em uma sequência de decisões.      | Método de *ensemble* que combina as previsões de múltiplas Árvores de Decisão treinadas de forma independente.  |
| **Funcionamento Principal** | Divide os dados recursivamente com base em critérios de impureza (Gini, Entropia). | Constrói múltiplas árvores usando *bagging* (amostragem com reposição) e seleção aleatória de *features*; agrega previsões por votação. |
| **Vantagens** | - Alta interpretabilidade e facilidade de visualização.\<br/\>- Rápido para treinar e prever.\<br/\>- Lida bem com dados não lineares e interações. | - Alta acurácia e robustez.\<br/\>- Redução significativa do *overfitting*.\<br/\>- Lida bem com alta dimensionalidade e grande volume de dados.\<br/\>- Fornece importância das *features*. |
| **Desvantagens** | - Alta propensão a *overfitting* (sem poda adequada).\<br/\>- Instabilidade: pequenas mudanças nos dados podem alterar drasticamente a árvore.\<br/\>- Baixa capacidade de generalização em cenários complexos. | - Menos interpretabilidade (considerado um modelo "caixa preta").\<br/\>- Maior tempo de treinamento (especialmente com muitas árvores).\<br/\>- Mais complexo computacionalmente. |
| **Robustez a *Overfitting*** | Baixa (alta variância), necessita de poda e controle de hiperparâmetros rigorosos. | Alta (devido ao *ensemble* e aleatoriedade), inerentemente mais robusto a ruídos e generaliza melhor.             |
| **Acurácia Preditiva** | Geralmente boa para problemas simples; pode ser superada por modelos mais robustos em cenários complexos. | Geralmente muito alta; consistentemente superior à de uma única Árvore de Decisão na maioria dos problemas.      |
| **Interpretabilidade** | Muito Alta: A lógica de decisão pode ser mapeada e visualizada claramente.       | Baixa: Difícil de interpretar o processo de decisão combinado de centenas de árvores.                             |
| **Custo Computacional** | Baixo: Treinamento e previsão são relativamente rápidos.                         | Moderado a Alto: Treina múltiplas árvores em paralelo, mas a predição é mais lenta.                                |
| **Casos de Uso Típicos** | - Necessidade crítica de transparência e regras de decisão claras.\<br/\>- Modelos de base para explicar conceitos de ML.\<br/\>- Problemas com dados simples e baixa dimensionalidade. | - Problemas de classificação e regressão onde a acurácia e a robustez são primordiais.\<br/\>- Dados com alta dimensionalidade e interações complexas.\<br/\>- Cenários que exigem alta capacidade de generalização. |

### 4.1. Forças e Fragilidades dos Modelos e Cenários de Aplicação

A escolha entre Árvore de Decisão e Random Forest é um equilíbrio entre interpretabilidade e desempenho, com cada modelo apresentando suas forças e fragilidades:

**Árvore de Decisão:**

  * **Forças:**

      * **Interpretabilidade Sem Igual:** Sua maior força reside na clareza. Uma Árvore de Decisão é como um fluxograma; cada decisão em um nó é explícita, tornando o modelo altamente compreensível para humanos. Isso é crucial em domínios como medicina (diagnóstico de doenças), finanças (avaliação de crédito com regras claras) ou processos regulatórios, onde não basta prever, mas é imperativo entender *por que* uma previsão foi feita. Imagine um sistema que aprova ou nega um empréstimo: a árvore pode explicar exatamente o caminho de decisão (renda, histórico de crédito, tempo de emprego).
      * **Simplicidade e Rapidez:** Para datasets pequenos e com poucas *features*, as árvores de decisão são rápidas de treinar e de gerar previsões, sendo ideais para prototipagem rápida ou para ambientes com recursos computacionais limitados.
      * **Lida com Não-Linearidades:** Consegue capturar relações não lineares complexas entre *features* e o *target* sem a necessidade de transformações explícitas.

  * **Fragilidades:**

      * **Propensão a Overfitting:** A Árvore de Decisão é excessivamente sensível a pequenos ruídos nos dados. Se não for cuidadosamente controlada (com poda ou restrições de profundidade), ela pode "decorar" os dados de treinamento, resultando em um desempenho péssimo em dados novos. Pense em um modelo de diagnóstico médico que se ajusta perfeitamente a um conjunto de pacientes específico, mas falha miseravelmente em casos ligeiramente diferentes.
      * **Instabilidade:** Uma pequena alteração nos dados de entrada pode levar a uma Árvore de Decisão completamente diferente, o que a torna instável e menos confiável para inferências robustas.
      * **Viés em Dados Desequilibrados:** Se as classes no *target* estiverem desequilibradas, a árvore pode ser enviesada em favor da classe majoritária.

  * **Cenários Onde se Sairia Melhor:**

      * **Sistemas de Apoio à Decisão com Necessidade de Explicação:** Em auditorias, sistemas de recomendação de produtos onde o cliente quer saber "por que" aquele produto foi sugerido, ou em sistemas de triagem que precisam justificar cada passo.
      * **Modelagem de Processos Simples:** Se o processo subjacente aos dados é naturalmente hierárquico e baseado em regras sequenciais, uma Árvore de Decisão pode modelá-lo com precisão e ser facilmente validada por especialistas de domínio.
      * **Análise Exploratória Inicial:** Como uma ferramenta de visualização para entender as interações mais importantes entre *features* antes de aplicar modelos mais complexos.

**Random Forest:**

  * **Forças:**

      * **Alta Acurácia e Robustez:** Sua maior força é a capacidade de combinar o poder de múltiplas árvores para gerar previsões altamente precisas e robustas. Ele efetivamente reduz a variância do modelo, tornando-o menos propenso a *overfitting*. Um sistema de detecção de fraudes, por exemplo, exige alta acurácia para não perder fraudes (falsos negativos) nem gerar muitos alarmes falsos (falsos positivos).
      * **Lida com Alta Dimensionalidade e Interações Complexas:** Eficiente em datasets com muitas *features* e pode capturar interações complexas entre elas sem a necessidade de engenharia de *features* extensiva. Imagine um modelo de previsão de churn de clientes com centenas de variáveis de comportamento.
      * **Menos Sensível a *Outliers*:** Devido à sua natureza de *ensemble* e ao *bagging*, o impacto de *outliers* ou ruídos em *features* específicas é diluído.
      * **Fornece Importância de *Features*:** Embora não seja interpretável como uma árvore única, ele pode indicar quais *features* são mais relevantes para o processo de classificação, o que é útil para seleção de *features* e *insights* gerais.

  * **Fragilidades:**

      * **Baixa Interpretabilidade ("Caixa Preta"):** A principal desvantagem é a dificuldade de entender o *porquê* de uma previsão específica. É como pedir a um conselho de especialistas para tomar uma decisão: eles dão a resposta, mas o processo interno de deliberação de cada um é opaco. Isso pode ser um problema em contextos onde a explicabilidade é legalmente exigida ou eticamente crucial.
      * **Custo Computacional Elevado:** Treinar centenas ou milhares de árvores pode ser computacionalmente intensivo e demorado, especialmente com datasets muito grandes. A previsão também pode ser mais lenta.
      * **Pode não Generalizar Bem para Extrapolação:** Embora robusto para interpolação (prever dentro do range dos dados de treinamento), pode não se comportar tão bem para previsões que exigem extrapolação para fora dos limites dos dados vistos.

  * **Cenários Onde se Sairia Melhor:**

      * **Problemas de Alta Performance Preditiva:** Detecção de fraudes (transações, seguros), reconhecimento de imagem (classificação de objetos), previsão de doenças (onde a acurácia é vital, mesmo que o médico não tenha a explicação exata do "porquê" via modelo).
      * **Grandes Volumes de Dados Complexos:** Em *e-commerce* para recomendar produtos baseados em um histórico de compra vasto e variáveis de comportamento, ou em análise de dados genômicos onde a dimensionalidade é enorme.
      * **Competições de Machine Learning:** Frequentemente um dos modelos de base ou parte de *ensembles* mais complexos devido à sua alta acurácia e versatilidade.

Em resumo, enquanto a Árvore de Decisão brilha na simplicidade e na capacidade de explicar suas decisões, o Random Forest se destaca na acurácia e robustez para a vasta maioria dos problemas de classificação do mundo real, especialmente quando a complexidade dos dados e a necessidade de alta performance preditiva superam a exigência de uma interpretabilidade detalhada de cada passo. A escolha final, portanto, deve sempre considerar o trade-off entre esses dois aspectos fundamentais do Machine Learning.




-----
### Distribuição do modelo (opcional)

Tende criar um pacote de distribuição para o modelo construído, para ser aplicado 
em um sistema inteligente.

<div id='Conclusão'/>  
	 <h3 align="center"><strong> Conclusão  </strong></h3> 

Apresente aqui a conclusão do seu trabalho. Discussão dos resultados obtidos no trabalho, 
onde se verifica as observações pessoais de cada aluno.

Uma conclusão deve ter 3 partes:

   * Breve resumo do que foi desenvolvido
	 * Apresenação geral dos resultados obtidos com discussão das vantagens e desvantagens do sistema inteligente
	 * Limitações e possibilidades de melhoria

---
<div id='REFERÊNCIAS'/>  
   <h3 align="center"><strong> REFERÊNCIAS   </strong></h3> 


*[1]* Kaggle: State of  Data Brazil-2023, o mapeamento mais completo do mercado brasileiro de dados [Data Hackers + Bain]. Disponível em: https://www.kaggle.com/datasets/datahackers/state-of-data-brazil-2023/data. Acesso em: 01 mar. 2025.

*[2]* Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira | Inep: Censo da Educação Superior Microdados do Censo da Educação Superio. Disponível em: (https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/microdados/censo-da-educacao-superior). Acesso em: 13 mar. 2025.


---

<div id='APÊNDICES'/>  
 <h3 align="center"><strong> APÊNDICES  </strong></h3> 

**Colocar link:**

Do código (armazenado no repositório);

Dos artefatos (armazenado do repositório);

Da apresentação final (armazenado no repositório);

Do vídeo de apresentação (armazenado no repositório).




