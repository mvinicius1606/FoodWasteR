# FoodWasteR — Monitoramento e Prevenção de Desperdício Alimentar
FoodWasteR é um projeto em R para coletar, processar e analisar dados de restaurantes com objetivo de identificar e prever desperdícios, mostrando os prejuízo e gerar recomendações operacionais. Desenvolvido como aperfeiçoamento pessoal, pode ser adotado profissionalmente em restaurantes e serviços de alimentação.

# 🧩 Necessidades do Projeto

O projeto FoodWasteR nasce com três necessidades principais:

- Aperfeiçoamento pessoal — aplicar e consolidar conhecimentos avançados em banco de dados com R e fundamentos em engenharia de dados na AWS, incluindo criação de Data Lake e Data Marts, ETL, e implementação de pipelines analíticos e preditivos.

- Sustentabilidade — contribuir para a redução do desperdício alimentar em restaurantes, por meio de análise de dados e previsão de padrões de consumo, otimizando estoques e compras.

- Eficiência financeira — gerar melhores decisões operacionais e financeiras para restaurantes, minimizando custos e aumentando a rentabilidade através do uso inteligente de dados.

# 🎯 Objetivos do Projeto

O FoodWasteR tem como meta transformar dados em decisões estratégicas, unindo tecnologia e sustentabilidade. Entre seus principais objetivos estão:

- Construir um Data Lake que centralize e padronize informações de vendas, preço de custo, clientes e desperdício obtidas por meio de tabelas feitas te cunho proprio atarvés da plataforma Mockaroo.

- Desenvolver dois Data Marts — um voltado para análise de vendas e outro para controle de desperdício, permitindo insights claros e segmentados.

- Implementar uma pipeline de Machine Learning capaz de prever desperdícios e identificar padrões de comportamento de clientes, ajudando na tomada de decisão.

- Documentar e estruturar todo o processo com foco em boas práticas de engenharia de dados e aprendizado contínuo.

- Demonstrar aplicabilidade prática, servindo tanto como projeto de aperfeiçoamento pessoal quanto como modelo profissional reutilizável para o setor de alimentação.

# 📄 Datasets 

Para aplicar melhor o objetivo do projeto foi utilizado a plataforma Mockaroo parra criar dados ficticios mas realistas em 3 tabelas com cerca de 1000 linhas que se correlacionam entre si, que são as: 
- **Tabela 1:** ingredientes_restaurante, com as colunas data, id_ingredientes, ingredientes, quantidade_ingredientes, preço_ingredientes. Permitindo acompanhar os custos e a quantidade de cada insumo.
- **Tabela 2:** menu_restaurante, com as colunas id_prato, prato, ingrediente, peso_prato. Relacionando os pratos aos ingredientes e seus pesos, possibilitando o cálculo de custo e desperdício por prato.
- **Tabela 2:** vendas_restaurante, com as colunas data, cliente, prato, vendas_cliente, desperdicio_cliente. Registrando as vendas e estimando o desperdício e a perda financeira.

As tabelas são interligadas para permitir análises consistentes sobre o impacto do desperdício, o custo dos ingredientes e a rentabilidade de cada prato. Os dados simulam um mês completo de operação do restaurante e podem ser utilizados em Data Lake, Data Marts, análises SQL e visualizações em ferramentas de BI, servindo como base para estudos de gestão de desperdício alimentar e controle financeiro. Ademais, as tabelas tem propositalmente alguns dados sujos para praticar ETL.

# ⚙️ Infraestrutura e Arquitetura

O projeto foi estruturado utilizando uma abordagem de Data Lake na AWS, permitindo armazenar, catalogar e analisar grandes volumes de dados de forma escalável e organizada.

## Data Lake na AWS

Os dados gerados no Mockaroo foram armazenados no Amazon S3 em um bucket. Para facilitar a análise, foi utilizado o AWS Glue, que realiza o catálogo de dados, registrando as tabelas e seus metadados, tornando-as acessíveis para consultas SQL. O AWS Athena foi empregado para consultas ad-hoc diretamente sobre os arquivos no S3, permitindo a exploração dos dados sem necessidade de carregamento adicional em bancos de dados tradicionais.

## ETL

Foi implementado um fluxo de ETL (Extract, Transform, Load) através do AWS Glue Visual, para transformar os dados brutos em informações analíticas. O processo incluiu:

- Extração: leitura dos arquivos CSV gerados no Mockaroo no S3.

- Transformação: padronização de formatos, cálculo de métricas derivadas como peso total de pratos, custo do desperdício e perda financeira.

- Carga: escrita dos dados transformados novamente em S3, já estruturados para consultas analíticas e criação de Data Marts.

## Data Marts em R

Com os dados transformados, foram criados dois Data Marts específicos utilizando R:

- Data Mart de Desperdício: concentra informações sobre ingredientes, pratos e percentual/peso de desperdício por cliente e por prato, permitindo análises de eficiência e custo.

- Data Mart de Vendas: centraliza dados de vendas por cliente, prato, valor e receita total, permitindo analisar o desempenho financeiro e identificar padrões de consumo.

Essa arquitetura permite a integração entre armazenamento escalável, processamento de dados e análise em R, fornecendo uma base completa para estudos de desperdício alimentar, otimização de custos e inteligência de negócios no setor de restaurantes.

# 📉 Análises de Dados em R 

As análises foram realizadas em R a partir dos dois Data Marts criados. No Data Mart de Desperdício, foram exploradas métricas como quantidade total de desperdício, perda financeira por prato e por cliente, além de estatísticas descritivas como média, mediana e moda. Também foram identificados os clientes que geraram mais desperdício, permitindo insights sobre eficiência operacional. No Data Mart de Vendas, foram calculados indicadores como ticket médio por cliente, variação de vendas ao longo do mês e estatísticas descritivas gerais para apoiar decisões estratégicas. Para ambos os Data Marts, foram desenvolvidos dashboards interativos utilizando R Shiny e ferramentas de BI, permitindo visualização dinâmica e análise detalhada dos padrões de consumo e desperdício do restaurante.


