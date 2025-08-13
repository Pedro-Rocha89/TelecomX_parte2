# TelecomX_parte2
 
Este projeto faz parte do **Challenge ONE Data Science da Alura**, focado na análise de dados da empresa TelecomX para construir um modelo de Machine Learning capaz de prever a **evasão de clientes (Churn)**. A partir dos dados tratados na primeira etapa do desafio, o objetivo é identificar os fatores que mais influenciam o cancelamento de serviços e desenvolver um modelo preditivo para identificar clientes com alto risco de cancelamento do serviço, permitindo que a empresa tome ações proativas de retenção.

## 📝 Etapas

  - `Etapa 1`: **Carregamento e Preparação Inicial dos Dados**
    Carregamento do dataset pré-processado da primeira fase do desafio e remoção de colunas que não agregam valor preditivo, como o `id_cliente`.

    **Métodos utilizados:**

      * `pd.read_csv()` para carregar os dados.
      * `.drop(columns=[...])` para remover colunas irrelevantes.
        

  - `Etapa 2`: **Engenharia de Features - Encoding de Variáveis Categóricas**
    Transformação das variáveis categóricas (como `genero`, `servico_internet`, `tipo_contrato` e `metodo_pagamento`) em formato numérico utilizando o `OneHotEncoder`, para      que possam ser utilizadas pelos modelos de machine learning.

    **Bibliotecas e Métodos utilizados:**

      * `sklearn.compose.make_column_transformer`
      * `sklearn.preprocessing.OneHotEncoder`
      * `pd.DataFrame()` para reconstruir o dataframe após a transformação.
        

 - `Etapa 3`: **Balanceamento de Dados**
    O conjunto de dados apresentou um desequilíbrio de classes, com 73.5% dos clientes não cancelando e 26.5% cancelando. Para evitar que o modelo ficasse enviesado, a técnica **SMOTE (Synthetic Minority Over-sampling Technique)** foi aplicada para criar um conjunto de dados de treino balanceado.

    **Bibliotecas e Métodos utilizados:**

      * `imblearn.over_sampling.SMOTE`
      * `.fit_resample()`

 - `Etapa 4`: **Seleção de Variáveis e Divisão do Dataset**
    Com base na análise de correlação entre as variáveis e a variável alvo (`cancelou_servico`), foram selecionadas as features mais relevantes para o modelo. O dataset foi então dividido em conjuntos de treino e teste (70/30).

    **Variáveis Selecionadas:** `tipo_contrato_Month-to-month`, `servico_internet_Fiber optic`, `metodo_pagamento_Electronic check`, `servico_internet_No`, `tipo_contrato_Two year`, `meses_de_servico`, `gastos_totais`.

    **Métodos utilizados:**

      * `pandas.DataFrame.corr()`
      * `sklearn.model_selection.train_test_split`

 - `Etapa 5`: **Treinamento e Avaliação de Modelos de Machine Learning**
    Foram treinados e avaliados dois modelos de classificação: **Árvore de Decisão** e **Random Forest**. O desempenho foi medido utilizando as métricas de Acurácia, Precisão, Recall, F1-Score e a Matriz de Confusão.

    **Bibliotecas e Métodos utilizados:**

      * `sklearn.tree.DecisionTreeClassifier`
      * `sklearn.ensemble.RandomForestClassifier`
      * `sklearn.metrics.accuracy_score`, `precision_score`, `recall_score`, `f1_score`
      * `sklearn.metrics.ConfusionMatrixDisplay`
  
        
## 📈 Análise e Conclusão

  * **Tipo de Contrato Mensal:** É o fator mais significativo. Clientes com contratos mensais têm uma taxa de cancelamento de **42.7%**, indicando uma baixa fidelidade e alta sensibilidade a ofertas concorrentes.
  * **Serviço de Internet via Fibra Ótica:** Este serviço, embora premium, está associado a uma alta taxa de churn de **41.9%**. Isso pode ser um indicativo de problemas de estabilidade, preço elevado ou expectativas não atendidas que precisam ser investigados.
  * **Forma de Pagamento por Cheque Eletrônico:** Clientes que utilizam este método de pagamento apresentam uma taxa de cancelamento de **45.3%**, consideravelmente maior que a de outros métodos. Isso pode estar relacionado à inconveniência do pagamento manual, que leva os clientes a reavaliarem o serviço a cada mês.
  * **Tempo de Contrato (meses\_de\_servico):** A análise de boxplot mostrou que clientes que cancelam o serviço tendem a ter um tempo de permanência muito menor na empresa. O risco de churn é mais alto nos primeiros meses de contrato.
  * **Contrato de Dois Anos e Ausência de Internet:** Em contrapartida, clientes com contratos de 2 anos (taxa de churn de apenas **2.8%**) e aqueles sem serviço de internet (taxa de churn de **7.4%**) são os mais leais.

## 📄 Relatório

Com base nos achados da análise, são propostas as seguintes recomendações para reduzir a taxa de cancelamento:

  * **Incentivar Contratos de Longo Prazo:** Criar ofertas e descontos especiais para clientes com contrato mensal migrarem para planos de 1 ou 2 anos.
  * **Otimizar o Serviço de Fibra Ótica:** Realizar uma investigação focada na qualidade e no custo-benefício do serviço de fibra ótica para identificar e corrigir os principais pontos de insatisfação.
  * **Promover Formas de Pagamento Automáticas:** Oferecer incentivos para que clientes que usam cheque eletrônico mudem para métodos de pagamento automáticos, como débito em conta ou cartão de crédito.
  * **Criar um Programa de Onboarding:** Desenvolver uma estratégia de engajamento para os primeiros meses de contrato, período em que o risco de churn é maior, oferecendo suporte proativo e benefícios iniciais.

## 🔨 Ferramentas e Aplicativos Utilizados

  - `Python`
  - `Google Colab`
  - `Pandas`
  - `Scikit-learn`
  - `Plotly Express`
  - `Imbalanced-learn`

## 💻 Desenvolvedores

[\<img loading="lazy" src="https://avatars.githubusercontent.com/u/201495780?s=96\&v=4" width=115\>\<br\>\<sub\>Pedro Rocha\</sub\>](https://github.com/Pedro-Rocha89)
