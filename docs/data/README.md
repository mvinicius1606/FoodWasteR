# 🗂️ Documentação dos Dados Usados

Este branch armazena os datasets brutos gerados para o projeto de análise de desperdício alimentar e gestão financeira de restaurante. O foco deste conjunto de dados é simular um ambiente de Data Lake heterogêneo, exigindo etapas robustas de ETL.

## 🛠️ Metodologia e Fonte dos Dados

Para garantir a aplicação prática em cenários de Engenharia de Dados, os dados foram gerados sinteticamente utilizando a plataforma **Mockaroo**.
- **Volume:** Aproximadamente 1.000 registros por tabela.
- **Período:** Simulação de um mês completo de operação.
- **Relacionamento:** As tabelas possuem chaves lógicas que se correlacionam, permitindo a execução de `JOINs` complexos.

## 💾 Formatos de Arquivos (Desafio de Ingestão)

Para simular um ambiente real de Big Data onde as fontes são diversas, **cada tabela foi disponibilizada em um formato de arquivo diferente**. Isso exige que o pipeline de ingestão seja capaz de ler e padronizar diferentes estruturas:

1. **Ingredientes** $\rightarrow$ Arquivo `.csv` (Comma Separated Values)
2. **Menu** $\rightarrow$ Arquivo `.json` (JavaScript Object Notation)
3. **Vendas** $\rightarrow$ Arquivo `.parquet` (Armazenamento colunar otimizado)

---

## 📊 Estrutura das Tabelas

Abaixo estão detalhadas as colunas e o propósito de cada dataset.

### 1. Tabela: `ingredientes_restaurante`
*Permite acompanhar os custos e a quantidade de cada insumo.*

| Coluna | Descrição |
| :--- | :--- |
| **data** | Data de compra ou registro do estoque. |
| **id_ingredientes** | Identificador único do ingrediente. |
| **ingredientes** | Nome do item (ex: Tomate, Arroz). |
| **quantidade_ingredientes** | Quantidade adquirida/disponível. |
| **preço_ingredientes** | Custo do ingrediente. |

### 2. Tabela: `menu_restaurante`
*Relaciona os pratos aos ingredientes e seus pesos, possibilitando o cálculo de custo e desperdício por prato.*

| Coluna | Descrição |
| :--- | :--- |
| **id_prato** | Identificador único do prato. |
| **prato** | Nome do prato servido. |
| **ingrediente** | Ingrediente que compõe o prato. |
| **peso_prato** | Peso total ou do componente no prato. |

### 3. Tabela: `vendas_restaurante`
*Registra as vendas, estimando o desperdício e a perda financeira.*

| Coluna | Descrição |
| :--- | :--- |
| **data** | Data e hora da venda. |
| **cliente** | Identificação do cliente. |
| **prato** | Prato vendido (Chave estrangeira). |
| **vendas_cliente** | Valor pago pelo cliente. |
| **desperdicio_cliente** | Quantidade de sobra deixada pelo cliente. |

---

## ⚠️ Dados Sujos e Tratamento (ETL)

Para fins educacionais, **foram introduzidos propositalmente "dados sujos"** nestas tabelas. O objetivo é praticar a limpeza e padronização (Data Cleaning) antes da análise.

Ao manipular os dados, você encontrará os seguintes desafios:

* **Formatos de Data Inconsistentes:** Em uma mesma coluna de data, podem existir formatos diferentes (ex: `DD/MM/AAAA` misturado com `AAAA-MM-DD` ou `MM-DD-AAAA`).
* **Valores Nulos (Null/NaN):** Colunas essenciais contêm valores vazios que precisarão de tratamento (imputação pela média, remoção ou preenchimento com zero).
* **Tipagem Incorreta:** Campos numéricos que podem estar sendo lidos como texto devido a caracteres especiais.

## 🎯 Objetivos de Análise

Após o tratamento, estes dados servem como base para:
1.  Criação de **Data Lake no AWS** e **dois Data Marts: Um de desperdícios e outro de vendas**.
2.  Análises em R para gerar relatóriois.
3.  Transformação dos dados adquiridos nas analises em tomada de decisão usando ferramentas de BI.
