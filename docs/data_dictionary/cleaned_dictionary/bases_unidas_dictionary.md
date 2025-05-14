# Juncao de Dados 
Junção das bases MICRODADOS_ED_SUP_IES_2023 e State of Data Brazil 2023 limpas e selecionadas: Análise do Ensino Superior Consolidada e Dados_processados

# Dicionário de Dados

| Atributo                    | Tipo de Dado               | Descrição                                                                 |
|-----------------------------|----------------------------|---------------------------------------------------------------------------|
| NO_IES                      | Qualitativo não ordinal    | Nome da Instituição de Ensino Superior (IES).                            |
| SG_UF_IES                   | Qualitativo não ordinal    | Sigla do estado da IES.                                                  |
| TP_CATEGORIA_ADMINISTRATIVA | Qualitativo ordinal        | Tipo de categoria administrativa da IES (1 a 7).                         |
| QT_TEC_TOTAL                | Quantitativo discreto      | Quantidade total de técnicos na IES.                                     |
| QT_DOC_TOTAL                | Quantitativo discreto      | Quantidade total de docentes na IES.                                     |
| QT_DOC_EX_DOUT              | Quantitativo discreto      | Quantidade de docentes com doutorado.                                    |
| QT_DOC_EX_MEST              | Quantitativo discreto      | Quantidade de docentes com mestrado.                                     |
| QT_PERIODICO_ELETRONICO     | Quantitativo discreto      | Quantidade de periódicos eletrônicos disponíveis.                        |
| QT_LIVRO_ELETRONICO         | Quantitativo discreto      | Quantidade de livros eletrônicos disponíveis.                            |
| IN_ACESSO_PORTAL_CAPES      | Qualitativo binário        | Indica se há acesso ao portal CAPES (1 = Sim, 0 = Não).                  |
| IN_REPOSITORIO_INSTITUCIONAL| Qualitativo binário        | Indica se há repositório institucional (1 = Sim, 0 = Não).               |
| IN_SERVICO_INTERNET         | Qualitativo binário        | Indica se há serviço de internet (1 = Sim, 0 = Não).                     |
| idade                       | Quantitativo discreto      | Idade do participante.                                                   |
| genero                      | Qualitativo binário        | Gênero do participante (ex: Masculino, Feminino).                        |
| cor_raca                    | Qualitativo não ordinal    | Cor/raça/etnia do participante.                                          |
| estado                      | Qualitativo não ordinal    | Estado de residência do participante.                                    |
| nivel_ensino                | Qualitativo ordinal        | Nível de ensino do participante (ex: Graduação, Mestrado, Doutorado).    |
| situacao_trabalho           | Qualitativo não ordinal    | Situação de trabalho do participante (ex: CLT, CNPJ, Desempregado).      |
| setor                       | Qualitativo não ordinal    | Setor de atuação do participante (ex: Finanças, Tecnologia).             |
| tamanho_empresa             | Qualitativo ordinal        | Tamanho da empresa onde o participante trabalha (ex: Pequena, Grande).   |
| cargo                       | Qualitativo não ordinal    | Cargo do participante (ex: Analista de Dados, Cientista de Dados).      |
| nivel_cargo                 | Qualitativo ordinal        | Nível do cargo (ex: Júnior, Pleno, Sênior).                             |
| faixa_salarial              | Qualitativo ordinal        | Faixa salarial do participante (ex: 3001-4000, 8001-12000).             |
| exp_dados                   | Qualitativo ordinal        | Experiência do participante na área de dados (ex: 1-2 anos, 10+ anos).  |
| exp_ti                      | Qualitativo ordinal        | Experiência do participante na área de TI (ex: 0-1 anos, 5-6 anos).     |
| satisfacao                  | Quantitativo contínuo      | Nível de satisfação do participante (escala de 0.0 a 1.0).              |
| motivo_insatisfacao         | Qualitativo não ordinal    | Motivos de insatisfação do participante (ex: Salário, Crescimento).     |
| modelo_trabalho             | Qualitativo não ordinal    | Modelo de trabalho atual (ex: Presencial, Remoto, Híbrido).             |
| modelo_ideal                | Qualitativo não ordinal    | Modelo de trabalho ideal para o participante.                           |
| layoff                      | Qualitativo binário        | Indica se o participante foi afetado por layoff (Sim/Não).              |
| sql                         | Qualitativo binário        | Indica se o participante utiliza SQL (1 = Sim, 0 = Não).                |
| r                           | Qualitativo binário        | Indica se o participante utiliza R (1 = Sim, 0 = Não).                  |
| python                      | Qualitativo binário        | Indica se o participante utiliza Python (1 = Sim, 0 = Não).             |
| c_cpp_csharp                | Qualitativo binário        | Indica se o participante utiliza C/C++/C# (1 = Sim, 0 = Não).           |
| dotnet                      | Qualitativo binário        | Indica se o participante utiliza .NET (1 = Sim, 0 = Não).               |
| java                        | Qualitativo binário        | Indica se o participante utiliza Java (1 = Sim, 0 = Não).               |
| javascript                  | Qualitativo binário        | Indica se o participante utiliza JavaScript (1 = Sim, 0 = Não).         |
| linguagem_principal         | Qualitativo não ordinal    | Linguagem de programação principal do participante.                     |
| mysql                       | Qualitativo binário        | Indica se o participante utiliza MySQL (1 = Sim, 0 = Não).              |
| sql_server                  | Qualitativo binário        | Indica se o participante utiliza SQL Server (1 = Sim, 0 = Não).         |
| postgresql                  | Qualitativo binário        | Indica se o participante utiliza PostgreSQL (1 = Sim, 0 = Não).         |
| bigquery                    | Qualitativo binário        | Indica se o participante utiliza BigQuery (1 = Sim, 0 = Não).           |
| snowflake                   | Qualitativo binário        | Indica se o participante utiliza Snowflake (1 = Sim, 0 = Não).          |
| databricks                  | Qualitativo binário        | Indica se o participante utiliza Databricks (1 = Sim, 0 = Não).         |
| azure                       | Qualitativo binário        | Indica se o participante utiliza Azure (1 = Sim, 0 = Não).              |
| aws                         | Qualitativo binário        | Indica se o participante utiliza AWS (1 = Sim, 0 = Não).                |
| gcp                         | Qualitativo binário        | Indica se o participante utiliza GCP (1 = Sim, 0 = Não).                |
| powerbi                     | Qualitativo binário        | Indica se o participante utiliza Power BI (1 = Sim, 0 = Não).           |
| tableau                     | Qualitativo binário        | Indica se o participante utiliza Tableau (1 = Sim, 0 = Não).            |
| looker                      | Qualitativo binário        | Indica se o participante utiliza Looker (1 = Sim, 0 = Não).             |
| looker_studio               | Qualitativo binário        | Indica se o participante utiliza Looker Studio (1 = Sim, 0 = Não).      |
| excel_planilhas             | Qualitativo binário        | Indica se o participante utiliza Excel/Planilhas (1 = Sim, 0 = Não).    |
| ia_prioridade               | Qualitativo binário        | Indica se IA é prioridade para o participante (1 = Sim, 0 = Não).       |
| ia_uso_independente         | Qualitativo binário        | Indica se o participante utiliza IA de forma independente (1 = Sim, 0 = Não). |
| ia_uso_centralizado         | Qualitativo binário        | Indica se o participante utiliza IA de forma centralizada (1 = Sim, 0 = Não). |
| ia_copilots                 | Qualitativo binário        | Indica se o participante utiliza copilots de IA (1 = Sim, 0 = Não).     |
| ia_produtos_externos        | Qualitativo binário        | Indica se o participante utiliza produtos externos de IA (1 = Sim, 0 = Não). |
| ia_produtos_internos        | Qualitativo binário        | Indica se o participante utiliza produtos internos de IA (1 = Sim, 0 = Não). |
| ia_principal_negocio        | Qualitativo binário        | Indica se IA é principal para o negócio (1 = Sim, 0 = Não).             |
| ia_nao_prioridade           | Qualitativo binário        | Indica se IA não é prioridade (1 = Sim, 0 = Não).                       |
| ia_nao_sabe                 | Qualitativo binário        | Indica se o participante não sabe sobre IA (1 = Sim, 0 = Não).          |
| ia_nao_usa                  | Qualitativo binário        | Indica se o participante não usa IA (1 = Sim, 0 = Não).                 |
| ia_gratuita                 | Qualitativo binário        | Indica se o participante utiliza IA gratuita (1 = Sim, 0 = Não).        |
| ia_paga_pessoal             | Qualitativo binário        | Indica se o participante paga por IA pessoalmente (1 = Sim, 0 = Não).   |
| ia_paga_empresa             | Qualitativo binário        | Indica se a empresa paga por IA (1 = Sim, 0 = Não).                     |
| ia_usa_copilot              | Qualitativo binário        | Indica se o participante utiliza copilot de IA (1 = Sim, 0 = Não).      |
| tamanho_empresa_cat         | Qualitativo ordinal        | Categoria do tamanho da empresa (ex: Pequena, Média, Grande).           |
| satisfacao_binaria          | Qualitativo binário        | Satisfação do participante em formato binário (1 = Satisfeito, 0 = Não).|
| salario_medio               | Quantitativo contínuo      | Salário médio do participante.                                           |
| exp_dados_num               | Quantitativo contínuo      | Experiência em dados em anos (valor numérico).                           |
| exp_ti_num                  | Quantitativo contínuo      | Experiência em TI em anos (valor numérico).                              |
| nivel_ia                    | Qualitativo não ordinal    | Nível de adoção de IA (ex: Baixa adoção, IA em produtos).                |
| Contextualizacao            | Qualitativo não ordinal    | Contexto adicional sobre o participante ou pesquisa.                     |
