# Seção 03: LANGUAGE STATEMENTS:
Realizar as leituras dos links e ir colocandos os pontos importantes nas minhas notas e realizar testes!

## Aula 01 - INTRODUÇÃO LANGUAGE STATEMENTS:
### Sintaxe SQL
Seguir link de leitura

    https://www.javatpoint.com/sql-syntax

Bom, antes mesmo de começarmos a ir criando as tabelas de curso, etc... Vamos entender direito as sintaxes.

A sintaxe da linguagem de consulta estruturada é um conjunto exclusivo de regras e diretrizes, que não diferencia maiúsculas de minúsculas. Sua sintaxe é definida e mantida pelos padrões ISO e ANSI.

Ciente do case-insensitive do SQL, aqui está um tópido de boas práticas quando for codar com essa linguagem de consulta:

- Você pode escrever as palavras-chave SQL em maiúsculas e minúsculas, mas escrever as palavras-chave SQL em maiúsculas melhora a legibilidade da consulta SQL.

- As instruções SQL ou a sintaxe dependem das linhas de texto. Podemos colocar uma única instrução SQL em uma ou várias linhas de texto.

- Você pode executar a maior parte da ação em um banco de dados com instruções SQL.

- A sintaxe SQL depende da álgebra relacional e do cálculo relacional de tupla.

### Language Statement
Bom, vimos, até agora, que o SQL ele tem inúmeros tipos de comandos, donde foi apresentados as mais usuais. Porém, ficaria mais fácil entender ao todo a estrutura do SQL se organizados elas nas seguintes categorias, que é o tema foco dessa seção:

- DDL - Linguagem de Definição de Dados

- DQL - linguagem de consulta de dados

- DML – Linguagem de Manipulação de Dados

- DCL - Linguagem de Controle de Dados

- TCL – Linguagem de Controle de Transação

Iremos abordar uma por uma essas categorias para vc conseguir ter uma visão bem geral da arquitetura do conceito dessa linguagem de consulta.

## Aula 02 - DML (Data Manipulation Language):
Seguir o link para leitura

    http://www.bosontreinamentos.com.br/bancos-de-dados/comandos-dml-sql-e-sua-sintaxe/
    https://docs.getdbt.com/terms/dml#:~:text=Data%20Manipulation%20Language%20(DML)%20is,level%20data%20from%20database%20tables
    https://docs.oracle.com/cd/B14156_01/doc/B13812/html/sqcmd.htm#CHDJCBDH

### Definição DML - Data Manipulation Language
É uma classe de declaração de SQL que é usado para requisitar (query), editar (edit),  adicionar (add) e deletar (delete) dados da linha ou coluna de uma base de dados, tabelas ou views.

### Comandos usados
Os comandos mais usados dessa categoria de declarações são:

- INSERT - Criar um novo registro (linha) em uma tabela

- UPDATE - Permite modificar registros em uma tabela

- DELETE - Exclui um ou mais registros selecionados de uma tabela

- SELECT INTO - Realiza uma consulta em uma tabela e inclui o resultado como um novo registro em outra tabela.

Claro, a lista acima são as mais usuais. Porém, existem outras que se encaixam dentro dessa categoria de declarações. São elas:

- EXPLAIN PLAN select_command - Determina um plano de execução em uma requisição/A requisição para qual você determina um plano de execução.

As instruções DML primárias, como foi listado acima, são SELECT, INSERT, DELETE e UPDATE. Com exceção das SELECT instruções, todas as outras são aplicáveis ​​apenas aos dados dentro das tabelas em um banco de dados. A principal diferença entre SELECT e todas as outras instruções DML é seu impacto nos dados em nível de linha:

- Para alterar os dados reais que residem nas tabelas, use as instruções INSERT, DELETE e UPDATE.

- Para acessar os dados no objeto databse, use SELECT instruções.
Todas as SELECT as intruções precisam de trÊs elementos:
    - SELECT cláusula no início

    - Seleção e manipulação do campo real

    - FROM, instrução que especifica qual objeto de banco de dados você está tentando acessar

Seguir um exemplo ilustrativo

        select

            payment_method,
            sum(amount) AS amount

        from {{ ref('raw_payments') }}
        group by 1

Neste exemplo, sua seleção da payment_method coluna e o somatório da amount coluna são a essência de sua consulta. O from {{ ref('raw_payments') }}especifica a tabela real da qual você deseja fazer a seleção.

Para o uso de teste vamos usar o arquivo 1_dml.sql.

## Aula 03 e 04 - DDL PARTE 1 e 2:
Seguir o link para leitura

    https://satoricyber.com/glossary/ddl-data-definition-language/#:~:text=DDL%20statements%20are%20similar%20to,considered%20a%20subset%20of%20SQL.

### Definição DDL - Data Definition Language
DDL é um conjunto de comandos SQL usados ​​para criar, modificar e excluir estruturas de banco de dados, mas não dados. Em outras palavras, o DDL são as sintaxes que permite criar e modificar objetos de banco de dados, como tabelas, índices e usuários.

Lista de comandos DDL: 

- CREATE : Este comando é usado para criar o banco de dados ou seus objetos (como tabela, índice, função, visualizações, procedimento de armazenamento e gatilhos).

- DROP : Este comando é usado para deletar objetos do banco de dados.

- ALTER : usado para alterar a estrutura do banco de dados.

