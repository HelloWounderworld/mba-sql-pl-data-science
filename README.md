# 🗃️ SQL e PL/SQL para Ciência de Dados

Este guia resume os principais conceitos e habilidades em **SQL (Structured Query Language)** e **PL/SQL (Procedural Language/SQL)** que são fundamentais para aplicações em **Ciência de Dados**, **Engenharia de Dados** e **Análise de Negócios**.

---

## 🎯 Objetivo

Capacitar profissionais e estudantes da área de dados a:

- Manipular, transformar e consultar dados com eficiência usando SQL
- Criar procedimentos automatizados com PL/SQL
- Integrar dados relacionais ao pipeline analítico e modelos de machine learning

---

## 📚 Tópicos Fundamentais de SQL

### 1. 🔍 Consultas Básicas

- `SELECT`, `FROM`, `WHERE`
- Filtros com operadores: `=`, `>`, `<`, `BETWEEN`, `IN`, `LIKE`
- Ordenação: `ORDER BY`
- Eliminação de duplicatas: `DISTINCT`
- Alias para colunas e tabelas: `AS`

### 2. 🧮 Funções e Agregações

- Funções de agregação: `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`
- Agrupamento de dados: `GROUP BY`
- Filtragem de agregações: `HAVING`
- Funções de data e string: `NOW()`, `SUBSTRING`, `CONCAT`, `UPPER`, `LOWER`

### 3. 🔗 JOINs e Relacionamentos

- Relações entre múltiplas tabelas:
  - `INNER JOIN`
  - `LEFT JOIN`
  - `RIGHT JOIN`
  - `FULL OUTER JOIN`
- Autojoins e subqueries correlacionadas

### 4. 📐 Subqueries e CTEs

- Subconsultas `IN`, `EXISTS`, `= (SELECT...)`
- Common Table Expressions (CTEs) com `WITH`
- Subqueries em `SELECT`, `FROM`, `WHERE`

### 5. 🎯 Filtros Avançados

- `CASE WHEN` para lógica condicional
- Expressões regulares: `REGEXP`
- Operações com `NULL` (`IS NULL`, `COALESCE`, `IFNULL`)

---

## 🧱 Tópicos de Manipulação de Dados

### 6. ✍️ DML – Data Manipulation Language

- Inserção: `INSERT INTO`
- Atualização: `UPDATE`
- Remoção: `DELETE`

### 7. 🛠️ DDL – Data Definition Language

- Criação de estruturas:
  - `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`
- Tipos de dados: `INT`, `VARCHAR`, `DATE`, `BOOLEAN`, `FLOAT`
- Restrições: `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `NOT NULL`

---

## 🧮 PL/SQL – Programação Procedural

> Muito utilizado em Oracle, mas o conceito se aplica a outros bancos com extensões procedurais como T-SQL (SQL Server) e PL/pgSQL (PostgreSQL).

### 8. 🔁 Estruturas de Controle

- `IF...THEN...ELSE`
- Loops: `FOR`, `WHILE`, `LOOP...EXIT`
- Exceções: `EXCEPTION WHEN`

### 9. 🧩 Blocos Programáveis

- Blocos anônimos `DECLARE ... BEGIN ... END`
- Variáveis e tipos
- Cursores (cursors)
- Funções e procedimentos (`CREATE FUNCTION`, `CREATE PROCEDURE`)

### 10. ⚙️ Triggers

- Disparadores automáticos em eventos: `BEFORE INSERT`, `AFTER UPDATE` etc.
- Muito úteis para auditoria, validações e automações

---

## 📊 SQL para Ciência de Dados

### 11. 📈 Casos de Uso Reais

- Extração de datasets limpos para análise
- Agregações e KPIs gerados diretamente via SQL
- Criação de tabelas temporárias para alimentar modelos
- Pré-processamento e feature engineering com SQL
- Monitoramento de dados e auditoria via queries programadas

### 12. 🧠 Integrações com Python e R

- Uso de bibliotecas como:
  - `pandas.read_sql()` (Python)
  - `DBI` e `dplyr` (R)
- Conexões com bancos PostgreSQL, Oracle, MySQL, SQL Server
- Queries como parte de pipelines com Airflow, dbt, etc.

---

## 🧪 Boas Práticas

- Nomear colunas e tabelas de forma clara e consistente
- Utilizar `LIMIT` durante testes para evitar uso excessivo de recursos
- Documentar queries complexas com comentários `--`
- Indexação para melhorar performance
- Separar lógica de negócio em views e procedures reutilizáveis

---

## 🧰 Ferramentas Recomendadas

- **SGBDs**: PostgreSQL, MySQL, Oracle, SQL Server, SQLite
- **Interfaces gráficas**: DBeaver, pgAdmin, SQL Developer, DataGrip
- **Ambientes integrados**: Jupyter, VS Code, Apache Superset, Metabase

---

## 📘 Referências e Leitura Complementar

- *SQL for Data Science* – Antonio Badia
- *Oracle PL/SQL Programming* – Steven Feuerstein

---

## ✅ Conclusão

O domínio de SQL e PL/SQL permite que cientistas de dados:

- Trabalhem de forma mais próxima e eficiente com engenheiros de dados
- Transformem grandes volumes de dados diretamente na camada do banco
- Automatizem e escalem a preparação de dados para modelos analíticos
