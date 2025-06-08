# Dicionario de Dados da Unificaçâo

A base de dados é o resultado da combinação de dados de uma pesquisa ('State of Data')  com dados agregados de Instituições de Ensino Superior (IES) no Brasil.

**Dados de Pesquisa Limpos e Selecionados: A maioria das colunas virá do conjunto de dados da pesquisa original ('State_of_data_BR_2023_Kaggle - df_survey_2023.csv'), após passar por um processo de limpeza e seleção. Isso inclui:**

* Características do Respondente: Idade, Gênero, Cor/Raça/Etnia, Nível de Ensino.
* Informações de Trabalho: Cargo Atual, Nível de Senioridade, Faixa Salarial, Número de Funcionários da empresa, Setor da empresa, Forma de Trabalho Atual e Preferida, Tempo de Experiência na área de dados, Satisfação com a empresa atual.
* Motivos de Insatisfação e Critérios de Escolha: As colunas que começavam com 'P2_l_' e 'P2_o_' foram selecionadas e preenchidas (com 0 para colunas específicas e 'Desconhecido' para outras). Elas representam os motivos de insatisfação e os critérios considerados ao escolher uma empresa.
* Estado de Residência: Uma coluna ('uf_residencia') que indica o estado onde o respondente da pesquisa reside.

 **Dados Agregados do IES por Estado: Dados agregados do arquivo 'MICRODADOS_ED_SUP_IES_2023.CSV' foram unidos ao DataFrame da pesquisa.  Essas colunas foram adicionadas com base na correspondência do estado:**

* Total de IES no Estado: A contagem total de Instituições de Ensino Superior no estado correspondente.
* Total de Técnicos no Estado: A soma total de técnicos que trabalham nas IES do estado correspondente.
* Total de Docentes no Estado: A soma total de docentes que trabalham nas IES do estado correspondente.

**Estrutura da Planilha:**

* Cada linha na planilha corresponde a um respondente individual da pesquisa.
* As colunas contêm as informações mencionadas acima, combinando os dados específicos do respondente com as informações agregadas sobre as IES no estado de residência desse respondente.


| Coluna                                | Descrição                                                                 | Tipo de Dado                        |
|---------------------------------------|---------------------------------------------------------------------------|-------------------------------------|
| Idade                                 | Idade do respondente                                                     | Numérico Contínuo                   |
| Genero                                | Gênero do respondente                                                    | Categórico Nominal                  |
| Etnia                                 | Identidade étnico-racial do respondente                                  | Categórico Nominal                  |
| Nivel_Educacao                        | Nível mais alto de escolaridade alcançado                                | Categórico Ordinal                  |
| Cargo_Atual                           | Cargo ocupado atualmente                                                 | Categórico Nominal                  |
| Senioridade                           | Nível de senioridade no cargo                                            | Categórico Ordinal                  |
| Faixa_Salarial                        | Faixa salarial mensal do respondente                                     | Categórico Ordinal                  |
| Tamanho_Empresa                       | Número de funcionários da empresa onde trabalha                          | Categórico Ordinal                  |
| Industria                             | Setor ou indústria da empresa                                            | Categórico Nominal                  |
| Modelo_Trabalho_Atual                 | Modelo de trabalho (remoto, híbrido, presencial)                         | Categórico Nominal                  |
| Experiencia_Area                      | Tempo de experiência na área de dados                                    | Categórico Ordinal ou Contínuo (*)  |
| Satisfacao_Atual                      | Nível de satisfação no trabalho atual                                    | Ordinal (1 a 5)                     |
| IA_Generativa_Utiliza                 | Utiliza IA generativa no trabalho                                        | Binário (Sim/Não)                   |
| IA_Generativa_Conhece                 | Conhece IA generativa                                                    | Binário (Sim/Não)                   |
| Estado                                | Estado onde reside                                                       | Categórico Nominal (UF)             |
| Regiao                                | Região do Brasil                                                         | Categórico Nominal                  |
| Possui_Doutorado_Estado               | Se há doutorado disponível na região                                     | Binário                             |
| Criterio_Flexibilidade_Remoto         | Importância da flexibilidade/remoto                                      | Binário                             |
| Criterio_Ambiente_Clima               | Importância do ambiente de trabalho                                      | Binário                             |
| Criterio_Aprendizado_Referencias      | Importância de aprendizado e referências                                 | Binário                             |
| Criterio_Plano_Carreira_Crescimento   | Importância do plano de carreira                                         | Binário                             |
| Criterio_Maturidade_Tecnologia_Dados  | Importância da maturidade tecnológica                                    | Binário                             |
| Criterio_Qualidade_Gestores           | Importância da qualidade da gestão                                       | Binário                             |
| Criterio_Reputacao_Mercado            | Importância da reputação da empresa                                      | Binário                             |
| Total_Tecnicos_Estado                 | Número de técnicos no estado                                             | Numérico Contínuo                   |
| Total_Docentes_Estado                 | Número de docentes no estado                                             | Numérico Contínuo                   |
| Total_IES_no_Estado                   | Número de instituições de ensino superior no estado                      | Numérico Contínuo                   |
