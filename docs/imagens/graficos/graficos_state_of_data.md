
# Analise Exploratoria da State of Data Brazil 2023 

###     **Descrição dos Gráficos**

  Os gráficos a seguir trazem uma visão abrangente sobre o cenário dos profissionais de dados no Brasil, com base na pesquisa *State of Data Brasil 2023*. A análise cobre desde perfis demográficos até uso de tecnologias emergentes e transformações no ambiente de trabalho:
  
[Codigo Python](/src/AnaliseExploratoriaDeDadosCodigo/base_principal/Explicação_Analise_Exploratoria_de_dados_State_of_base_Brazil_2023.md)


## **Distribuição de genêro dos profissionais de dados**

![download](https://github.com/user-attachments/assets/5acfee10-d566-4505-bbc1-fcfabc961ab3)

## **Distribuição Etária dos Profissionais de Dados no Brasil**
![download](https://github.com/user-attachments/assets/fdea1642-161f-4395-842e-c2099ba19921)

**Descrição**:  
     Este gráfico de barras mostra a quantidade de respondentes por faixa etária, utilizando a coluna `('P0', 'Faixa idade')` do dataset. As faixas etárias estão ordenadas de forma categórica (22-24, 25-29, ..., 55+), e os valores absolutos de respondentes são exibidos acima de cada barra.  
     - **Paleta de cores**: Tons de azul (`palette='Blues_d'`).  
     - **Destaques**:  
       - A faixa etária predominante é **30-34 anos**, seguida por **25-29 anos**.  
       - Há uma queda significativa na participação de profissionais acima de **44 anos**, indicando menor representatividade de profissionais sêniores ou uma migração para outras áreas.  
       - A faixa **55+** tem a menor participação, sugerindo desafios na retenção de profissionais mais experientes no setor.  

   - **Insights**:  
     - A maioria dos profissionais de dados está na fase inicial/média de carreira (25-39 anos).  
     - Empresas podem precisar investir em atração de talentos mais experientes ou em programas de mentoria para equilibrar a pirâmide etária.  

## **Distribuição data roles por nivel de experiência**


![image](https://github.com/user-attachments/assets/e6d193c8-eeb0-47f4-b859-319f65ecc74c)


### **Variação Salarial X Experiência/Cargo**

![download](https://github.com/user-attachments/assets/fad78574-d78a-4f7c-9828-e93f1235e1e4)
![download](https://github.com/user-attachments/assets/157c7fdb-ba78-4829-a4d9-5a0e7b4ed12c)

**Descrição:**

Este gráfico de boxplot apresenta a variação salarial (coluna 'Salario_medio') entre diferentes cargos, segmentando cada cargo pelos níveis de experiência ('Júnior', 'Pleno' e 'Sênior'). A base de dados utilizada é a pesquisa "State of Data - Brasil 2023", com foco nas colunas 'Cargo' e 'Experiencia'. Os cargos são exibidos no eixo X e os salários médios no eixo Y, com caixas coloridas que representam os diferentes níveis de experiência dentro de cada cargo.

**Tipo de gráfico:**

Boxplot com hue (diferença por cor) para representar a experiência.

**Paleta de cores:** Tons pastel suaves para facilitar a leitura comparativa.

**Organização dos dados:**

* Os cargos foram ordenados de acordo com os principais grupos da pesquisa.
* Os níveis de experiência foram ordenados como: Júnior, Pleno, Sênior.

**Destaques**

* Progressão salarial consistente: Em quase todos os cargos, observa-se uma progressão salarial clara entre os níveis de experiência.

* Cargos com maior amplitude salarial: Cargos como "Cientista de Dados" e "Engenheiro de Dados" apresentam maior dispersão nos salários, indicando variabilidade nas remunerações desses papéis.

* Cargos com maior mediana salarial: Os cargos de nível técnico mais especializado (como Engenheiro de Machine Learning e Especialista em IA) tendem a apresentar salários medianos mais altos mesmo em níveis juniores.

* Sobreposição entre níveis: Em alguns cargos, como Analista de BI, as faixas salariais de Pleno e Sênior se sobrepõem, o que pode indicar políticas salariais pouco diferenciadas por experiência ou distorções regionais.

**Insights:**

* Valorização da experiência: A experiência profissional continua sendo um fator relevante para a remuneração, mas sua influência varia conforme o cargo.

* Possíveis distorções: A sobreposição entre níveis pode indicar desafios na progressão salarial ou critérios pouco objetivos na definição de cargos.

* Atenção a cargos técnicos: Profissionais técnicos com habilidades avançadas (ex.: engenharia de IA) podem atingir salários elevados mesmo em níveis mais baixos de experiência.


## **Distribuição Salarial**

![download](https://github.com/user-attachments/assets/8c9596ef-2dfd-4944-a6b8-76f21a5c834b)




## **Uso de IA por profissionais de dados**

![download](https://github.com/user-attachments/assets/4a90da1b-d863-4dca-a7c0-cef3b9246a3f)



## **Uso de IA X Experiência**


![image](https://github.com/user-attachments/assets/2c91693d-e04b-41c3-87eb-0edf69a43b16)


## **Principais Motivos de Insatisfação**

![download](https://github.com/user-attachments/assets/7acb92ab-7eef-46a4-9e6e-f66f05acd8ed)
![download](https://github.com/user-attachments/assets/d6190403-29c9-4ea4-b794-c8b73874e790)


### **Faixa Salarial por Experiência em Dados **

![download](https://github.com/user-attachments/assets/90be4e22-0469-4dcb-a047-e20f4ab0e86b)

### **Ferramentas Mais Utilizadas**

![download](https://github.com/user-attachments/assets/bb9dfa9b-e029-4641-98cd-5af02c6c337c)

### **Ferramentas de BL por Tamanho da Empresa**

![download](https://github.com/user-attachments/assets/bb9dfa9b-e029-4641-98cd-5af02c6c337c)


### **Priorização de IA Generativa por Porte da Empresa**

![download](https://github.com/user-attachments/assets/e51211be-51ea-4213-8b95-07e5d30813ba)

### **Correlações no Mercado de Dados Brasileiro **


![download](https://github.com/user-attachments/assets/64767d7a-52f0-4bea-96dc-0b3efe951439)
