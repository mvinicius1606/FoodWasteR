# Etapas do Projeto (Cronograma de 4 a 6 Semanas)

## 🗂️ Semana 1 – Planejamento e Coleta de Dados

Objetivo: Definir a base do projeto e iniciar o Data Lake.
- Estruturar o repositório no GitHub (pastas, README, versionamento).
- Mapear fontes de dados relevantes (APIs públicas e datasets sobre restaurantes, consumo e desperdício).

 - Conectar e coletar dados via R (httr, jsonlite, tidyverse).

- Armazenar dados brutos no Data Lake local (formato CSV/Parquet).

- Criar documentação inicial sobre o fluxo de coleta.

📘 Resultado esperado: primeiros datasets organizados e centralizados em um ambiente de Data Lake.

## 🧮 Semana 2 – Tratamento e Modelagem de Dados

Objetivo: Limpar, padronizar e preparar dados para os Data Marts.

- Tratar valores nulos, duplicados e inconsistências com dplyr e tidyr.

- Normalizar unidades e padronizar colunas (ex: datas, categorias de produtos).

- Implementar lógica de extração de métricas úteis (ex: desperdício diário, ticket médio).

- Criar tabelas derivadas para Data Mart de Vendas e Data Mart de Desperdício.

- Salvar dados transformados em formato pronto para análise (CSV/SQLite).

📘 Resultado esperado: dados limpos e prontos para uso analítico.

## 🤖 Semana 3 – Desenvolvimento do Modelo Preditivo

Objetivo: Criar pipeline de machine learning integrada ao fluxo de dados.

- Definir variáveis preditoras e alvo (ex: volume de desperdício, probabilidade de sobra).

- Separar dados em treino/teste com caret ou tidymodels.

- Implementar um modelo simples (ex: regressão linear ou árvore de decisão).

 - Automatizar a atualização de previsões com scripts R.

 - Criar métricas de avaliação (MAE, RMSE, acurácia).

📘 Resultado esperado: pipeline inicial funcional com previsões básicas.

## 📊 Semana 4 – Visualização, Documentação e Ajustes

Objetivo: Consolidar resultados e preparar o projeto para apresentação.

- Criar dashboards analíticos simples com ggplot2 e shiny (opcional).

- Documentar todas as etapas (README e relatórios em Markdown).

- Revisar estrutura do repositório e boas práticas de código.

- Ajustar parâmetros do modelo e preparar sugestões de melhoria futura.

📘 Resultado esperado: versão funcional e documentada do projeto.

##🕐 Extensão opcional (Semanas 5 e 6)

Se houver mais tempo, o foco pode ser:

- Refinar a pipeline para atualização automática (ex: CRON jobs ou APIs em tempo real).

- Testar outros algoritmos de ML (Random Forest, Gradient Boosting).

Melhorar o front-end de visualização com Shiny Dashboard ou Flexdashboard.

Integrar armazenamento em banco de dados SQL e modularizar o código.
