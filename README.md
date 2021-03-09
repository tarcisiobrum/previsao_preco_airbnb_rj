# previsao_preco_airbnb_rj
Análise exploratória de dados dataset Airbnb, clusterização de imóveis baseado em características físicas e previsão de preço aplicando técnicas de séries temporais.

a.	Como foi a definição da sua estratégia de modelagem?

Foram realizadas pesquisas prévias na literatura científica sobre estudos relacionados à previsão de preços de imóveis Airbnb ao redor do mundo. Posteriormente, definiu-se 2 tipos principais de abordagem para o problema: Predição de preço por atributos do imóvel (Exemplo em Tang (2015)) e por sentimentos/avaliação dos usuários (Exemplo em Kalehbast et. al (2019)).  Optou-se pela primeira abordagem a partir da análise dos atributos físicos e de localização do imóvel na cidade do Rio de Janeiro-RJ.
Foram utilizados dois datasets: Listings com a descrição dos imóveis e Calendar com datas de locação destes imóveis e, a partir de análise prévia dos dados disponíveis, adotou-se como estratégia modelar o problema a partir do agrupamento dos imóveis por determinados atributos, visto que existe influencia não somente do tipo de imóvel, mas também de sua localização e qualificações como quantidade de quartos, banheiros e acomodações, por exemplo. Como existem 4 tipos de imóvel, a proposta foi de analisar o preço a partir de uma quantidade maior de grupos de imóveis para verificar a relação com o preço. A partir da etapa de clusterização, foram implementados métodos de séries temporais em cada grupo (além do grupo de tipo de imóvel) para verificar a acurácia do racional proposto.

Kalehbasti, P. R., Nikolenko, L., & Rezaei, H. (2019). Airbnb price prediction using machine learning and sentiment analysis. arXiv preprint arXiv:1907.12665.

Tang, E., & Sangani, K. (2015). Neighborhood and price prediction for San Francisco Airbnb listings. Departments of Computer science, Psychology, economics–Stanford University.

b.	Como foi definida a função de custo utilizada?

Foi definida como métrica para avaliação dos modelos de previsão a medida de erro MAPE – Erro médio percentual absoluto por ser uma métrica clássica em séries temporais e de fácil interpretação e comparação com outros resultados e, além disso, a métrica contribui para penalizar diferenças grandes entre o previsto e o realizado, tendo em vista que valores do tipo outliers (apesar de presentes) são indesejados no resultado final e, resultados mesmo que com poucos erros grandes individuais penalizam o resultado do modelo, como um todo.

c.	Qual foi o critério utilizado na seleção do modelo final?
O critério principal é o erro MAPE, analisado em seu número absoluto e no comportamento individual de cada resposta do modelo. Pode ser observado que as medidas de erro MAPE foram baixas para os grupos de imóvel já disponibilizados nas bases de dados. O método de suavização simples foi o que apresentou o melhor resultado com MAPE de 0.01. Na clusterização foram obtidos os mesmos índices de erro MAPE porém, no total de erros, a clusterização se mostrou melhor com erros próximos a 0.1 em todos os métodos considerados enquanto no agrupamento por imóveis este erro ficou próximo de 0.4. A clusterização se mostra promissora para resultados de previsão de preços do Airbnb visto que há uma gama elevada de atributos do imóvel e do host que podem ser consideradas para aumentar a aproximação dos modelos à realidade do problema.
d.	Qual foi o critério utilizado para validação do modelo? Por que escolheu utilizar este método?

A validação do modelo foi pela comparação direta do erro MAPE entre a previsão realizada pelo agrupamento dos imóveis (conforme disponibilizado pelo dataset) a partir da aplicação na base considerada como “real” no problema. Em aplicações de previsão, é comum trabalhar com parte do dataset para treino e deixar uma outra parte para aplicação dos modelos (parte chamada de real).

e.	Quais evidências você possui de que seu modelo é suficientemente bom?
Assim como qualquer modelo, são tentativas de representar a realidade de algum fenômeno através da criação de algo que seja o mais próximo à realidade, que neste caso é a dinâmica de locação de imóveis via Airbnb no Rio de Janeiro-RJ. Existem suposições, simplificações e adaptações do problema que, as vezes, no mundo real isso não é possível de ser realizado e nada impede de um novo host precificar seu imóvel da forma que considerar justa e pertinente à sua realidade. Em linhas gerais, com tratamento estatístico e análise exploratória dos dados adequados, eliminando outliers (no nosso exemplo considerando preços abaixo de $2500) e analisando o comportamento e o relacionamento entre as diferentes variáveis do problema e detectando as principais que contribuem para o preço da locação bem como a utilização de técnicas cientificamente comprovadas (K-means, média móvel e suavização exponencial), pode-se dizer que são evidências de que o modelo combinado de séries temporais e clusterização retorna bons resultados dentro do conjunto de variáveis considerado, porém são necessários mais estudos (como análise de sentimentos, do próprio host, de mercado imobiliário na cidade, turismo e dentre outras...) para poder ter mais embasamento científico e mais evidências para construção do que podemos chamar de um bom modelo de previsão.
