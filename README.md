# Análise de Dados - Walmart

Objetivo: Realizar a análise de um conjunto de dados de compras do Walmart, focando no comportamento de compra dos clientes com base em diferentes atributos, como gênero, categoria de produto, cidade, estado civil e faixa etária. 

####  Objetivo

Gerar insights e visualizar as tendências desses dados de maneira eficiente. Traçando um perfil do cliente e suas tendencias na hora da compra.

#### Dataset Utilizado

 - [Kaggle - Walmart Dataset](https://www.kaggle.com/datasets/devarajv88/walmart-sales-dataset)


#### Bibliotecas Utilizadas


- ``pandas: Para manipulação e análise de dados ``
- ``matplotlib: Para criação de gráficos``
- ``numpy: Para computação numérica``
- ``seaborn: Para visualização de dados baseada em matplotlib``
- ``xgboost: Para modelos de gradiente boosting``
- ``sklearn: Para machine learning, incluindo modelos, métricas e pré-processamento``
- ``copy: Módulo para manipulação de objetos em Python``


#### Descrição das Variáveis


| Variável          | Descrição                                                        |
| ----------------- | ---------------------------------------------------------------- |
| User_ID           | Identificação do usuário.                                         |
| Product_ID        | Identificação do produto.                                         |
| Gender            | Gênero do usuário. |
| Age               | Faixa etária do usuário.                                          |
| Occupation        | Ocupação do usuário representada por um código numérico.         |
| City_Category     | Categoria da cidade (A, B, ou C).                                 |
| Stay_In_Current_City_Years | Quantos anos o usuário está na cidade atual (representado como 1, 2, 3, ou 4+). |
| Marital_Status    | Estado civil.          |
| Product_Category  | Categoria do produto.                                             |
| Purchase          | Valor da compra.



##### Tipos das Variáveis


| Variável          | Tipo                                                        |
| ----------------- | ---------------------------------------------------------------- |
|     Occupation       |          Inteiro - Categórica - Quantitativa (representa categorias ou grupos de ocupação, mas é tratado como numérico)          |
|     Marital_Status   |          Inteiro  - Categórica  - Quantitativa (também representa categorias, mas é numérico)          |
|     Product_Category |          Inteiro  - Categórica - Quantitativa (representa categorias de produtos)         |
|     Purchase         |          Inteiro - Cardinal - Quantitativa (representa o valor da compra)         |
 |     Product_ID         |    Categórica - Nominal - Qualitativa (identificadores de produtos)   |
 |     Gender         |    Categórica - Nominal - Qualitativa (representa duas categorias: 'Male' e 'Female')   |
 |     User_ID         |    Categórica - Nominal - Qualitativa (representa categorias de usuários)   |
 |     Age         |    Categórica - Ordinal - Qualitativa (faixas etárias)   |
 |     City_Category         |    Categórica - Nominal - Qualitativa (representa categorias de cidade)   |
 |     Stay_In_Current_City_Years         |    Categórica - Ordinal - Qualitativa (representa a duração da estadia em anos como categoria)   |

### Fases da Análise

##### 1. Limpeza e Agrupamento dos Dados

Identificar e corrigir problemas nos dados brutos que podem comprometer a precisão da análise, verificando se há dados nulos/ausentes, discrepantes(outliers) ou inconsistentes. Nessa fase agrupando os dados por variáveis como estado civil, cidade e gênero, permitindo uma visão geral da distribuição dos clientes e suas compras. Gráficos de barras são gerados para ilustrar a quantidade e porcentagem de compras para cada grupo, ajudando a identificar padrões no comportamento de compra com base nessas características demográficas.

##### 2. Identificação de Outliers

Uma fase importantissima na preparação dos dados envolve a identificação de outliers no valor das compras. Isso é feito usando a métrica do Intervalo Interquartil (IQR), que ajuda a identificar compras muito abaixo ou acima da média. Essa etapa é importante para garantir que esses valores  não distorçam a análise e as previsões subsequentes.

##### 3. Agrupamentos e Percentuais

Essa etapa tem como objetivo entender a distribuição dos dados em diferentes categorias e calcular estatísticas para cada grupo. Isso ajuda a identificar padrões relevantes e gerar insights  sobre o comportamento dos clientes, produtos e compras.


##### 4. Geração de Gráficos

Nessa etapa, convertemos os números e percentuais calculados em representações visuais, facilitando a identificação de padrões.

##### 5. Preparação dos Dados para Machine Learning

Após a análise exploratória inicial, os dados são preparados para modelos de machine learning. Que envolve mais uma fase de limpeza e transformação dos dados, com o objetivo de torna-los dados mais adequados para o modelo. São aplicadas transformações de dados, como:

- Codificação de Variáveis Categóricas: Variáveis como Gender, City_Category e Age são transformadas em formatos numéricos utilizando Label Encoding para que os modelos de machine learning possam processá-las.

- Normalização/Padronização: Os valores das variáveis numéricas, como Purchase, podem ser normalizados ou padronizados, para melhorar a performance dos modelos de Machine Learning.

- Divisão dos Dados: Os dados são então divididos em conjuntos de treino e teste. O conjunto de treino é usado para ajustar o modelo, enquanto o conjunto de teste é mantido separado para avaliar a capacidade do modelo de fazer previsões sobre dados não vistos. Dividimos 25% para teste e 75% para treino.

##### 6. Seleção e Treinamento de Modelos de Machine Learning

Nesta fase, diferentes algoritmos de machine learning são aplicados, como por exemplo:

- ###### Regressão Linear (LinearRegression)

A Regressão Linear é um modelo estatístico que tenta prever o valor de uma variável dependente (target) com base em uma ou mais variáveis independentes (features) usando uma relação linear.
O modelo foi treinado com os dados de treino (X_treino, y_treino) e as previsões foram feitas sobre os dados de teste (y_pred). A acurácia é avaliada com o método score() que retorna o coeficiente de determinação 𝑅²

- ###### Classificador SGD (SGDClassifier)

O SGDClassifier é um modelo que utiliza o método de Gradiente Descendente Estocástico para otimização. É útil para problemas de classificação com grandes conjuntos de dados.
O modelo é treinado em mini-lotes (batch) de dados, onde a cada iteração ele atualiza os pesos de forma incremental. A acurácia é avaliada com accuracy_score.

- ###### Regressão Logística (LogisticRegression)

A Regressão Logística é um modelo de classificação que usa uma função logística para modelar a probabilidade de uma classe ou evento, como um rótulo binário (por exemplo, "sim" ou "não").
Uso no código: O modelo é treinado com X_treino e y_treino, e as previsões podem ser geradas com o método predict().

- ###### Árvore de Decisão (DecisionTreeRegressor)

Este modelo cria uma estrutura de árvore para prever valores, onde cada nó representa uma pergunta sobre uma feature, e as folhas representam a previsão final.
O modelo é treinado e avaliado da mesma forma que os anteriores, usando X_treino e y_treino.

- ###### Regressão Ridge (Ridge)

A Regressão Ridge é uma técnica de regularização que adiciona um termo de penalização à função de custo da regressão linear, ajudando a evitar overfitting.
O modelo é treinado com X_treino e y_treino, e a acurácia é avaliada usando score().

- ###### Random Forest (RandomForestRegressor)

O Random Forest é um modelo de ensemble que cria várias árvores de decisão durante o treinamento e combina suas previsões. Ele é robusto contra overfitting e fornece boas previsões em muitos cenários.
O modelo é treinado e avaliado da mesma forma que os anteriores.

- ###### Regressão Lasso (Lasso)

A Regressão Lasso também é uma técnica de regularização que penaliza a soma dos valores absolutos dos coeficientes. Ela pode zerar alguns coeficientes, o que ajuda na seleção de características.
O modelo é treinado e avaliado da mesma forma que os anteriores.

- ###### Gradient Boosting (GradientBoostingRegressor)

O Gradient Boosting é um modelo de ensemble que combina várias árvores de decisão de forma sequencial, onde cada nova árvore corrige os erros da árvore anterior. É um modelo muito eficaz para problemas de regressão e classificação.
O modelo é treinado com os dados de treino e avaliado com score() nos dados de teste.



##### Avaliação dos Modelos

- ###### Classificação

Objetivo:  Prever categorias discretas. É uma tarefa de aprendizado supervisionado, na qual o objetivo é prever uma categoria(rótulo discreto) para novas observações com base em dados de treinamento rotulados.

Saída:  Resultados em forma de rótulos (ex: "sim" ou "não"). Um exemplo comum é o reconhecimento de emails como "spam" ou "não spam".

###### Modelos de Machine Learning para Classificação:

- Regressão Logística
- Árvores de Decisão
- Support Vector Machines (SVM)
- Redes Neurais
- Random Forest

###### Métricas de Avaliação:

- Acurácia
- Precisão
- Recall
- F1 Score
- Matriz de Confusão

- ###### Regressão

Objetivo: Prever valores contínuos. É uma tarefa de aprendizado supervisionado, na qual o objetivo é prever um valor contínuo para novas observações com base em dados de treinamento rotulados.

Saída: Resultados em forma de números reais, um exemplo é prever o preço de uma casa com base em suas características (tamanho, localização, número de quartos).

###### Modelos Comuns:

- Regressão Linear
- Regressão Polinomial
- Árvores de Decisão para Regressão
- Random Forest para Regressão
- Gradient Boosting

###### Métricas de Avaliação:

- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- R² Score
- Root Mean Squared Error (RMSE)
- Resumo das Diferenças

##### Análise dos Resultados dos Modelos de Machine Learning


- **Árvore de Decisão**

MSE: 0.2212 (Baixo)
MAE: 0.3445 (Baixo)
R² Score: 0.6413 (Bom)
Teve um bom desempenho, com baixos valores de MSE e MAE e um R² razoavelmente alto. Ele pode captar padrões, mas pode ser superado por modelos mais robustos.

- **Regressão Linear**

MSE: 0.2212 (Igual ao modelo de árvore de decisão)
MAE: 0.3445 (Igual ao modelo de árvore de decisão)
R² Score: 0.6413 (Igual ao modelo de árvore de decisão)
Teve o mesmo desempenho que a árvore de decisão em todas as métricas. Isso sugere que ambas as abordagens estão captando os mesmos padrões, porém a simplicidade da regressão linear pode ser uma vantagem.

- **Gradient Boosting**

MSE: 0.2293 (Levemente maior)
MAE: 0.3663 (Levemente maior)
R² Score: 0.6282 (Levemente menor)
O modelo de Gradient Boosting tem métricas um pouco piores do que os modelos de árvore de decisão e regressão linear, mas ainda é competitivo. Isso sugere que, nesse conjunto de dados, o modelo pode não ter captado tantos padrões adicionais como esperado.

- **Random Forest**

MSE: 0.2184 (Melhor MSE)
MAE: 0.3436 (Melhor MAE)
R² Score: 0.6458 (Melhor R²)
Teve o melhor desempenho geral entre os modelos avaliados, com os menores valores de erro (MSE e MAE) e o maior valor de R². Ele consegue captar a complexidade dos dados com um bom nível de generalização.

- **Regressão Ridge**

MSE: 0.5043 (Alto)
MAE: 0.5426 (Alto)
R² Score: 0.1822 (Fraco)
Desempenho ruim, os erros são altos e o R² é muito baixo, sugerindo que o modelo não está captando bem os padrões dos dados.

- **Regressão Lasso**

MSE: 0.5248 (Maior)
MAE: 0.5612 (Maior)
R² Score: 0.1489 (Fraco)
O pior desempenho entre os modelos avaliados, com os maiores erros e o menor R². Ou seja, sse modelo não está captando bem a variabilidade dos dados.


**Melhor Modelo:** O Random Forest teve o melhor desempenho com os menores erros (MSE e MAE) e o maior R², se mostrando que o mais eficaz para o conjunto de dados.
**Piores Modelos:** Tanto a Regressão Ridge quanto a Regressão Lasso tiveram desempenhos fracos, sugerindo que elas não são adequadas para este problema.
**Modelos Satisfatórios:** Árvore de Decisão e Regressão Linear tiveram desempenhos praticamente iguais e razoavelmente bons, embora não tão eficazes quanto o Random Forest.


##### Conclusão

Por meio deste projeto, podemos experienciar como é uma situação real onde a análise e ciência de dados é essencial para a tomada de decisões. Vimos desde o início, que começa com o tratamento dos dados, sendo esta a fase mais extensa e importante, até o treinamento e avaliação dos modelos de Machine Learning.
