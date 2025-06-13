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

| Nome da Coluna                                 | Descrição                                           | Tipo de Dado                   |
| ---------------------------------------------- | --------------------------------------------------- | ------------------------------ |
| `idade`                                        | Idade do respondente                                | Numérico Contínuo              |
| `genero`                                       | Gênero do respondente                               | Categórico Nominal             |
| `cor_raca_etnia`                               | Identidade étnico-racial do respondente             | Categórico Nominal             |
| `nivel_de_ensino`                              | Nível mais alto de escolaridade alcançado           | Categórico Ordinal             |
| `cargo_atual`                                  | Cargo ocupado atualmente                            | Categórico Nominal             |
| `nivel`                                        | Nível de senioridade no cargo                       | Categórico Ordinal             |
| `faixa_salarial`                               | Faixa salarial mensal do respondente                | Categórico Ordinal             |
| `numero_de_funcionarios`                       | Número de funcionários da empresa                   | Categórico Ordinal             |
| `setor`                                        | Setor ou indústria da empresa                       | Categórico Nominal             |
| `atualmente_qual_a_sua_forma_de_trabalho?`     | Modelo de trabalho (remoto, híbrido, presencial)    | Categórico Nominal             |
| `tempo_de_experiencia_com_dados`               | Tempo de experiência na área de dados               | Categórico Ordinal ou Contínuo |
| `nivel_de_satisfacao_com_trabalho_atual`       | Nível de satisfação no trabalho atual (1 a 5)       | Ordinal                        |
| `voce_ja_utilizou_alguma_ferramenta_ia_gen...` | Utiliza IA generativa no trabalho                   | Binário (Sim/Não)              |
| `voce_conhece_ia_generativa?`                  | Conhece IA generativa                               | Binário (Sim/Não)              |
| `estado`                                       | Estado onde reside                                  | Categórico Nominal (UF)        |
| `regiao`                                       | Região do Brasil                                    | Categórico Nominal             |
| `possui_doutorado_estado`                      | Se há doutorado disponível na região                | Binário (Sim/Não)              |
| `criterio_flexibilidade_trabalho_remoto`       | Importância da flexibilidade/remoto                 | Binário                        |
| `criterio_ambiente_e_clima_organizacional`     | Importância do ambiente de trabalho                 | Binário                        |
| `criterio_aprendizado_e_boas_referencias`      | Importância de aprendizado e referências            | Binário                        |
| `criterio_plano_de_carreira_e_crescimento`     | Importância do plano de carreira                    | Binário                        |
| `criterio_maturidade_da_empresa_com_dados`     | Importância da maturidade tecnológica               | Binário                        |
| `criterio_qualidade_dos_gestores`              | Importância da qualidade da gestão                  | Binário                        |
| `criterio_reputacao_da_empresa_no_mercado`     | Importância da reputação da empresa                 | Binário                        |
| `Total_Tecnicos_Estado`                        | Número de técnicos no estado                        | Numérico Contínuo              |
| `Total_Docentes_Estado`                        | Número de docentes no estado                        | Numérico Contínuo              |
| `Total_IES_no_Estado`                          | Número de instituições de ensino superior no estado | Numérico Contínuo              |
