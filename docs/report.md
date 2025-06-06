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

**Resumo:**

Este trabalho analisa os desafios enfrentados por profissionais juniores e microempresas brasileiras na adoção da Inteligência Artificial Generativa (IA Generativa) e Large Language Models (LLMs).Com base em dados do "State of Data Brazil 2023" e microdados da educação superior, o estudo investiga fatores que influenciam a satisfação profissional e a competitividade das microempresas no contexto da IA. 

Para isso, foram induzidos e comparados modelos de machine learning, como a Árvore de Decisão e o Random Forest, para identificar os principais fatores que explicam a satisfação dos profissionais da área de dados. O processo envolveu rigoroso pré-processamento dos dados, treinamento, validação e otimização dos modelos, além da comparação entre diferentes abordagens para garantir resultados confiáveis e interpretáveis. 
Os resultados indicam que fatores como satisfação com a remuneração, tempo de experiência e satisfação com o ambiente de trabalho são determinantes para a satisfação no mercado de IA Generativa, especialmente para perfis juniores e pequenos negócios.


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

[10. Indução de modelos](#Indução_de_modelos)
* [10.1 Indução de Modelo 1](#Indução_de_modelo_1)
* [10.2 Indução de  Modelo 2](#Indução_de_modelo_2))

[11. Resultados ](#Resultados)
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
	
Para o desenvolvimento deste trabalho, diversas perguntas foram levantadas para guiar a análise e a modelagem. A pergunta principal que o presente trabalho busca responder através da indução de modelos de machine learning é:

* Quais são os principais fatores que explicam a satisfação (ou insatisfação) dos profissionais da área de dados no Brasil?
* 
Adicionalmente, outras questões relevantes que foram exploradas na análise exploratória dos dados e que servem de base para insights futuros incluem:

* Quais fatores (salário, experiência, ferramentas utilizadas) influenciam a inserção profissional no mercado de IA?
* As microempresas têm acesso às mesmas tecnologias e recursos que as grandes empresas?
* Como a adoção da IA Generativa impacta a competitividade das microempresas?
* Quais habilidades e conhecimentos são mais valorizados no mercado para quem deseja atuar com IA Generativa?


<div id='Objetivos'/>  
   <h3 align="center"><strong> Objetivo geral  </strong></h3> 

 Desenvolver um sistema inteligente que analise dados do mercado de trabalho e de microempresas para identificar os principais desafios enfrentados por profissionais juniores e pequenos negócios na adoção da IA ​​Generativa, propondo soluções baseadas em insights obtidos

---

   <h3 align="center"><strong> Objetivos específicos   </strong></h3> 

* Avaliar o impacto da adoção da IA Generativa na competitividade de microempresas.

* Investigar os fatores que influenciam a valorização profissional na área, como experiência, habilidades e acesso a ferramentas, com foco na classificação da satisfação dos profissionais.

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
  
Estudantes e recém-formados em Ciência de Dados, Inteligência Artificial, Análise e Desenvolvimento de Sistemas, entre outros.

Possuem conhecimentos básicos ou intermediários sobre IA, mas enfrentam barreiras como exigência de experiência prévia e acesso.

Buscar informações sobre habilidades valorizadas no mercado, oportunidades de capacitação e formas de entrada no setor de IA Generativa.

* Microempresas e Pequenos Negócios:
  
Pequenos empreendedores e startups que desejam incorporar IA Generativa. 

Geralmente possuem conhecimento limitado sobre as tecnologias de IA e seu aplicativo.

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


A pergunta escolhida para a indução de modelos de aprendizado de máquina foi: **Quais são os principais fatores que explicam a satisfação (ou insatisfação) dos profissionais da área de dados no Brasil?** Para responder a essa questão, foram desenvolvidos e comparados dois modelos de classificação: Árvore de Decisão e Random Forest.

<div id='Indução_de_modelos_1'/>  
	
###  Indução de Modelo 1 - Árvore de Decisão

O modelo de Árvore de Decisão foi desenvolvido para lidar com problemas de classificação, conforme implementado no notebook "Pergunta1ArvoreDeDecisao.ipynb". O processo de indução (treinamento) do modelo seguiu as seguintes etapas rigorosas:

- **Importação de Bibliotecas**: Importação de *Pandas*, *NumPy*, *Matplotlib*, *Seaborn*, *NLTK*, *WordCloud* e *Scikit-learn*, incluindo ferramentas para balanceamento de dados (*SMOTE*), trazendo atenção a possíveis desequilíbrios de classe no dataset.
- **Carregamento e Pré-processamento de Dados**:
  - Carregamento do conjunto de dados "State_of_data_BR_2023_Kaggle - df_survey_2023.csv".
  - Execução de pré-processamento crítico, incluindo tratamento de valores ausentes e codificação de variações categóricas (*One-Hot Encoding*), para garantir a integridade e interpretabilidade numérica dos dados.
- **Definição de Variáveis**: Definição clara das variáveis independentes (*features*, representadas por *X*) e da variável dependente (*target*, representada por *y*), que é a variável a ser prevista pelo modelo (satisfação do profissional).
- **Divisão de Dados**: Particionamento do conjunto de dados em conjuntos de treinamento e teste para avaliar a capacidade de generalização do modelo e mitigar o risco de *overfitting*.
- **Treinamento do Modelo**: Uma instância do classificador *DecisionTreeClassifier* foi criada e treinada utilizando os dados de treinamento.
- **Validação do Modelo**: O desempenho do modelo treinado foi avaliado no conjunto de teste utilizando métricas de classificação padrão, como pontuação de exatidão, precisão, *recall*, pontuação *F1* e a matriz de confusão.
- **Otimização de Hiperparâmetros**: Uso de *GridSearchCV* para explorar sistematicamente diferentes configurações de hiperparâmetros (por exemplo, *max_depth*, *min_samples_split*, *criterion*) e selecionar aqueles que resultaram no melhor desempenho, calculado por validação cruzada.
- **Visualização da Árvore**: O caderno permite a visualização gráfica da árvore de decisão treinada, fundamental para compreender as regras lógicas matemáticas pelo modelo.

#### Tipo de Problema e Modelo Escolhido:

O problema é de classificação, mudando prever uma variável categórica que representa a satisfação dos profissionais. O modelo escolhido para esta abordagem inicial foi a Árvore de Decisão.

#### Funcionamento do Algoritmo: [Árvore de Decisão](/src/Modelos_Corrigidos/ArvoreDeDecisao.ipynb)
A Árvore de Decisão é um algoritmo de aprendizagem supervisionado não-paramétrico. Para classificação, seu funcionamento se baseia em um processo de divisão recursiva dos dados:

- **Nó Raiz e Divisão Recursiva**: O processo se inicia com um nó único (a raiz) que engloba a totalidade dos dados. Em cada nó, o algoritmo busca os melhores classificações (ou "pergunta") para particionar os dados em subconjuntos mais homogêneos em relação à variável alvo.
- **Critérios de Impureza**: As divisões são determinadas pela otimização de métricas de impureza, como a Entropia ou o Índice Gini. O algoritmo seleciona a divisão que maximiza o ganho de informação ou minimiza a impureza.
- **Nós Internos e Folhas**: O processo de divisão prossegue recursivamente, formando nós internos que representam testes em atributos específicos e ramos que denotam os resultados. Quando um nó não pode ser mais dividido de forma significativa, ele se torna uma "folha", representando a classe prevista.
- **Poda (*Poda*)**: Técnicas de poda foram aplicadas para combater o *overfitting*, removendo ramos que não valorizaram significativamente para o desempenho de generalização.

#### Objetivo do Modelo (Árvore de Decisão):

O objetivo primordial é desenvolver um sistema preditivo capaz de classificar novas instâncias com base nos padrões e regras de decisão inferidas a partir dos dados de treinamento. Sua característica de "caixa branca" permite a interpretação das regras de decisão, valiosa para a compreensão do domínio do problema.


<div id='Indução_de_modelos_2'/> 
	
###  Indução de Modelo 2 - Random Forest



O modelo Random Forest, implementado no notebook "Pergunta1RandonFlorest.ipynb", também é projetado para problemas de classificação. A indução deste modelo, um método de conjunto, incorporou as seguintes fases:

- **Importação de Bibliotecas**: Importação de *Pandas*, *NumPy*, *Matplotlib*, *Seaborn*, *WordCloud* e *Scikit-learn*, com destaque para o *RandomForestClassifier*.
- **Carregamento e Pré-processamento de Dados**: Utilização do mesmo conjunto de dados ("State_of_data_BR_2023_Kaggle - df_survey_2023.csv") para garantir consistência. O pré-processamento incluiu limpeza e seleção de variações categóricas.
- **Definição de Variáveis**: As características (*X*) e a variável alvo (*y*) foram definidas de forma análoga ao modelo de Árvore de Decisão.
- **Divisão de Dados**: O conjunto de dados foi segmentado em conjuntos de treinamento e teste para permitir uma avaliação imparcial da generalização do modelo.
- **Treinamento do Modelo**: Uma instância do *RandomForestClassifier* foi criada e treinada com os dados de treinamento, envolvendo o treinamento de múltiplas árvores de decisão.
- **Validação Cruzada Estratificada**: Utilização de *StratifiedKFold* e *cross_val_score* para garantir que as proporções das classes na variável *target* sejam preservadas em cada dobra, fornecendo uma estimativa mais confiável do desempenho.
- **Otimização de Hiperparâmetros**: Ajuste de hiperparâmetros como *n_estimators*, *max_depth*, *min_samples_split* e *criterion* via *GridSearchCV* para maximizar o desempenho.
- **Curva de Aprendizagem**: Inclusão de uma curva de aprendizagem para ilustrar como o desempenho do modelo varia com o aumento do volume de dados de treinamento, auxiliando na identificação de problemas de *bias* ou variância.

#### Tipo de Problema e Modelo Escolhido:

O problema é de classificação, mudando a predição de uma variável categórica. O modelo escolhido foi o Random Forest.

#### Funcionamento do Algoritmo: [Random Forest](/src/Modelos_Corrigidos/RandonFlorest.ipynb)

Random Forest é um algoritmo de conjunto que aprimora a robustez e a acurácia das variações ao combinar a força de múltiplas Árvores de Decisão. Ele opera com base em dois princípios fundamentais:

- **Ensacamento (*Bootstrap Aggregation*)**:
  - Amostragem com Reposição: Cada árvore na "floresta" é treinada em um subconjunto aleatório dos dados de treinamento com configuração.
  - Diversidade das Árvores: O ensacamento garante que cada árvore seja treinada em um conjunto de dados intermediários distintos, promovendo a diversidade.
  - Seleção Aleatória de Características: Em cada nó de cada árvore, apenas um subconjunto aleatório das características é considerado, aumentando a diversidade das árvores.
- **Votação Majoritária (para Classificação)**: As variações de todas as árvores são agregadas por votação majoritária para determinar a classe final.

A combinação desses mecanismos permite que o Random Forest supere a propensão ao *overfitting* e à alta variância das Árvores de Decisão individuais, resultando em um modelo mais estável e com maior poder preditivo.

#### Objetivo do Modelo (Random Forest):

O objetivo é classificar novas instâncias com alta precisão e capacidade de generalização, mitigando o *overfitting* e fornecendo mais confiável em dados não vistos, graças à sua arquitetura de conjunto.


---

 <div id='Resultados'/>

<h3 align="center"><strong> Resultados </strong></h3> 

Esta seção apresenta os resultados quantitativos obtidos pelos modelos de Árvore de Decisão e Random Forest na tarefa de classificar a satisfação dos profissionais da área de dados, bem como a otimização de hiperparâmetros e a importância das características.

<div id='Resultado_1'/>
	
### [Resultado Modelo 1 - Árvore de Decisão](/docs/imagens/graficos/graficos_modelos.md)

#### Resultados Obtidos

Após o treinamento e otimização, o modelo de Árvore de Decisão foi avaliado no conjunto de teste com 1.324 amostras. Os hiperparâmetros utilizados foram: *max_depth=5*, *min_samples_leaf=10*, e *class_weight='balanced'*, com *SMOTE* aplicado para balanceamento de classes.

- **Distribuição da Satisfação**: 1.873 insatisfeitos (0) e 3.420 satisfeitos (1), totalizando 5.293 amostras.
- **Acurácia no Teste**: 72%.
- **Relatório de Classificação**:
  | Classe           | Precisão | Recall | F1-Score | Suporte |
  |------------------|----------|--------|----------|---------|
  | 0 (Insatisfeito) | 0.65     | 0.49   | 0.55     | 469     |
  | 1 (Satisfeito)   | 0.75     | 0.85   | 0.80     | 855     |
  | **Acurácia**     |          |        | 0.72     | 1.324   |
  | **Macro Avg**    | 0.70     | 0.67   | 0.68     | 1.324   |
  | **Weighted Avg** | 0.71     | 0.72   | 0.71     | 1.324   |
- **Matriz de Confusão**:
  | Real \ Predito | 0   | 1   |
  |----------------|-----|-----|
  | 0              | 228 | 241 |
  | 1              | 125 | 730 |
- **Curva ROC**: AUC = 0.73.
- **Importância das Features**: As 15 principais features incluem "Forma de Trabalho Atual", "Novos Talentos", "Tableau", entre outras, com valores variando de ~0.05 a ~0.25.
- **Curva de Aprendizado**: Acurácia de treino estabiliza em ~0.74-0.76, e validação em ~0.70-0.72, indicando bom ajuste com aumento do tamanho do conjunto de treino.
- **Nuvem de Palavras**: Motivos de insatisfação destacam "falta", "salário", "atual", e "oportunidade".

#### Discussão dos Resultados

O modelo alcançou uma acurácia de 72%, com bom desempenho na classe majoritária (Satisfeito, recall 0.85). A classe minoritária (Insatisfeito, recall 0.49) apresenta desempenho moderado, melhorado pelo uso de *SMOTE*. A AUC de 0.73 indica capacidade razoável de discriminação. A árvore de decisão reflete a importância de fatores como a forma de trabalho e oportunidades de novos talentos.


<div id='Resultado_2'/>
	
### [Resultados Modelo 2 - Floresta Aleatória](/docs/imagens/graficos/graficos_modelos.md)

#### Resultados Obtidos

O modelo Random Forest foi treinado com hiperparâmetros padrão (*n_estimators=100*, *random_state=42*), utilizando *SMOTE* para balanceamento de classes, e avaliado no conjunto de teste com 1.324 amostras.

- **Distribuição da Satisfação**: 1.873 insatisfeitos (0) e 3.420 satisfeitos (1), totalizando 5.293 amostras.
- **Acurácia no Teste**: 77%.
- **Relatório de Classificação**:
  | Classe           | Precisão | Recall | F1-Score | Suporte |
  |------------------|----------|--------|----------|---------|
  | 0 (Insatisfeito) | 0.74     | 0.55   | 0.63     | 469     |
  | 1 (Satisfeito)   | 0.78     | 0.89   | 0.83     | 855     |
  | **Acurácia**     |          |        | 0.77     | 1.324   |
  | **Macro Avg**    | 0.76     | 0.72   | 0.73     | 1.324   |
  | **Weighted Avg** | 0.77     | 0.77   | 0.76     | 1.324   |
- **Matriz de Confusão**:
  | Real \ Predito | 0   | 1   |
  |----------------|-----|-----|
  | 0              | 256 | 213 |
  | 1              | 91  | 764 |
- **Curva ROC**: AUC = 0.79.
- **Importância das Features**: As 15 principais features incluem "Faixa Salarial", "Tempo na Área de Dados", "Forma de Trabalho Atual", entre outras, com valores variando de ~0.03 a ~0.15.
- **Curva de Aprendizado**: Acurácia de treino estabiliza em ~0.90-0.92, e validação em ~0.76-0.78, indicando bom ajuste, mas com leve sobreajuste em relação ao conjunto de treino.
- **Nuvem de Palavras**: Motivos de insatisfação destacam "falta", "salário", "atual", e "oportunidade".

#### Discussão dos Resultados

O modelo alcançou uma acurácia de 77%, superando a Árvore de Decisão (72%). Apresenta bom desempenho na classe majoritária (Satisfeito, recall 0.89) e melhora na classe minoritária (Insatisfeito, recall 0.55) em relação ao modelo anterior (recall 0.49). A AUC de 0.79 indica melhor capacidade de discriminação. A importância das features destaca fatores como faixa salarial e tempo de experiência, corroborando sua relevância no contexto de satisfação no trabalho.

---

<div id='Comparacoes'/>

<h3 align="center"><strong> Comparações </strong></h3> 

 

O modelo Random Forest (acurácia 77%, AUC 0.79) superou a Árvore de Decisão (acurácia 72%, AUC 0.73) em todas as métricas principais. O Random Forest apresentou melhor desempenho na classe minoritária (Insatisfeito), com recall de 0.55 contra 0.49 da Árvore de Decisão, e na classe majoritária (Satisfeito), com recall de 0.89 contra 0.85. A curva de aprendizado do Random Forest indica leve sobreajuste (acurácia de treino ~0.92 vs. validação ~0.77), enquanto a Árvore de Decisão é mais estável, mas com desempenho inferior (validação ~0.71).

Ambos os modelos identificaram fatores como faixa salarial e forma de trabalho como importantes, mas o Random Forest distribuiu melhor a importância entre as features, capturando relações mais complexas. Para aplicações práticas, o Random Forest é preferível devido à maior acurácia e capacidade de discriminação, embora demande mais recursos computacionais.

## Conclusão

Este trabalho explorou os desafios enfrentados por profissionais juniores e microempresas na adoção de IA Generativa e LLMs, com foco na identificação dos fatores que influenciam a satisfação profissional. Os modelos de aprendizado de máquina desenvolvidos, especialmente o Random Forest, obtiveram alta capacidade preditiva (acurácia de 77%), destacando a faixa salarial, tempo de experiência e forma de trabalho como fatores-chave.

### Resumo do Desenvolvimento:

Foram utilizados dados do *State of Data Brazil 2023* e *Microdados Educação Superior 2023* para analisar barreiras e propor soluções. Após pré-processamento rigoroso e unificação das bases, os modelos de Árvore de Decisão e Random Forest foram treinados e otimizados para classificar a satisfação profissional, com o Random Forest superando em desempenho.

### Vantagens e Desvantagens do Sistema Inteligente:

O sistema oferece recomendações personalizadas para capacitação e identificação de lacunas de mercado, mas sua natureza de "caixa preta" (Random Forest) dificulta a interpretação detalhada das decisões.

### Limitações e Possibilidades de Melhoria:

- **Limitações**: Dados autodeclarados podem introduzir vieses, e o desbalanceamento de classes impactar a predição de categorias minoritárias.
- **Melhorias**: Integrar novas fontes de dados, aplicar técnicas avançadas de balanceamento (*SMOTE-NC*, *ADASYN*), testar modelos como *XGBoost*, realizar análise de sentimento em dados textuais, desenvolver um protótipo funcional e validar insights com entrevistas qualitativas.




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




