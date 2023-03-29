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

    Vamos estudar as suas sintaxes.

    No caso, para inserir um dado diretamente em uma tabela

        INSERT INTO table_name VALUES (value1, value2, value3....);

    Essa forma de inserção vc não precisa especificar a coluna da tabela onde vc estiver inserindo o dado.

    E tem, tbm, a forma em especificar a coluna

        INSERT INTO table_name (column1, column2, column3....) VALUES (value1, value2, value3.....);

    Inserindo dados atráves da declaração SELECT. A sua sintaxe

        INSERT INTO table_name  [(column1, column2, .... column)] SELECT column1, column2, .... Column N FROM table_name [WHERE condition];

    Seguir o link de leitura

        https://www.javatpoint.com/sql-insert

- UPDATE - Permite modificar registros em uma tabela

    Lembrando que o UPDATE vale mais para dados que já estão presentes no banco de dados.

    A sua sintaxe para aplicar a atualização é o seguinte

        UPDATE table_name SET [column_name1= value1,... column_nameN = valueN] [WHERE condition]

    A sintaxe em sua forma simplificada é o seguinte

        UPDATE table_name SET column_name = expression WHERE conditions

    Podemos usar a declaração SELECT para atualizar um registro através da declaração UPDATE

        UPDATE tableDestination SET tableDestination.col = value WHERE EXISTS (SELECT col2.value FROM  tblSource WHERE tblSource.join_col = tblDestination. Join_col AND  tblSource.Constraint = value)
    
    Ou vc pode tentar essa tbm

        UPDATE Table SET Table.column1 = othertable.column 1, Table.column2 = othertable.column 2 FROM Table INNER JOIN Other_table ON Table.id = other_table.id 

    Seguir o link de leitura para mais funcionalidades de UPDATE

        https://www.javatpoint.com/sql-update

- DELETE - Exclui um ou mais registros selecionados de uma tabela

    A sintaxe para aplicar essa lógica é o seguinte

        DELETE FROM table_name [WHERE condition];

    Aqui o table_name é a tabela na qual tem que ser deletado. O WHERE em SQL DELETE é opcional. Ou seja, se vc usar o DELETE sem o WHERE, significa que vc estará excluindo todos os dados da tabela. A exclusão se dá por linha.

    Em Oracle, vc não pode usar o "*" da seguinte forma

        DELETE * FROM table_name

    Isso não irá excluir os dados da tabela inteira.

    Seguir o link de leitura para mais funcionalidades do DELETE

        https://www.javatpoint.com/sql-delete

