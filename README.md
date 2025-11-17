# FoodWasteR — Monitoramento e Prevenção de Desperdício Alimentar
FoodWasteR é um projeto em R para coletar, processar e analisar dados de restaurantes com objetivo de identificar e prever desperdícios (ingredientes, dias, clientes) e gerar recomendações operacionais. Desenvolvido como aperfeiçoamento pessoal, pode ser adotado profissionalmente em restaurantes e serviços de alimentação.

# 🧩 Necessidades do Projeto

O projeto FoodWasteR nasce com três necessidades principais:

- Aperfeiçoamento pessoal — aplicar e consolidar conhecimentos avançados em banco de dados com R e fundamentos em engenharia de dados na AWS, incluindo criação de Data Lake e Data Marts, ETL, e implementação de pipelines analíticos e preditivos.

- Sustentabilidade — contribuir para a redução do desperdício alimentar em restaurantes, por meio de análise de dados e previsão de padrões de consumo, otimizando estoques e compras.

- Eficiência financeira — gerar melhores decisões operacionais e financeiras para restaurantes, minimizando custos e aumentando a rentabilidade através do uso inteligente de dados.

# 🎯 Objetivos do Projeto

O FoodWasteR tem como meta transformar dados em decisões estratégicas, unindo tecnologia e sustentabilidade. Entre seus principais objetivos estão:

- Construir um Data Lake que centralize e padronize informações de vendas, estoque e consumo obtidas por mmeio de datasets públicos.

- Desenvolver dois Data Marts — um voltado para análise de vendas e outro para controle de desperdício, permitindo insights claros e segmentados.

- Implementar uma pipeline de Machine Learning capaz de prever desperdícios e identificar padrões de comportamento de clientes, ajudando na tomada de decisão.

- Documentar e estruturar todo o processo com foco em boas práticas de engenharia de dados e aprendizado contínuo.

- Demonstrar aplicabilidade prática, servindo tanto como projeto de aperfeiçoamento pessoal quanto como modelo profissional reutilizável para o setor de alimentação.

# 📄 Datasets 

Como datasets base dos dados, foi utilizado dois datasets públicos do Kaggle: 
- [food_wastage_data.csv](https://www.kaggle.com/datasets/trevinhannibal/food-wastage-data-in-restaurant)
- [9.Sales-Data-Analysis.csv](https://www.kaggle.com/datasets/rohitgrewal/restaurant-sales-data)
- Também foi utilizado um dataset como refência para consultas: [Food Waste Dataset in U.S. 2018](https://www.kaggle.com/datasets/aritra100/food-waste-dataset-in-u-s-2018)

# Tabela de Referência

Devido a ausência de datasets especificos para o objetivo do projeto foi necessário uma tabela de referência, criada para agrupar campos semelhantes das duas tabelas bases e adicionar atributos necessários para transformar quantidade desperdiçada em custo. Para facilitar o processo de criação irei utilizar um recurso de machine learning do R, o Random Florest. Com isso, essa fase do projeto será dividia em:
- **Etapa 1:** Preparação dos dados base, criando uma nova coluna "food_category" para relacionar as colunas "type_of_food" da tabela food_wastage_data e a coluna "product" da tabela Sales-Data-Analysis.
- **Etapa 2:** Inserção manualmente de 100-200 linhas para usar como base de treino do Random Florest
- **Etapa 3:** Transformar os textos (strings) em valores numericos usando a vetorização (TF-IDF) para o funcionamneto do machine learning.
- **Etapa 4:** Implemtação, treino e validação do Random Florest.



