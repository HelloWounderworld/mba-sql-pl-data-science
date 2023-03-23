# Seção 03: LANGUAGE STATEMENTS:
Realizar as leituras dos links e ir colocandos os pontos importantes nas minhas notas e realizar testes!

## Aula 01 - INTRODUÇÃO LANGUAGE STATEMENTS:
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

Para o uso de teste vamos usar o arquivo 2_ddl.sql.

## Aula 05 - DCL GRANT:
Seguir o link de leitura

    https://docs.oracle.com/cd/B14156_01/doc/B13812/html/sqcmd.htm
    https://www.scaler.com/topics/dcl/
    https://www.educative.io/answers/what-are-the-grant-and-revoke-commands-of-dcl
    https://www.geeksforgeeks.org/difference-between-grant-and-revoke/

Para o uso de teste vamos usar o arquivo 3_dcl_grant.sql usando a conexão Ora XE.

Basicamente, o Grant serve para permitir que duas conexões se comuniquem.

## Aula 06 - DCL REVOKE:
Seguir o link de leitura

    https://www.microfocus.com/documentation/enterprise-developer/ed80/ED-Eclipse/HRQRRHSQLX45.html
    https://docs.oracle.com/cd/B14156_01/doc/B13812/html/sqcmd.htm
    https://www.geeksforgeeks.org/difference-between-grant-and-revoke/

Para o uso de teste vamos usar o arquivo 4_dcl_revoke_aula.sql.

Ao contrário do grant, o Revoke, serve para sessar a comunicação com duas conexões.

## Aula 07 - TCL:
Seguir o link de leitura

    https://byjus.com/gate/tcl-full-form/#:~:text=What%20Is%20The%20Full%20Form,commands%20for%20maintaining%20its%20transactions.