- TRUNCATE : É usado para remover todos os registros de uma tabela, inclusive todos os espaços alocados para que os registros sejam removidos.

- COMENTÁRIO : usado para adicionar comentários ao dicionário de dados.

- RENAME : Usado para renomear um objeto existente no banco de dados.

Para o uso de teste vamos usar o arquivo 2_ddl.sql.

### Diferença entre DDL e DML
Seguir o link de leitura

    https://www.geeksforgeeks.org/difference-between-ddl-and-dml-in-dbms/?ref=rp
    
É importante ressaltar que DDL e DML são diferentes conceitos.

DDL é a linguagem de definição de dados usada para definir estruturas de dados. Por exemplo: criar tabela, alterar tabela são instruções em SQL. DML é a Linguagem de Manipulação de Dados usada para manipular os próprios dados. Por exemplo: insert, update e delete são instruções em SQL.

## Aula 05 e 06 - DCL GRANT e REVOKE:
Seguir o link de leitura

    https://docs.oracle.com/cd/B14156_01/doc/B13812/html/sqcmd.htm
    https://www.scaler.com/topics/dcl/
    https://www.educative.io/answers/what-are-the-grant-and-revoke-commands-of-dcl
    https://www.geeksforgeeks.org/difference-between-grant-and-revoke/

### Definição DCL - Linguagem de Controle de Dados
DCL inclui comandos como GRANT e REVOKE que lidam principalmente com os direitos, permissões e outros controles do sistema de banco de dados.

Lista de comandos DCL: 

- GRANT: Este comando dá aos usuários privilégios de acesso ao banco de dados.

- REVOKE: Este comando retira os privilégios de acesso do usuário concedidos usando o comando GRANT.

### GRANT
Para o uso de teste vamos usar o arquivo 3_dcl_grant.sql usando a conexão Ora XE.

Basicamente, o Grant serve para permitir que duas conexões se comuniquem.

### REVOKE
Para o uso de teste vamos usar o arquivo 4_dcl_revoke_aula.sql.

Ao contrário do grant, o Revoke, serve para sessar a comunicação com duas conexões.

## Aula 07 - TCL:
Seguir o link de leitura

    https://byjus.com/gate/tcl-full-form/#:~:text=What%20Is%20The%20Full%20Form,commands%20for%20maintaining%20its%20transactions.
    https://www.geeksforgeeks.org/difference-between-grant-and-revoke/

### Definição TCL - Linguagem de Controle de Transação
As transações agrupam um conjunto de tarefas em uma única unidade de execução. Cada transação começa com uma tarefa específica e termina quando todas as tarefas do grupo são concluídas com sucesso. Se alguma das tarefas falhar, a transação falhará. Portanto, uma transação tem apenas dois resultados: sucesso ou falha.

Os seguintes comandos TCL são usados ​​para controlar a execução de uma transação: 

- BEGIN: Abre uma Transação.

- COMMIT : Confirma uma transação.

Este comando é usado para salvar os dados permanentemente. 

Sempre que executamos qualquer um dos comandos DML como -INSERT, DELETE ou UPDATE, eles podem ser revertidos se os dados não forem armazenados permanentemente.

Portanto, para estar no lado mais seguro, o comando COMMIT é usado. 

- ROLLBACK : Reverte uma transação caso ocorra algum erro.

Este comando é usado para obter os dados ou restaurar os dados para o último ponto de salvamento ou último estado confirmado. Se, por algum motivo, os dados inseridos, excluídos ou atualizados não estiverem corretos, você pode reverter os dados para um ponto de salvamento específico ou, se o ponto de salvamento não for feito, para o último estado confirmado. 

- SAVEPOINT : Define um ponto de salvamento dentro de uma transação.

Este comando é usado para salvar temporariamente os dados em um determinado ponto, para que sempre que necessário possa ser revertido para aquele determinado ponto.

- SET TRANSACTION: Especifica as características da transação.

 Esses comandos são utilizados para manter a consistência do banco de dados e para o gerenciamento das transações feitas pelos comandos DML.

 Uma transação é um conjunto de instruções SQL que são executadas nos dados armazenados no DBMS. Sempre que qualquer transação é feita, essas transações acontecem temporariamente no banco de dados. 
 
 Portanto, para tornar as alterações permanentes, usamos comandos  TCL.

## Aula 08 (Que por algum motivo não foi abordado...) - DQL:
Seguir o link de leitura

    https://www.geeksforgeeks.org/sql-ddl-dql-dml-dcl-tcl-commands/

### Definição DQL - Linguagem de Consulta de Dados
As instruções DQL são usadas para realizar consultas nos dados dentro dos objetos do esquema.

O objetivo do comando DQL é obter alguma relação de esquema com base na consulta passada para ele. Podemos definir DQL da seguinte forma: é um componente da instrução SQL que permite obter dados do banco de dados e impor ordem sobre eles. Inclui a instrução SELECT. Este comando permite obter os dados do banco de dados para realizar operações com ele. Quando um SELECT é acionado contra uma tabela ou tabelas, o resultado é compilado em uma tabela temporária adicional, que é exibida ou talvez recebida pelo programa, ou seja, um front-end.

Lista de DQL: 

- SELECT : É usado para recuperar dados do banco de dados.

    A sua estrutura sintática é 

        SELECT "column_name" FROM "table_name";    
