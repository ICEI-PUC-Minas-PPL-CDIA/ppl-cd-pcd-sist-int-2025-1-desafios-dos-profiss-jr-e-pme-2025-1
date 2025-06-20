# Modelos do sistema

* [LightGBM (Light Gradient Boosting Machine)](/assets/models/lightgbm.ipynb)
O LightGBM é um algoritmo de aprendizado de máquina baseado em árvores de decisão, reconhecido por sua alta velocidade e eficiência. No contexto do problema, ele foi implementado dentro de um pipeline que primeiro pré-processa os dados (padronizando valores numéricos e codificando variáveis categóricas) e depois utiliza a técnica SMOTE para criar dados sintéticos da classe minoritária (profissionais "insatisfeitos").

Este passo de balanceamento visa ensinar o modelo a reconhecer melhor os padrões de ambos os grupos. O modelo final, otimizado por meio de RandomizedSearchCV, demonstrou uma excelente capacidade de predição, identificando corretamente 87% dos profissionais insatisfeitos no conjunto de teste.

* [XGBoost (eXtreme Gradient Boosting)](/assets/models/xgboost.ipynb)
O XGBoost é um dos mais robustos e populares algoritmos de gradient boosting, amplamente utilizado em competições e na indústria pela sua precisão e flexibilidade. A abordagem utilizada neste notebook também envolveu um pipeline de pré-processamento similar. No entanto, para tratar o desbalanceamento de classes, em vez de criar dados novos, foi utilizado o parâmetro interno do XGBoost, scale_pos_weight. Este método ajusta o treinamento do modelo para que ele dê mais importância aos erros na classificação da classe minoritária ("insatisfeitos"). O modelo resultante, também otimizado com RandomizedSearchCV, alcançou uma performance de classificação idêntica ao LightGBM, identificando 87% dos profissionais insatisfeitos e obtendo uma precisão de 100% para esta mesma classe no conjunto de teste.
  




