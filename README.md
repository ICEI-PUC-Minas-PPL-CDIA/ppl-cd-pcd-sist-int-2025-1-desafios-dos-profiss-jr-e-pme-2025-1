# Desafios para profissionais junior e microempresas no uso de dados e tecnologia, IA generativa e LLM’S.

## Contextualização

Este projeto, desenvolvido no âmbito do curso de Ciência de Dados da PUC Minas, analisa os desafios enfrentados por profissionais juniores e microempresas brasileiras na adoção de Inteligência Artificial Generativa (IA Generativa) e *Large Language Models* (LLMs). Com base em dados do *State of Data Brazil 2023* e microdados da educação superior de 2023, o estudo utiliza técnicas de *machine learning* para identificar fatores que influenciam a satisfação profissional e a competitividade no mercado de IA.

## Objetivo

Desenvolver um sistema inteligente que identifique os principais obstáculos para profissionais juniores e microempresas na utilização de IA Generativa, propondo insights para promover maior inclusão e competitividade no setor.

## Metodologia

1. **Fontes de Dados:**
   - *State of Data Brazil 2023*: Dados demográficos e profissionais de 5.293 respondentes, coletados pela Data Hackers e Bain & Company.
   - *Microdados da Educação Superior 2023*: Informações sobre instituições de ensino superior no Brasil, fornecidas pelo INEP.

2. **Preparação dos Dados:**
   - Limpeza, transformação e combinação das bases, resultando em um arquivo unificado (`dados_tratados_combinados.csv`).
   - Script de pré-processamento disponível em `limpeza_e_combinacao.ipynb`.

3. **Indução de Modelos:**
   - Dois modelos de *machine learning* foram desenvolvidos para prever a satisfação profissional:
     - **LightGBM com SMOTE**: Utiliza reamostragem para lidar com desbalanceamento de classes.
     - **XGBoost com Ponderação de Classes**: Ajusta pesos para a classe minoritária (*Insatisfeito*).
   - Ambos os modelos foram otimizados com *RandomizedSearchCV* e avaliados por métricas como acurácia, AUC-ROC, precisão e *recall*.

4. **Resultados:**
   - Acurácia de 96% e AUC-ROC acima de 0.95 em ambos os modelos.
   - Principais fatores de insatisfação: *falta de oportunidade de crescimento*, *salário não correspondente ao mercado* e *falta de maturidade analítica na empresa*.
   - Visualizações (matrizes de confusão, curvas ROC, curvas de aprendizado e importância de *features*) disponíveis em `/imagens/graficos/`.

## Estrutura do Repositório

- **`/src`**: Código-fonte, incluindo `limpeza_e_combinacao.ipynb` para preparação dos dados.
- **`/assets/data`**: Bases de dados originais e tratadas (`dados_tratados_combinados.csv`).
- **`/imagens/graficos`**: Visualizações geradas (matrizes de confusão, curvas ROC, etc.).
- **`/SlidePitch.pdf`**: Slides da apresentação final.
- **`/Pitch.mp4`**: Vídeo explicativo do projeto.
- 
## Resultados e Insights

- **Para Profissionais Juniores**: A falta de oportunidades de crescimento e a exigência de experiência prévia são barreiras significativas. Investir em capacitação e demonstrar habilidades práticas pode aumentar a empregabilidade.
- **Para Microempresas**: Limitações financeiras e estruturais dificultam a adoção de IA Generativa. Soluções acessíveis e parcerias com instituições educacionais podem impulsionar sua competitividade.
- O modelo XGBoost foi considerado preferível por sua simplicidade e eficiência, mas ambos os modelos validaram os mesmos fatores preditores, reforçando a confiabilidade dos resultados.

## Limitações e Melhorias Futuras

- **Limitações**: Desbalanceamento de classes, foco em dados de 2023 e ênfase em profissionais em detrimento de microempresas.
- **Melhorias**: Incluir dados qualitativos, expandir o escopo para infraestrutura tecnológica e realizar análises temporais com dados de outros anos.

## Como Executar

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-repositorio
   ```
2. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```
3. Execute o script de pré-processamento:
   ```bash
   jupyter notebook src/limpeza_e_combinacao.ipynb
   ```
4. Explore os modelos e visualizações nos notebooks correspondentes.



## Integrantes
* Caio César de Oliveira
* Nicolas Rodrigues Duarte
* Gabriel Fernandes Souza
* Thiago Domingos Venturim Ribeiro dos Santos

## Professores:

* Hayala Nepomuceno Curto

* Prof. Hugo Bastos de Paula

## Instruções de utilização

Assim que a primeira versão do sistema estiver disponível, deverá complementar com as instruções de utilização. Descreva como instalar eventuais dependências e como executar a aplicação.

## Conteúdo: 

Acesse o [Report](/docs/report.md)  para uma apresentação completa do projeto.

| [Assets](/assets/)                   | [Docs](/docs/)                           | [Src](/src/)                                                 |
|--------------------------------------|------------------------------------------|-------------------------------------------------------------
| [Data](/assets/data)                 | [Imagens](/docs/imagens)                 |  [AnaliseExploratoria](/src/AnaliseExploratoriaDeDadosCodigo)  |  
| [Models](/assets/models)             | [Report](/docs/report.md)                |  [Limpeza](/src/limpeza_e_combinacao.ipynb)            | 
| [results](/assets/results)           |                                          |                       | 




## Histórico de Versões

* **Versão 1.0.0 (Final)**
    * **ENTREGA:** Versão final do projeto entregue. Inclui a apresentação, o vídeo da aplicação, `README.md` atualizado e arquivo `CITATION.cff` preenchido.
    * *Corresponde à conclusão da Sprint 6.*

* **Versão 0.5.0**
    * **NOVO:** Segundo modelo ajustado e otimizado.
    * **NOVO:** Análise comparativa entre os modelos e documentação técnica finalizada.
    * *Corresponde à conclusão da Sprint 5.*

* **Versão 0.4.0**
    * **NOVO:** Indução e otimização do primeiro modelo de machine learning.
    * **NOVO:** Indução da versão preliminar do segundo modelo para avaliação.
    * *Corresponde à conclusão da Sprint 4.*

* **Versão 0.3.0**
    * **NOVO:** Implementação das rotinas de limpeza e transformação dos dados.
    * **STATUS:** Base de dados considerada pronta para a etapa de modelagem.
    * *Corresponde à conclusão da Sprint 3.*

* **Versão 0.2.0**
    * **NOVO:** Conclusão da Análise Exploratória de Dados (AED).
    * **NOVO:** Implementação do processo de seleção de atributos e enriquecimento da base.
    * *Corresponde à conclusão da Sprint 2.*

* **Versão 0.1.0**
    * **NOVO:** Definição dos temas, coleta e validação da base de dados.
    * **NOVO:** Elaboração do documento de contexto e planejamento inicial do projeto.
    * *Corresponde à conclusão da Sprint 1.*
 
 * **Versão 0.1.1**
    * **ALTERAÇÃO:** Atualização da documentação do projeto. O código fonte permaneceu inalterado.
  
   ## Referências

- Kaggle: *State of Data Brazil 2023*. Disponível em: [Kaggle](https://www.kaggle.com/datasets/datahackers/state-of-data-brazil-2023).
- INEP: *Microdados do Censo da Educação Superior 2023*. Disponível em: [INEP](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/microdados/censo-da-educacao-superior).