- SELECT INTO - Realiza uma consulta em uma tabela e inclui o resultado como um novo registro em outra tabela.

    A sintaxe para o uso seria

        SELECT * INTO newtable [IN externaldb] FROM oldtable WHERE condition;

    O formato acima seleciona toda a coluna.

    Agora, selecionando determinadas colunas

        SELECT column1, column2, column3, ... INTO newtable [IN externaldb] FROM oldtable WHERE condition;

    Uma nova tabela será criado caso a tabela, na qual vc queira enviar os dados não exista. Ou se existir, simplesmente será inputado.

    Nesse processo, vc pode usar o AS para criar uma nova coluna e dentro dela colocar os dados que vc queira colocar.

    Podemos usar a sintaxe IN para copiar uma tabela dentro de uma nova tabela

        SELECT * INTO CustomersBackup2017 IN 'Backup.mdb' FROM Customers;

    Seguir o link de leitura

        https://www.w3schools.com/sql/sql_select_into.asp

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
    
    Para a criação do banco de dados

    - O banco de dados que queremos criar deve ser simples e com único nome, na qual pode ser facilmente identificado.

    - O nome de um banco de dados deve ter não mais de 128 caracteres.
    
    A sintaxe certa para isso seria o seguinte

        CREATE DATABASE Database_Name;

    OBS: Não há necessidade de criar banco de dados no sistema Oracle. No banco de dados da Oracle, podemos diretamente criar a tabela de banco de dados.

    Seguir o link de leitura

        https://www.javatpoint.com/sql-create-database

    Bom, no caso da Oracle, usamos, basicamente, CREATE TABLE, visto a condição acima. Para isso a sintaxe para isso seria o seguinte

        create table "tablename"
        ("column1" "data type",
        "column2" "data type",
        "column3" "data type",
        ...
        "columnN" "data type");
    
    OBS: O tipo de dado das colunas poderia variar de uma base de dados para outra. Por exemplo, NUMBER é suportado no banco de dados Oracle para valores inteiros, equanto que para MySQL é suportado INT.

    Podemos, também, criar uma tabela com base da outra tabela, realizando uma cópia dela. A nova tabela obterá as mesmas colunas como na tabela antiga. Nesse processo de cópia podemos selecionar todas as colunas ou apenas selecionar algumas. A sintaxe para isso é o seguinte

        CREATE TABLE table_name AS
        SELECT column1, column2,...
        FROM old_table_name WHERE ..... ; 

    The following SQL creates a copy of the employee table.

        CREATE TABLE EmployeeCopy AS
        SELECT EmployeeID, FirstName, Email
        FROM Employee;

    Seguir o link de leitura

        https://www.javatpoint.com/sql-create-table

    Temos o uso no CREATE para sequências tbm. Basicamente, o SEQUENCE em SQL é usado para criar uma sequência de objetos e suas propriedades pode ser, também, especificados. A sintaxe para isso seria o seguinte

        CREATE SEQUENCE [name_of_schema.] name_of_sequence
        [ AS type_as_integer ]
        [ START WITH starting_value_of_sequence ]    
        [ INCREMENT BY incremental_index ]    
        [ { MINVALUE [ minimum_value ] } | { NO MINVALUE } ]    
        [ { MAXVALUE [ maximum_value ] } | { NO MAXVALUE } ]    
        [ CYCLE | { NO CYCLE } ]    
        [ { CACHE [ size_of_cache ] } | { NO CACHE } ];

    Na sintaxe escrito acimma tem, basciamente, os seguintes significados

    - Name_of_schema: O name_of_schema especifica o esquema ao qual essa sequência pertencerá.

    - Type_as_integer: O tipo de dados type_as_integer do objeto Sequence. Alguns dos tipos de dados com suporte para objetos Sequence são NUMERIC, BIGINT, INT, TINYINT, DECIMAL e SMALLINT.

    Podemos qualquer um deles de acordo com nossa exigência:
    
    - bigint - Varia de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807

    - int - Varia de -2.147.483.648 a 2.147.483.647

    - decimal e numérico com uma escala de 0

    - smallint - Varia de -32.768 a 32.767

    - tinyint - Varia de 0 a 255

    - Starting_value_of_sequence: O Starting_value_of_sequence representa o valor inicial da sequência. O objeto de sequência é inicializado com este valor e incrementação ou decrementação adicional é feita neste valor.

    - Incremental_index: O incremental_index representa o valor ou índice pelo qual o valor inicial da sequência será incrementado cada vez que o próximo valor do objeto de sequência for buscado.

    - Minimum_value: O Minimum_value representa o valor mínimo que um objeto de sequência pode atingir. Funciona como um limite inferior.

    - Maximum_value: O maximum_value representa o valor máximo que um objeto de sequência pode atingir. Funciona como um limite superior.

    - Size_of_cache: O size_of_cache representa o número de valores a serem armazenados em cache para melhorar o desempenho do objeto de sequência.

    Seguir o link de leitura

        https://www.javatpoint.com/sql-server-sequence

- DROP : Este comando é usado para deletar objetos do banco de dados.

    Seguir os links de leitura

        https://www.w3schools.com/sql/sql_ref_drop.asp
        https://www.javatpoint.com/sql-drop-database
        https://www.javatpoint.com/sql-drop-table

    

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

    ou 

        SELECT Column_Name_1, Column_Name_2, ....., Column_Name_N FROM Table_Name;

    Bom, claro, os Column_Name_1, Column_Name_2, ..., Column_Name_N, os os nomes das colunas da tabela que vc queira consultar.

    Bom, seria o uso básico acima. Mas, vale ressaltar que temos outras formas de combinações do uso de SELECT com outras sintaxes.

    Se vc quiser que seja exibido todas as colunas de uma tabela vc usa o "*"

        SELECT * FROM table_name; 

    Uso do SELECT com o WHERE. No caso, o WHERE aqui ele funciona para filtrar certos tipos de elementos que existem dentro da coluna

        SELECT * FROM Name_of_Table WHERE [condition]; 

    Lembrando que o WHERE ele não é uma sintaxe dependente do SELECT.

    Uso do SELECT com GROUP BY. O GROUP BY, aqui ele é usado com o SELECT para mostrar dados comuns de uma coluna da tabela. No caso, a sintaxe aqui é o seguinte

        SELECT column_Name_1, column_Name_2, ....., column_Name_N aggregate_function_name(column_Name2) FROM table_name GROUP BY column_Name1;

    Uso do SELECT com o HAVING. O HAVING cria uma seleção naqueles grupos na qual são definidos pelo GROUP BY. A sua sintaxe seria o seguinte

        SELECT column_Name_1, column_Name_2, ....., column_Name_N aggregate_function_name(column_Name_2) FROM table_name GROUP BY column_Name1 HAVING ;  

    Uso do SELECT com o ORDER BY. O ORDER BY ele é uma sintaxe dependente do SELECT e serve para mostrar registros ou linhas de forma ordenada. Basicamente, a forma de ordenação está em ascendente e descendente. A sua sintaxe é o seguinte

        SELECT Column_Name_1, Column_Name_2, ....., column_Name_N FROM table_name WHERE [Condition] ORDER BY[column_Name_1, column_Name_2, ....., column_Name_N asc | desc ];
