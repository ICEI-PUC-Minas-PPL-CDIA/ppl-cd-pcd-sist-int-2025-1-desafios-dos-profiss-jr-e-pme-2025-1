

# 📊 Análise de Microdados do Ensino Superior 2023

Esta análise utiliza dados abertos do ensino superior no Brasil para explorar aspectos como qualificação docente, acesso a tecnologia e estrutura das instituições. O processo é dividido em duas partes: uma análise automatizada com exportação em Excel e uma análise exploratória interativa com gráficos.

---

## ✅ **Parte 1: Análise Consolidada e Exportação para Excel**

```python
Arquivo: Analise_Ensino_Superior_Consolidada.py
```

### 🔍 Objetivo

Automatizar o processamento dos microdados do ensino superior, gerar análises estatísticas e exportar os resultados (inclusive gráficos) para um arquivo Excel organizado por abas.

### 🧩 Etapas do Processo

- **Importação de bibliotecas**: uso de `pandas`, `numpy`, `matplotlib`, `seaborn` e `xlsxwriter`.
- **Carregamento e limpeza dos dados**:
  - Leitura do arquivo CSV com separador `;` e codificação `latin-1`.
  - Conversão de colunas numéricas e remoção de *outliers* usando o método do Z-score.
- **Análises realizadas**:
  - Estatísticas descritivas.
  - Acesso tecnológico por estado (Portal CAPES, repositório institucional, internet).
  - Qualificação docente por estado (proporção de mestres e doutores).
  - Comparações por tipo de instituição (privada/pública).
  - Matriz de correlação entre variáveis quantitativas.
  - Identificação das 10 IES com maior número de doutores.
- **Exportação**: todos os resultados são salvos em abas no Excel, junto com gráficos gerados e inseridos como imagens nas planilhas.

---

## 🔎 **Parte 2: Análise Exploratória Interativa**

```python
Arquivo: Analise_Exploratoria_IES.py
```

### 🎯 Objetivo

Realizar uma análise interativa e visual dos microdados para investigar padrões em categorias administrativas, acesso a tecnologia e qualificação docente.

### 📌 Componentes da Análise

#### 1. **Carregamento e Limpeza**

- Seleção de colunas-chave relacionadas à infraestrutura e pessoal docente.
- Conversão de colunas para valores numéricos e limpeza de outliers via Z-score.

#### 2. **Análise Descritiva**

- Geração de estatísticas básicas (`describe()`).
- Matriz de correlação entre variáveis quantitativas com `seaborn.heatmap`.

#### 3. **Análise por Categoria Administrativa**

- Agrupamento das instituições por tipo (ex: públicas, privadas).
- Cálculo da média de doutores e mestres por grupo.
- Visualização comparativa com gráfico de barras.

#### 4. **Acesso a Recursos Tecnológicos**

- Cálculo da proporção de instituições com acesso a:
  - Portal de Periódicos CAPES.
  - Repositório institucional.
  - Serviço de internet.
- Visualização de dispersão para verificar relação entre número de periódicos e número de doutores, colorido por tipo de instituição.

---

## 🧠 Conclusões e Aplicações

Este código serve como base para **diagnósticos educacionais** e **análises institucionais**, sendo útil para:

- Órgãos públicos e reguladores da educação.
- Pesquisadores interessados em infraestrutura e qualificação docente.
- Análises comparativas entre instituições e estados.

---
