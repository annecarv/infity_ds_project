# infity_ds_project

Análise de Dados - Walmart

Introdução:
Este código foi desenvolvido para realizar a análise de um conjunto de dados de compras do Walmart, focando no comportamento de compra dos clientes com base em diferentes atributos, como gênero, categoria de produto, cidade, estado civil, e faixa etária. O objetivo principal é gerar insights e visualizar as tendências desses dados de maneira eficiente.

Bibliotecas Utilizadas:

pandas 
matplotlib 
numpy 

1. Distribuição dos Clientes
O código agrupa os dados por estado civil, cidade e gênero, fornecendo insights sobre a distribuição de clientes e suas compras. Gráficos de barras são utilizados para destacar as porcentagens de compras por essas categorias.

2. Percentual de Compras por Gênero
Há uma análise dedicada ao percentual de compras realizadas por clientes de diferentes gêneros (masculino e feminino). Isso é representado por meio de gráficos de barras, onde as cores e percentuais tornam os dados facilmente interpretáveis.

3. Identificação de Outliers
Outliers no valor das compras são identificados usando a técnica do intervalo interquartil (IQR). Isso é importante para garantir que valores atípicos não afetem a análise principal.

4. Análise por Faixa Etária
A mediana de compras é calculada e visualizada por faixa etária, mostrando como o valor de compra tende a variar com a idade.

Conclusão
Este código realiza uma análise detalhada do comportamento de compras de clientes com base em atributos demográficos e categorias de produtos. Com o uso de pandas para manipulação de dados e matplotlib para visualização, os insights são apresentados de forma clara e visualmente atraente. Técnicas como detecção de outliers garantem que a análise seja precisa, e o uso de gráficos permite uma melhor compreensão das tendências gerais no comportamento de compra dos clientes.

Pontos Fortes:
O uso extensivo de agregações permite insights ricos a partir dos dados.
Gráficos claros e bem definidos tornam as análises acessíveis.
A detecção de outliers melhora a precisão das análises estatísticas.


User_ID: Identificação do usuário.
Product_ID: Identificação do produto.
Gender: Gênero do usuário (F para feminino, M para masculino).
Age: Faixa etária do usuário.
Occupation: Ocupação do usuário representada por um código numérico.
City_Category: Categoria da cidade (A, B, ou C).
Stay_In_Current_City_Years: Quantos anos o usuário está na cidade atual (representado como 1, 2, 3, ou 4+).
Marital_Status: Estado civil (0 para solteiro, 1 para casado).
Product_Category: Categoria do produto.
Purchase: Valor da compra.

1. Preparação dos Dados
Tratar dados categóricos: Colunas como Gender, Age, City_Category, e Stay_In_Current_City_Years precisam ser transformadas em um formato que o modelo consiga entender (normalmente numérico).
Preenchimento de valores nulos: Verifique se há valores faltantes e trate-os adequadamente (substituindo por uma média, mediana ou uma categoria "desconhecida").
Feature scaling: A normalização ou padronização dos dados pode ser útil dependendo do algoritmo escolhido.
2. Divisão do Dataset
Divida os dados em conjuntos de treino e teste (normalmente uma proporção de 70-80% para treino e 20-30% para teste).
3. Seleção do Modelo
Escolha um algoritmo de regressão apropriado para prever valores contínuos (como o preço da compra):

Regressão Linear
Random Forest Regressor
Gradient Boosting Machines (como XGBoost)
LightGBM
4. Treinamento do Modelo
Treine o modelo usando o conjunto de treino.
5. Avaliação
Avalie o desempenho do modelo no conjunto de teste usando métricas como MAE (Mean Absolute Error), MSE (Mean Squared Error), ou RMSE (Root Mean Squared Error).
6. Otimização
Tente ajustar os hiperparâmetros do modelo (usando GridSearch ou RandomSearch) para melhorar o desempenho.
Vou ajudar com a preparação dos dados e a construção do modelo. Vamos começar criando variáveis dummies para os dados categóricos e depois preparar os dados para treinar um modelo.

Primeiro, verificarei se há valores nulos e depois criarei as variáveis dummies.

Os dados foram codificados com variáveis dummies para colunas categóricas, e não há valores nulos no DataFrame.

Agora, podemos separar as variáveis independentes (features) e a variável dependente (target, que será a coluna Purchase). Em seguida, dividiremos o conjunto de dados em treino e teste, e treinaremos um modelo de regressão, como o Random Forest Regressor.

Vou preparar os dados e treinar o modelo. ​