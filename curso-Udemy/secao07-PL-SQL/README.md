# Seção 07: PL/SQL:
Seguir o link de leitura

    https://www.javatpoint.com/pl-sql-tutorial

## Aula 01 - INTRODUÇÃO:
Seguir o link de leitura

    https://www.devmedia.com.br/conhecendo-o-pl-sql/24763
    https://www.oracle.com/br/database/technologies/appdev/plsql.html
    https://blog.betrybe.com/linguagem-de-programacao/pl-sql-tudo-sobre/
    https://pt.stackoverflow.com/questions/480913/qual-a-diferen%C3%A7a-entre-sql-server-mysql-e-outros-sql#:~:text=SQL%20%C3%A9%20uma%20linguagem%20de,o%20banco%20de%20dados%20ORACLE.

## Aula 02 - CONJUNTO DE CARACTERS:
Conjuntos de caracteres

- Letras:
PL/SQL é case-insentive (o compilador enxerga tudo como uppercase) e aceita os caracteres: A-Z, a-z, 0-9, whitespace (tab, espaço, newline, carriage return) e símbolos (~!@#$%*()_-+=|:;"'<>,.?/^).

    A-Z, a-z

- Digitos:

    0-9

- Símbolos:

    ; - Termina os statements e declarações
    % - Indicador de atributos
    @ - Indicador de localização
    << e >> - Delimitadores de labels
    := - é indicador de atribuição de valor à variáveis, etc.
    => - é operador de associação para notação posicional
    .. - é operador de range

## Aula 03 - VARIAVEIS:
Seguir o link de leitura

    https://oraclepress.wordpress.com/2015/11/18/variaveis-plsql/
    https://www.devmedia.com.br/pl-sql-tipos-de-dados-escalar-e-lob/29824
    https://www.ibm.com/docs/pt-br/db2/11.5?topic=support-variables-plsql

O arquivo para poder realizar o teste é 1_DECLARA_VARIAVEIS.SQL.

## Aula 04 - ATRIBUTOS TYPE E ROWTYPE:
Seguir o link de leitura

    https://www.ibm.com/docs/pt-br/db2/11.1?topic=plsql-rowtype-attribute-in-record-type-declarations
    https://www.profissionaloracle.com.br/2016/09/29/type-do-tipo-table-com-atributo-rowtype/
    https://pt.stackoverflow.com/questions/380966/pl-sql-record-type-vs-rowtype
    https://fabiosmorais.wordpress.com/2008/07/25/quando-usar-o-type-e-rowtype/

O arquivo para poder realizar o teste é 2_atrib_type_rowtype.sql.

## Aula 05 - TIPO DE REGISTRO:
Seguir o link de leitura

    http://profesionghh.blogspot.com/2015/02/registros-plsql.html#:~:text=Los%20registros%20(Records)%20son%20un,varchar%2C%20n%C3%BAmero%2C%20entre%20otros.
    https://elbauldelprogramador.com/plsql-registros-y-tablas/#:~:text=Los%20registros%20no%20son%20m%C3%A1s,acceden%20con%20el%20mismo%20nombre.
    https://www.ibm.com/docs/es/db2/11.5?topic=support-collection-record-object-types-plsql
    https://www.juntadeandalucia.es/servicios/madeja/contenido/recurso/107

O arquivo para poder realizar o teste é 3_tipo_registro.sql.

## Aula 06 - ESCOPO DE VARIAVEIS:
Seguir o link de leitura

    https://oraclepress.wordpress.com/2015/11/18/variaveis-plsql/
    https://www.devmedia.com.br/pl-sql-tipos-de-dados-escalar-e-lob/29824
    https://www.ibm.com/docs/pt-br/db2/11.5?topic=support-variables-plsql

O arquivo para poder realizar o teste é 4_escopo_var.sql.

## Aula 07 - IDENTIFICADORES:
Seguir o link de leitura

    https://www.juntadeandalucia.es/servicios/madeja/contenido/recurso/107

Esse aqui é melhor assistir a vídeo aula e anotar aqui mesmo o conteúdo.

## Aula 08 - BLOCOS ANÔNIMOS:
Seguir o link de leitura

    https://www.ibm.com/docs/pt-br/db2/11.5?topic=support-blocks-plsql
    https://www.ibm.com/docs/pt-br/db2/11.1?topic=plsql-anonymous-block-statement
    https://gist.github.com/samueltcsantos/359c1dd926c37b8e3b48

O arquivo para realizar os teste é o 5_bloco_anonimo.sql.

## Aula 09 - ESTRUTURA IF-THEN / IF-THEN-ELSE / IF-THEN-ELSIF:
Seguir o link de leitura

    https://www.w3schools.blog/if-else-plsql
    https://www.guru99.com/pl-sql-decision-making-statements.html
    https://docs.oracle.com/database/121/LNPLS/controlstatements.htm#LNPLS00402

O arquivo para realizar o teste é o 6_estrutura_if.sql.

## Aula 10 - ESTRUTURA CASE WHEN:
Seguir o link de leitura

    https://www.devmedia.com.br/estruturas-condicionais-sequenciais-e-comentarios-no-oracle/32984
    https://www.techonthenet.com/oracle/functions/case.php
    https://www.oracletutorial.com/plsql-tutorial/plsql-case-statement/

O arquivo para realizar o teste é o 7_case.sql.

## Aula 11 - GOTO:
Seguir o link de leitura

    https://www.devmedia.com.br/estruturas-condicionais-sequenciais-e-comentarios-no-oracle/32984
    https://www.techonthenet.com/oracle/loops/goto.php
    https://www.oracletutorial.com/plsql-tutorial/plsql-goto/
    https://docs.oracle.com/database/121/LNPLS/goto_statement.htm#LNPLS01323
    https://www.tutorialspoint.com/plsql/plsql_goto_statement.htm

O arquivo para realizar o teste é o 8_goto.sql.

## Aula 12 - LOOP FOR:
Seguir o link de leitura

    https://www.devmedia.com.br/estruturas-condicionais-sequenciais-e-comentarios-no-oracle/32984
    https://pt.stackoverflow.com/questions/201349/loop-em-pl-sql-oracle
    https://www.javatpoint.com/pl-sql-for-loop

O arquivo para realizar o teste é o 9_for.sql.

## Aula 13 - LOOP WHILE:
Seguir o link de leitura

    https://www.devmedia.com.br/estruturas-condicionais-sequenciais-e-comentarios-no-oracle/32984
    https://www.techonthenet.com/oracle/loops/while.php
    https://www.oracletutorial.com/plsql-tutorial/plsql-while-loop/
    https://docs.oracle.com/cd/E18283_01/appdev.112/e17126/while_loop_statement.htm

O arquivo para realizar o teste é o 10_while.sql.

## Aula 14 - LOOP CONTINUE:
Seguir o link de leitura

    https://www.oracletutorial.com/plsql-tutorial/plsql-continue/
    https://docs.oracle.com/database/121/LNPLS/continue_statement.htm#LNPLS01360
    https://www.tutorialspoint.com/plsql/plsql_continue_statement.htm
    https://www.ibm.com/docs/en/db2/11.5?topic=plsql-continue-statement

O arquivo para realizar o teste é 11_Loop_continue.sql.
