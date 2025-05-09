

#  Codigo da Análise Exploratória da Junção de Bases

Este código realiza uma **análise exploratória de dados (EDA)** com base no arquivo `Juncao_de_Dados.csv`


---

##  1. Importação de Bibliotecas

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

* `pandas`: manipulação de dados tabulares.
* `numpy`: operações numéricas.
* `matplotlib.pyplot`: criação de gráficos.

---

##  2. Carregamento do Dataset

```python
df = pd.read_csv('Juncao_de_Dados.csv')
```

Carrega os dados da pesquisa em um DataFrame `df`.

---

##  3. Configurações Globais de Estilo dos Gráficos

```python
plt.rcParams['figure.figsize'] = (10, 6)
plt.rcParams['font.size'] = 12
```

Define o tamanho e fonte padrão dos gráficos.

---

##  4. Conversão de Faixa Salarial para Valor Numérico

```python
def parse_salary(s):
    ...
df['salario_medio'] = df['faixa_salarial'].apply(parse_salary)
```

* Converte faixas como `"R$ 2.000 a R$ 4.000"` para médias numéricas.
* Retorna `NaN` para ausentes ou não respondidos.

---

##  5. Conversão de Experiência em Dados para Número

```python
def parse_exp(exp):
    ...
df['exp_dados_num'] = df['exp_dados'].apply(parse_exp)
```

* `"menos de 1 ano"` → `0.5`
* `"mais de 10 anos"` → `10.5`
* `"3 a 5 anos"` → média `4.0`

---

##  6. Gráfico: Distribuição da Satisfação Profissional

```python
satisfacao_counts = df['satisfacao'].value_counts().sort_index()
bars = plt.bar(...)
```

* Gráfico de barras mostrando o número de profissionais satisfeitos (1) e insatisfeitos (0).
* Adiciona contagens no topo das barras.

---

##  7. Gráfico: Boxplot de Experiência por Satisfação

```python
box = plt.boxplot([exp_insatisfeitos, exp_satisfeitos], ...)
```

* Boxplot comparando a experiência de quem está satisfeito vs insatisfeito.
* **Atenção**: variável `colors` usada, mas **não foi definida**. É necessário incluir:

```python
colors = ['#ff7f0e', '#1f77b4']
```

---

##  8. Uso de Tecnologias por Tamanho de Empresa

```python
tech_columns = ['sql', 'r', 'python', 'c_cpp_csharp', 'dotnet', 'java', 'javascript']
tech_by_size = df.groupby('tamanho_empresa')[tech_columns].mean()
```

* Cria gráfico de barras agrupadas.
* Compara o uso médio de tecnologias por empresas de diferentes portes.

---

##  9. Tecnologias por Nível de Satisfação

```python
lang_satisfied = df[df['satisfacao'] == 1][tech_columns].mean()
lang_unsatisfied = df[df['satisfacao'] == 0][tech_columns].mean()
```

* Dois gráficos horizontais:

  * Um com tecnologias mais usadas por satisfeitos.
  * Outro com tecnologias mais usadas por insatisfeitos.

---

##  10. Satisfação por Tamanho da Empresa (Barras Empilhadas)

```python
tamanho_counts = df.groupby(['tamanho_empresa', 'satisfacao']).size().unstack().fillna(0)
```

* Gráfico de **barras empilhadas**.
* Mostra o número de satisfeitos e insatisfeitos por porte da empresa.
* Adiciona rótulos com total no topo de cada barra.

---
