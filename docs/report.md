# Desafios Para Profissionais Juniores e Microempresas no Uso de Dados e Tecnologia, IA Generativa e LLM’S.

---

**Caio César de Oliveira, caio.oliveira.1551586@sga.pucminas.br**

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

[11. Resultados ](#Resultados)  

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


## Base principal: [**State of Data Brazil 2023**](/assets/data/state-of-data-brazil-2023)
A base "State of Data Brazil 2023" coleta informações demográficas e sobre a carreira de profissionais de dados no Brasil, como idade, gênero, cor/raça/etnia, experiência profissional e aspectos da carreira, como oportunidades de emprego e progressão na carreira. Esses dados ajudam a analisar as dificuldades de inclusão e as barreiras enfrentadas por profissionais juniores, permitindo um foco nos desafios de inserção no mercado de IA Generativa, como a falta de acesso a oportunidades e a desigualdade em processos seletivos.


 [**Dicionário de dados - State of Data Brazil 2023**](/assets/data/state-of-data-brazil-2023/dicionario_state.md)

 [**Descrição de dados - State of Data Brazil 2023**](/imagens/graficos/graficos_state_of_data.md)

--- 

## Base auxiliar:  [**Microdrados Educação Superior**](/assets/data/microdados_ed_sup_ies_2023)
 A base "MICRODADOS_ED_SUP_IES 2023" reúne dados sobre instituições de ensino superior no Brasil, como localização geográfica, tipo de instituição e rede de ensino (pública ou privada). Ela é crucial para entender a distribuição e a oferta de cursos de educação superior, especialmente em áreas relacionadas à IA Generativa.

 [**Dicionário de dados - MICRODADOS_ED_SUP_IES**](/assets/data/microdados_ed_sup_ies_2023/dicionario_micro.md)

 [**Descrição de dados - MICRODADOS_ED_SUP_IES_2023**](/imagens/graficos/graficos_microdados.md)

---

<div id='Preparação_dos_dados'/>  
 <h3 align="center"><strong> Preparação dos dados  </strong></h3> 
	
[Base Tratada](/assets/data/dados_tratados_combinados/dados_tratados_combinados.csv)
[Codigo](/src/limpeza_e_combinacao.ipynb)


## 1. Introdução

Este documento detalha o processo de limpeza, transformação, seleção e combinação de dados realizado pelo script `LimpezaCombinacao.ipynb`. O objetivo deste pipeline de preparação é consolidar duas fontes de dados distintas em um único conjunto de dados coeso e enriquecido, pronto para análises exploratórias e para o treinamento de modelos preditivos.

As fontes de dados são:
1.  **Pesquisa "State of Data 2023"**: Um arquivo CSV contendo respostas de uma pesquisa com profissionais da área de dados no Brasil.
2.  **Microdados do Censo da Educação Superior (IES)**: Um arquivo CSV com dados sobre Instituições de Ensino Superior no Brasil.

O processo é dividido em quatro partes principais:
1.  Configuração e Processamento dos dados da pesquisa.
2.  Processamento e Agregação dos dados das IES.
3.  União dos dois conjuntos de dados.
4.  Salvamento do resultado final.

## 2. Configuração Inicial e Bibliotecas

A primeira célula do notebook é responsável por importar as bibliotecas essenciais para a manipulação e processamento dos dados.

```python
import pandas as pd
import re
import numpy as np
```

- **`pandas`**: Biblioteca fundamental para a manipulação e análise de dados em Python. É utilizada para carregar os dados dos arquivos CSV para DataFrames, que são estruturas de dados tabulares otimizadas, e para realizar a maioria das operações de limpeza, transformação e agregação.
- **`re`**: Módulo de expressões regulares do Python. Neste script, é crucial para a limpeza e padronização dos nomes das colunas, que originalmente possuem um formato complexo.
- **`numpy`**: Biblioteca para computação numérica. É utilizada aqui para a criação da feature `emprego_status` através da função `np.where`.

## 3. Parte 1 - Processamento do Dataset "State of Data"

Esta seção foca em limpar e estruturar os dados da pesquisa.

### 3.1. Carregamento e Seleção de Colunas

O processo inicia com o carregamento dos dados da pesquisa e a seleção de colunas relevantes.

```python
df_survey = pd.read_csv('State_of_data_BR_2023_Kaggle - df_survey_2023.csv')
```

- **Seleção de Colunas**: O código define uma lista de colunas (`fixed_columns`) que contêm informações demográficas e profissionais chave, como idade, gênero, cargo, faixa salarial e o estado de residência (`uf onde mora`), que é fundamental para a posterior união dos dados.
- **Seleção Dinâmica**: Utilizando compreensão de listas, o código seleciona dinamicamente grupos de colunas que seguem um padrão de prefixo. Isso é feito para capturar todas as respostas de perguntas de múltipla escolha, como:
    - `P2_l_` e `P2_o_`: Motivos de satisfação/insatisfação no trabalho.
    - `P4_j_`, `P4_k_`, `P4_l_`: Ferramentas de IA/ML, serviços de nuvem e tecnologias de IA Generativa utilizadas.
    - `P3_d_`, `P3_e_`: Habilidades técnicas e comportamentais.
- **Criação do DataFrame Selecionado**: As listas de colunas são combinadas e utilizadas para criar um novo DataFrame, `df_selected`, contendo apenas os dados de interesse. O método `.copy()` é usado para garantir que o DataFrame original (`df_survey`) não seja modificado.

### 3.2. Limpeza da Variável Alvo e Tratamento de Nulos

Esta etapa garante a qualidade da variável alvo (satisfação) e trata valores ausentes.

- **Variável Alvo**: A coluna de satisfação profissional (`'P2_k '`) é identificada. As linhas onde este valor é nulo ou "Desconhecido" são removidas com o método `.dropna()` para garantir que todas as entradas no dataset final tenham uma resposta válida para a variável que se deseja prever.
- **Tratamento de Nulos**: O script itera sobre as colunas do DataFrame `df_cleaned_survey`:
    - Para as colunas dinâmicas (ferramentas, habilidades, etc.), valores nulos (`NaN`) são preenchidos com `0`. Isso assume que um valor ausente significa que o respondente não usa a ferramenta ou não possui a habilidade.
    - Para as colunas fixas (demográficas), valores nulos são preenchidos com a string `'Desconhecido'`, tratando a ausência de informação como uma categoria distinta.

### 3.3. Renomeação Inteligente de Colunas

Os nomes das colunas no dataset original são complexos e inadequados para análise (ex: `("('P1_a ', 'Idade')"`). Uma função customizada, `get_clean_column_name`, foi criada para resolver isso.

- **Lógica da Função**: A função utiliza expressões regulares (`re.search`) para extrair a parte descritiva do nome da coluna (ex: 'Idade'). Em seguida, padroniza este nome, convertendo-o para minúsculas e substituindo espaços e caracteres especiais por underscores (`_`).
    - **Exemplo**: `("('P4_j_1 ', 'Azure Machine Learning')")` se torna `azure_machine_learning`.
- **Aplicação**: Esta função é aplicada a todas as colunas do DataFrame, criando um mapa de renomeação que é utilizado pelo método `.rename()` para padronizar todos os nomes de uma só vez, resultando em um DataFrame com colunas limpas e fáceis de manipular.

### 3.4. Criação de Novas Features (Engenharia de Atributos)

Para facilitar análises futuras, uma nova coluna é criada.

- **`emprego_status`**: Utilizando a função `np.where`, o código cria a coluna `emprego_status`. Se o valor na coluna `cargo_atual` for '14' (código para "Outra situação"), o status é definido como 'Desempregado'; caso contrário, é 'Empregado'. Esta é uma forma simples e eficaz de engenharia de features.

## 4. Parte 2 - Processamento e Agregação dos Dados das IES

Esta parte do script prepara os dados contextuais sobre o ambiente educacional em cada estado.

### 4.1. Carregamento e Seleção

O dataset `MICRODADOS_ED_SUP_IES_2023.CSV` é carregado. O código especifica o delimitador como `;` e a codificação como `latin1`, comum em arquivos de dados governamentais brasileiros. Apenas as colunas de interesse são selecionadas e renomeadas para maior clareza:
- `SG_UF_IES` → `uf_ies` (UF da instituição)
- `QT_TEC_TOTAL` → `Qtd_Tecnicos_IES` (Quantidade de técnicos)
- `QT_DOC_TOTAL` → `Qtd_Docentes_IES` (Quantidade de docentes)

### 4.2. Agregação por Estado (UF)

O objetivo aqui é transformar os dados do nível de instituição para o nível de estado.
- **`groupby('uf_ies').agg({...})`**: Este é o comando central da agregação. Ele agrupa o DataFrame por estado e aplica as seguintes funções de agregação:
    - **`sum`**: Para as colunas `Qtd_Tecnicos_IES` e `Qtd_Docentes_IES`, calculando o total de profissionais por estado.
    - **`count`**: Para a coluna `uf_ies`, contando o número de instituições em cada estado.
- **Renomeação Final**: As colunas agregadas são renomeadas para refletir seu novo significado (ex: `Qtd_Tecnicos_IES` torna-se `Total_Tecnicos_Estado`).

## 5. Parte 3 - União dos Datasets (Merge)

Nesta etapa crucial, os dois DataFrames preparados são combinados.

```python
df_final = pd.merge(df_cleaned_survey, df_ies_aggregated, ...)
```

- **`pd.merge()`**: Esta função une os dois conjuntos de dados.
- **Chaves de Junção**: A união é feita conectando a coluna `uf_onde_mora` (do dataset da pesquisa) com a coluna `uf_ies` (do dataset agregado das IES).
- **Tipo de Junção**: É utilizada uma **mesclagem à esquerda** (`how='left'`). Essa escolha é importante, pois garante que **todos os registros da pesquisa (DataFrame da esquerda) sejam mantidos**. Se um respondente for de um estado para o qual não há dados de IES, as colunas correspondentes no DataFrame final serão preenchidas com valores nulos, preservando a integridade da amostra da pesquisa.

## 6. Parte 4 - Salvamento e Verificação Final

A última parte do script salva o resultado e realiza uma verificação.

- **`df_final.to_csv(...)`**: O DataFrame final e combinado é salvo no arquivo `dados_tratados_combinados.csv`.
    - `index=False`: Impede que o índice do DataFrame seja salvo como uma coluna no arquivo CSV.
    - `encoding='utf-8-sig'`: Garante a compatibilidade de caracteres, especialmente com softwares como o Microsoft Excel.
- **Verificação**: O código imprime as primeiras linhas de algumas colunas chave do DataFrame final como uma verificação visual rápida para confirmar que a união foi bem-sucedida e os dados estão estruturados como esperado.

## Conclusão

Ao final do processo, o script gera um único arquivo CSV, `dados_tratados_combinados.csv`, que serve como uma **Base Analítica de Tabela (Analytical Base Table - ABT)**. Este dataset está limpo, estruturado, enriquecido com dados contextuais e pronto para ser utilizado em análises exploratórias e na construção de modelos de Machine Learning.	


---

<div id='Indução_de_modelos'/>  
	
 <h3 align="center"><strong> Indução de modelos  </strong></h3> 


A pergunta escolhida para a indução de modelos de aprendizado de máquina foi: **Quais são os principais fatores que explicam a satisfação (ou insatisfação) dos profissionais da área de dados no Brasil?** Para responder a essa questão, foram desenvolvidos e comparados dois modelos:

--- 
<div id='Indução_de_modelos_1'/> 
### **Modelo 1: Análise do LightGBM com SMOTE**

Esta abordagem utiliza o framework LightGBM em conjunto com a técnica de reamostragem SMOTE para lidar com o desbalanceamento de classes.

#### **3.1. Detalhamento do Código e Metodologia**

1.  **Pré-processamento com `ColumnTransformer`**: As variáveis preditoras são processadas para que possam ser utilizadas pelo modelo. Features categóricas (como nível e setor) são transformadas via `OneHotEncoder`, enquanto as numéricas (como anos de experiência) são padronizadas via `StandardScaler`.

2.  **Pipeline com `SMOTE`**: Para tratar o desbalanceamento de classes (72% satisfeitos vs. 28% insatisfeitos), o pipeline foi construído com o `ImbPipeline` da biblioteca `imbalanced-learn`.
    * **Técnica `SMOTE` (Synthetic Minority Over-sampling Technique)**: Este passo é crucial. O SMOTE gera novas amostras sintéticas da classe minoritária ("Insatisfeito") com base nas características de suas vizinhas mais próximas. O objetivo é criar um conjunto de dados de treino artificialmente balanceado, permitindo que o modelo aprenda os padrões de ambas as classes de forma mais equitativa.

3.  **Otimização com `RandomizedSearchCV`**: Um processo de busca por hiperparâmetros foi executado para encontrar a melhor configuração para o `LGBMClassifier`. Foram testadas 30 combinações aleatórias de parâmetros, utilizando validação cruzada de 5 folds e otimizando para a métrica `f1_macro`, que é ideal para cenários com classes desbalanceadas.

#### **3.2. Análise dos Resultados**

O modelo final apresentou um alto poder preditivo, conforme demonstram as métricas abaixo.

##### **Desempenho no Conjunto de Treino:**
* **Acurácia**: 97%
* **AUC-ROC**: 0.982
* **Classe 'Insatisfeito' (minoritária)**:
    * Precisão: 1.00
    * Recall: 0.90
* **Classe 'Satisfeito' (majoritária)**:
    * Precisão: 0.96
    * Recall: 1.00

##### **Desempenho no Conjunto de Teste (Validação):**
* **Acurácia**: 96%
* **AUC-ROC**: 0.955
* **Classe 'Insatisfeito' (minoritária)**:
    * **Precisão: 1.00**: Quando o modelo prevê que um profissional está insatisfeito, ele está sempre correto.
    * **Recall: 0.87**: O modelo consegue identificar 87% de todos os profissionais que realmente estão insatisfeitos.
* **Classe 'Satisfeito' (majoritária)**:
    * **Precisão: 0.95**: Das previsões de "satisfeito", 95% estão corretas.
    * **Recall: 1.00**: O modelo identifica 100% dos profissionais que de fato estão satisfeitos.

A pequena diferença entre as métricas de treino e teste indica que o modelo **generaliza bem** para dados não vistos, sem sinais de sobreajuste (overfitting) severo. O gráfico de **Importância das Features** destacou que a falta de oportunidade de crescimento e o desalinhamento salarial são os fatores mais determinantes para a previsão.

---
<div id='Indução_de_modelos_2'/> 
### **Modelo 2: Análise do XGBoost com Ponderação de Classes**

Esta segunda abordagem emprega o robusto framework XGBoost, utilizando um método interno para o tratamento do desbalanceamento.

#### **4.1. Detalhamento do Código e Metodologia**

1.  **Pré-processamento**: A etapa de `ColumnTransformer` é idêntica à do modelo anterior, garantindo a mesma preparação das features.

2.  **Pipeline com Ponderação de Classe**: A diferença fundamental está no pipeline e no algoritmo. Utiliza-se o `Pipeline` padrão do `scikit-learn`.
    * **Técnica `scale_pos_weight`**: Em vez de gerar dados sintéticos, o `XGBClassifier` foi configurado com o parâmetro `scale_pos_weight`. Este parâmetro ajusta a importância das classes durante o treinamento, atribuindo um peso maior aos erros cometidos na classe minoritária. O valor de **0.39** foi calculado (`contagem_negativos / contagem_positivos`), instruindo o modelo a penalizar mais fortemente os erros na classificação de profissionais "insatisfeitos".

3.  **Otimização com `RandomizedSearchCV`**: O processo de otimização foi mais extenso, testando 50 combinações de hiperparâmetros específicos do XGBoost, como `gamma`, `subsample` e `colsample_bytree`, também com o objetivo de maximizar o `f1_macro`.

<div id='Resultados'/> 

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
 
#### **4.2. Análise dos Resultados**

O modelo XGBoost demonstrou um desempenho de excelência, muito similar ao do LightGBM.

##### **Desempenho no Conjunto de Treino:**
* **Acurácia**: 97%
* **AUC-ROC**: 0.988
* **Classe 'Insatisfeito' (minoritária)**:
    * Precisão: 1.00
    * Recall: 0.91
* **Classe 'Satisfeito' (majoritária)**:
    * Precisão: 0.97
    * Recall: 1.00

##### **Desempenho no Conjunto de Teste (Validação):**
* **Acurácia**: 96%
* **AUC-ROC**: 0.961
* **Classe 'Insatisfeito' (minoritária)**:
    * **Precisão: 1.00**: Performance perfeita na precisão para a classe de maior interesse.
    * **Recall: 0.87**: Capacidade de identificação dos insatisfeitos idêntica à do LightGBM.
* **Classe 'Satisfeito' (majoritária)**:
    * **Precisão: 0.95** e **Recall: 1.00**, novamente em linha com o modelo anterior.

O modelo XGBoost também apresentou ótima capacidade de generalização. De forma crucial, a análise de **Importância das Features** confirmou os mesmos fatores como sendo os mais relevantes, o que confere grande robustez às conclusões extraídas.

---

<div id='Comparacoes'/> 

### **5. Análise Comparativa e Conclusão Técnica**

Ao comparar os dois modelos, observamos uma paridade notável em termos de performance de classificação, mas diferenças importantes na metodologia.

| Característica | Modelo LightGBM | Modelo XGBoost |
| :--- | :--- | :--- |
| **Acurácia (Teste)** | 96% | 96% |
| **AUC-ROC (Teste)** | 0.955 | **0.961** |
| **Recall 'Insatisfeito' (Teste)** | 0.87 | 0.87 |
| **Precisão 'Insatisfeito' (Teste)**| 1.00 | 1.00 |
| **Técnica de Balanceamento** | SMOTE (Criação de dados sintéticos) | `scale_pos_weight` (Ponderação de erros) |
| **Complexidade do Pipeline**| Maior (requer `ImbPipeline`) | Menor (usa `Pipeline` padrão) |

#### **Discussão e Recomendação**

Ambos os modelos se mostraram extremamente eficazes. As métricas de classificação no conjunto de teste são praticamente idênticas. O XGBoost apresenta uma ligeira vantagem no AUC-ROC, sugerindo uma capacidade marginalmente superior de discriminar corretamente entre as duas classes.

A principal distinção reside na abordagem ao desbalanceamento de dados.
* O **LightGBM com SMOTE** é uma abordagem poderosa, mas que envolve a criação de dados sintéticos, o que pode introduzir ruído e aumentar a complexidade do pipeline.
* O **XGBoost com `scale_pos_weight`** representa uma solução mais elegante e computacionalmente mais eficiente. Ele lida com o desbalanceamento de forma intrínseca, ajustando a função de perda sem alterar o dataset original, o que é metodologicamente mais direto.

**Conclusão Final:**

Considerando a performance praticamente idêntica e a superioridade metodológica na abordagem do desbalanceamento, **o modelo XGBoost é a solução tecnicamente preferível para este problema**. Sua implementação é mais limpa e o risco de introduzir artefatos nos dados é nulo.

Ainda assim, o fato de ambos os modelos, com suas diferentes abordagens, terem apontado para os mesmos fatores preditores (oportunidade de crescimento e salário) é a validação mais forte do estudo, fornecendo insights de negócio confiáveis e acionáveis.



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




