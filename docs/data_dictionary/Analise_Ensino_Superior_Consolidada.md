# Dicionário de Dados - Análise do Ensino Superior Consolidada

Limpeza e Seleção de dados da base MICRODADOS_ED_SUP_IES_2023

| Atributo                      | Tipo de dado               | Descrição                                                                 |
|-------------------------------|----------------------------|---------------------------------------------------------------------------|
| NO_IES                        | Qualitativo nominal        | Nome da instituição de ensino superior                                   |
| SG_UF_IES                     | Qualitativo nominal        | Sigla do estado onde a instituição está localizada                       |
| TP_CATEGORIA_ADMINISTRATIVA   | Qualitativo ordinal        | Categoria administrativa da instituição (2=Estadual, 3=Municipal, 4=Privada com fins lucrativos, 5=Privada sem fins lucrativos, 7=Federal) |
| QT_TEC_TOTAL                  | Quantitativo discreto      | Quantidade total de técnicos administrativos na instituição              |
| QT_DOC_TOTAL                  | Quantitativo discreto      | Quantidade total de docentes na instituição                              |
| QT_DOC_EX_DOUT                | Quantitativo discreto      | Quantidade de docentes com título de doutorado                           |
| QT_DOC_EX_MEST                | Quantitativo discreto      | Quantidade de docentes com título de mestrado                            |
| QT_PERIODICO_ELETRONICO       | Quantitativo discreto      | Quantidade de periódicos eletrônicos disponíveis                         |
| QT_LIVRO_ELETRONICO           | Quantitativo discreto      | Quantidade de livros eletrônicos disponíveis                             |
| IN_ACESSO_PORTAL_CAPES        | Qualitativo binário        | Indica se a instituição tem acesso ao portal CAPES (1=Sim, 0=Não)        |
| IN_REPOSITORIO_INSTITUCIONAL  | Qualitativo binário        | Indica se a instituição possui repositório institucional (1=Sim, 0=Não)  |
| IN_SERVICO_INTERNET           | Qualitativo binário        | Indica se a instituição oferece serviço de internet (1=Sim, 0=Não)       |
