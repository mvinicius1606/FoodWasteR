# FoodWasteR — Monitoramento e Prevenção de Desperdício Alimentar

FoodWasteR é um projeto de Engenhario e Analíse de Dados para coletar, processar e analisar dados de restaurantes com objetivo de identificar e prever desperdícios, quantificar prejuízos e gerar recomendações operacionais. Desenvolvido como aperfeiçoamento pessoal, sua arquitetura pode ser adotada profissionalmente em serviços de alimentação.

# 🧩 Necessidades do Projeto

O projeto FoodWasteR nasce com três necessidades principais:

- **Aperfeiçoamento pessoal:** Aplicar e consolidar conhecimentos avançados em banco de dados com R e fundamentos em engenharia de dados na AWS, incluindo criação de Data Lake, Data Marts, ETL e pipelines preditivos.
- **Sustentabilidade:** Contribuir para a redução do desperdício alimentar em restaurantes por meio de análise de dados e previsão de padrões de consumo, otimizando estoques e compras.
- **Eficiência financeira:** Gerar melhores decisões operacionais para restaurantes, minimizando custos e aumentando a rentabilidade através do uso inteligente de dados.

# 🎯 Objetivos do Projeto

O FoodWasteR tem como meta transformar dados em decisões estratégicas, unindo tecnologia e sustentabilidade:

- Construir um **Data Lake** que centralize e padronize informações de vendas, custos, clientes e desperdício.
- Desenvolver dois **Data Marts** (Vendas e Desperdício) para insights segmentados.
- Implementar uma pipeline de **Machine Learning** capaz de prever desperdícios e identificar padrões de comportamento.
- Documentar todo o processo com foco em boas práticas de Engenharia de Dados.

# 📄 Datasets e Engenharia de Dados

Para simular um cenário real de Big Data e garantir a complexidade necessária para o treino de Engenharia de Dados, foi criado um conjunto de dados sintético robusto utilizando a plataforma **Mockaroo** com auxílio de lógica avançada via IA.

Os dados simulam um mês completo de operação e apresentam desafios propositais de ingestão:
* **Heterogeneidade:** Cada tabela está em um formato diferente (**CSV**, **XLSX**, e **JSON**) para simular fontes desconexas.
* **Dados Sujos:** Foram inseridas inconsistências (datas em formatos mistos, nulos, tipagem incorreta) para prática intensiva de limpeza e tratamento (ETL).

As tabelas principais são:
1.  **ingredientes_restaurante.CSV,** com as colunas: data_estoque, id_ingredientes, peso_ingredientes, preço_ingredientes.
2.  **menu_restaurante.XLSX,** com as colunas: id_prato, prato, ingredientes, quantidade_ingredientes, peso_prato, preço_prato.
3.  **vendas_restaurante.JSON,** com as colunas: id_venda, data, cliente, id_prato, prato, vendas_cliente, desperdicio_cliente, ingrediente_desperdicado.

> 📚 **Documentação Completa:**
> Para ver a estrutura detalhada das tabelas, tipos de dados e a lógica de negócio aplicada, consulte o Dicionário de Dados em:
> 👉 **[`docs/data/DATA_DICTIONARY.md`](docs/data/DATA_DICTIONARY.md)**

# ⚙️ Infraestrutura e Arquitetura

O projeto foi estruturado utilizando uma abordagem de Data Lake na AWS, permitindo armazenar, catalogar e analisar grandes volumes de dados de forma escalável.

## Data Lake na AWS
Os dados gerados foram armazenados no **Amazon S3**. O **AWS Glue** foi utilizado para catalogar os metadados, tornando as tabelas acessíveis para consultas SQL. O **AWS Athena** foi empregado para consultas *ad-hoc* diretamente sobre os arquivos (Serverless), permitindo a exploração rápida dos dados brutos.

## ETL (Extract, Transform, Load)
Foi implementado um fluxo de ETL através do **AWS Glue Visual** para transformar os dados brutos em informações analíticas:
- **Extração:** Leitura dos arquivos heterogêneos (CSV, JSON, Parquet) no S3.
- **Transformação:** Padronização de formatos de data, limpeza de strings, tratamento de nulos e cálculo de métricas derivadas (custo do desperdício e perda financeira).
- **Carga:** Escrita dos dados transformados e limpos novamente no S3, prontos para consumo.

## Data Marts em R
Com os dados transformados, foram criados dois Data Marts específicos utilizando R:
- **Data Mart de Desperdício:** Concentra informações sobre ingredientes, pratos e percentual/peso de desperdício por cliente, permitindo análises de eficiência.
- **Data Mart de Vendas:** Centraliza dados de receita, ticket médio e frequência, permitindo analisar o desempenho financeiro.

# 📉 Análises de Dados em R

As análises foram realizadas em R a partir dos Data Marts criados.
- **Desperdício:** Foram exploradas métricas como quantidade total desperdiçada, perda financeira por prato e identificação de clientes com maior índice de sobras.
- **Vendas:** Foram calculados indicadores como ticket médio, variação de vendas ao longo do mês e estatísticas descritivas.

Para ambos os cenários, foram desenvolvidos dashboards interativos utilizando **R Shiny**, permitindo visualização dinâmica dos padrões de consumo e desperdício.

# Autor
Marcos Vinicius Vieira dos Santos Assis

RIO DE JANEIRO 2025
