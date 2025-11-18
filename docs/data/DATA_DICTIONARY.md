# 🗂️ Documentação dos Dados (Data Branch)

Este branch armazena os datasets brutos gerados para o projeto de análise de desperdício alimentar e gestão financeira de restaurante. O foco deste conjunto de dados é simular um ambiente de Data Lake heterogêneo, exigindo etapas robustas de ETL para transformar dados brutos em inteligência de negócio.

## 🔄 Como Reproduzir (Mockaroo)

Os scripts (JSON Schemas) utilizados para configurar a lógica de geração de cada tabela estão armazenados neste repositório, no diretório:
> **`docs/data/mockaroo/`**

Caso queira gerar novos dados ou alterar as regras de negócio, siga este passo a passo:

1.  Acesse o arquivo desejado na pasta `docs/data/mockaroo` e copie todo o conteúdo JSON.
2.  Vá para o site [Mockaroo](https://mockaroo.com/).
3.  Clique no botão **"Import Fields"** (localizado acima da lista de campos).
4.  Cole o código JSON e clique em **Import**.
5.  Configure o número de linhas (**# Rows**) e o formato (**Format**) conforme a tabela de especificações abaixo (Seção "Estrutura das Tabelas").
6.  Clique em **Download Data**.

## 🤖 Processo de Criação e Metodologia

Para garantir a aplicação prática em cenários complexos de Engenharia de Dados, os dados foram gerados sinteticamente utilizando a plataforma **Mockaroo**, com o auxílio do **Google Gemini** para o desenvolvimento de scripts lógicos avançados (Ruby/JSON schemas).

O objetivo não foi apenas criar dados aleatórios, mas sim simular um **ecossistema relacional coerente**:

1.  **Consultoria com Gemini:** A IA foi utilizada para criar a lógica de negócio (ex: garantir que o desperdício nunca seja maior que o peso do prato, ou que o preço da Picanha seja consistentemente maior que o do Frango).
2.  **Cadeia de Valor:** As tabelas foram desenhadas para representar o fluxo real de um restaurante:
    * *Compra (Ingredientes)* $\rightarrow$ *Transformação (Menu)* $\rightarrow$ *Venda e Sobra (Vendas)*.
3.  **Volume e Tempo:**
    * **Volume:** Aproximadamente 1.000 registros transacionais.
    * **Período:** Simulação de um mês completo de operação (Novembro/2024).

---

## 💾 Desafio de Ingestão (Formatos Heterogêneos)

Para simular um ambiente real de Big Data onde as fontes de dados são diversas e desconexas, **cada tabela foi gerada propositalmente em um formato diferente**. Isso exige que o pipeline de ingestão seja capaz de ler, tratar e padronizar diferentes estruturas:

1.  **Ingredientes** $\rightarrow$ Arquivo `.CSV` (Comma Separated Values)
2.  **Menu** $\rightarrow$ Arquivo `.XLSX` (Excel)
3.  **Vendas** $\rightarrow$ Arquivo `.JOSN` (JavaScript Object Notation - Estrutura Hierárquica)

---

## 📊 Estrutura e Racional das Tabelas

Abaixo estão detalhados o propósito de criação de cada dataset, suas colunas e a lógica aplicada.

### 1. Tabela: `ingredientes_restaurante` (Estoque/Custos)
**Motivo da Criação:** Simular a entrada de insumos no atacado. Sem esta tabela, não seria possível calcular a margem de lucro real nem controlar o estoque.
**Lógica Aplicada:** Os dados representam compras de grande volume (ex: sacas de 50kg de arroz) em datas aleatórias ao longo do mês, permitindo análise de flutuação de preço de custo.

| Coluna | Descrição |
| :--- | :--- |
| **data_estoque** | Data da compra/reabastecimento do insumo. |
| **id_ingredientes** | Identificador único do ingrediente (Chave Primária). |
| **ingredientes** | Nome do item (ex: Tomate, Arroz, Filé Mignon). |
| **quantidade_ingredientes** | Volume adquirido (em Kg) para estoque. |
| **preço_ingredientes** | Custo total da nota fiscal de compra. |

### 2. Tabela: `menu_restaurante` (Ficha Técnica)
**Motivo da Criação:** Servir como a "receita" do sistema. Esta tabela conecta o ingrediente bruto ao prato vendido.
**Lógica Aplicada:** Utiliza uma relação de **1:N** (um prato é composto por vários ingredientes). Aqui definimos pesos e preços fixos para garantir que o sistema saiba que uma "Feijoada" sempre consome "Feijão" e "Bacon".

| Coluna | Descrição |
| :--- | :--- |
| **id_prato** | Identificador único do prato. |
| **prato** | Nome comercial do prato servido. |
| **ingrediente** | Ingrediente componente (Chave Estrangeira para a tabela 1). |
| **quantidade_ingrediente** | Quanto de cada ingrediente vai no prato (ex: 0.200kg). |
| **peso_prato** | Peso total do prato servido ao cliente. |
| **preço_prato** | Preço de venda no cardápio. |

### 3. Tabela: `vendas_restaurante` (Tabela Fato)
**Motivo da Criação:** Registrar a transação financeira e o comportamento do consumidor. É aqui que cruzamos o lucro com o desperdício.
**Lógica Aplicada:** Simula clientes recorrentes e calcula o desperdício de forma lógica (o cliente nunca desperdiça mais do que o peso total do prato). Inclui também qual ingrediente específico foi desperdiçado para análises granulares.

| Coluna | Descrição |
| :--- | :--- |
| **id_venda** | Identificador único da transação. |
| **data** | Data e hora da venda. |
| **cliente** | Nome do cliente (permite análise de recorrência). |
| **id_prato** | Chave de ligação com o Menu. |
| **prato** | Nome do prato vendido. |
| **vendas_cliente** | Valor monetário pago (Receita). |
| **desperdicio_cliente** | Quantidade de sobra deixada no prato (Perda física). |
| **ingrediente_desperdicado** | Qual item o cliente deixou no prato (ex: deixou só a 'Cebola'). |

---

## ⚠️ Dados Sujos e Tratamento (ETL Challenge)

Para fins educacionais, **foram introduzidos propositalmente "dados sujos" e inconsistências** nestas tabelas através dos scripts do Mockaroo.

O objetivo é praticar técnicas de **Data Cleaning e Data Quality**. Ao manipular os dados, você encontrará:

* **Inconsistência Temporal:** Colunas de data misturando formatos (`DD/MM/AAAA`, `AAAA-MM-DD` e `DD-MM-AAAA`).
* **Valores Nulos (Null/NaN):** Campos obrigatórios vazios que exigirão estratégias de inputação ou remoção.
* **Tipagem Mista:** Campos numéricos (como peso e preço) contaminados com texto (ex: `50kg`, `R$ 120,00`) exigindo limpeza de strings e conversão de tipos (Casting).

## 🎯 Objetivos de Análise

Após o tratamento (ETL), estes dados formam a base para:
1.  **Engenharia de Dados:** Construção de Data Lake e Data Marts organizados.
2.  **Gestão Financeira:** Análise de Lucro Líquido (Preço de Venda - Custo dos Ingredientes - Custo do Desperdício).
3.  **Sustentabilidade:** Dashboards de BI monitorando o volume de comida jogada fora e quais ingredientes são os maiores vilões do desperdício.
