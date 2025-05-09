
# Explicação do Código para Junção das Bases e Limpeza
[Acesse o Codigo ](/src/Codigo_Juncao/JuncaoDeBases.ipynb)


---

###  Importação de bibliotecas

```python
import pandas as pd
```


###  Carregamento dos dados

####  Microdados de Instituições de Ensino Superior (INEP)

```python
try:
    df_ies = pd.read_csv('MICRODADOS_ED_SUP_IES_2023.CSV', sep=';', encoding='utf-8')
except UnicodeDecodeError:
    df_ies = pd.read_csv('MICRODADOS_ED_SUP_IES_2023.CSV', sep=';', encoding='latin-1')
```

* Tenta carregar o arquivo CSV dos microdados do INEP com codificação `utf-8`.
* Se houver erro de decodificação, usa `latin-1` como alternativa.

###  Base da pesquisa "State of Data - Brasil 2023"

```python
df_survey = pd.read_csv('State_of_data_BR_2023_Kaggle - df_survey_2023.csv', sep=',', encoding='utf-8')
```

Carrega a base principal da pesquisa usando codificação `utf-8` e separador `,`.

---

###  Mapeamento e renomeação de colunas

```python
rename_survey = {
    "('P1_a ', 'Idade')": 'idade',
    "('P1_b ', 'Genero')": 'genero',
    ...
}
```

* Define um dicionário `rename_survey` para renomear as colunas originais (com nomes compostos e espaços) para nomes mais simples e padronizados.
* As colunas representam informações como idade, gênero, formação, cargo, salário, uso de ferramentas, etc.

---

###  Seleção e renomeação de colunas

```python
df_survey = df_survey.rename(columns=rename_survey)
```

Renomeia as colunas do DataFrame `df_survey` com base no dicionário `rename_survey`.

```python
selected_columns = [
    'idade', 'genero', 'cor_raca', 'SG_UF_IES', 'nivel_ensino', ...
]
```

Define a lista das colunas **relevantes para análise**.

```python
df_survey = df_survey[selected_columns]
```

Seleciona apenas as colunas da lista no DataFrame, descartando o restante.

---

###  Salvamento do resultado

```python
df_survey.to_csv('dados_selecionados.csv', index=False, encoding='utf-8')
```

Exporta o novo dataset tratado para um arquivo CSV chamado `dados_selecionados.csv`, sem o índice.

```python
print("Dataset final salvo com sucesso!")
print(f"Dimensões: {df_survey.shape}")
```

Exibe uma mensagem de sucesso e as dimensões (linhas, colunas) do DataFrame final.

---
