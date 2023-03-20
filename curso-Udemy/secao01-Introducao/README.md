# Seção 01: Introdução:

## Aula 01 - Apresentação do Instrutor:

## Aula 02 - Introdução:

## Aula 03 - INSTALANDO ORACLE XE:
Seguir os dois links para tal finalidade

    https://www.oracle.com/database/technologies/xe-prior-release-downloads.html
    https://www.dropbox.com/s/k6wng52rsb633i8/OracleXE112_Win64.zip?dl=0

Caso vc não tenha alguma conta na Oracle, será necessário criar uma sua.

## Aula 04 - CONFIGURANDO SQL DEVELOPER:
Seguir o link de configuração do SQL Developer

    https://docs.oracle.com/en/database/oracle/sql-developer/19.2/

No caso, vamos precisar criar uma coneção de forma manual, donde vc colocará como nome "Ora XE" e com nome de usuário "system" e a senha que vc configurou na instalação do sql-developer acima.

## Aula 05 - CRIANDO TABLESPACE:
Seguir o arquivo

    create_table_space.sql

Vc terá que abrir esse arquivo no Oracle SQL Developer e rodar ele para podemos criar o arquivo CURSO.DBF.

Para isso, seria necessário selecionar o código que faz essa criação e clicar no botão play para de fato ocorrer a criação

    create tablespace curso
     datafile
        'C:\oraclexe\app\oracle\oradata\XE\curso.dbf' 
            size 100m autoextend on next 50m maxsize 500m
        online
        permanent
        extent management local autoallocate
        segment space management auto;

Deixar o código acima selecionado e então, clicar em Play para criar o tal arquivo.

## Aula 06 - HISTORICO LINGUAGEM SQL:
Seguir o link de leitura

    https://harve.com.br/blog/analise-de-dados/o-que-e-sql/#:~:text=SQL%20foi%20criado%20no%20come%C3%A7o,dados%20da%20IBM%2C%20System%20R.
    https://www.devmedia.com.br/entedendo-a-linguagem-sql/7775#:~:text=A%20linguagem%20SQL%20surgiu%20em,adapta%2Dse%20ao%20modelo%20relacional.

## Aula 07 - DEFINIÇÃO PL/SQL:
Seguir o link de leitura

    https://pt.wikipedia.org/wiki/PL/SQL#:~:text=PL%2FSQL%20(acr%C3%B3nimo%20para%20a,inclu%C3%ADda%20em%20unidades%20de%20programas.
    https://www.oracle.com/br/database/technologies/appdev/plsql.html#:~:text=A%20PL%2FSQL%20%C3%A9%20uma,armazenadas%20no%20banco%20de%20dados.
    https://pt.stackoverflow.com/questions/480913/qual-a-diferen%C3%A7a-entre-sql-server-mysql-e-outros-sql#:~:text=SQL%20%C3%A9%20uma%20linguagem%20de,o%20banco%20de%20dados%20ORACLE.
    https://www.devmedia.com.br/conhecendo-o-pl-sql/24763

## Aula 08 e 09 - CONCEITOS DB PARTE 1 e 2:
Seguir o link de leitura

    https://www.devmedia.com.br/conceitos-fundamentais-de-banco-de-dados/1649
    https://www.oracle.com/br/database/what-is-database/#:~:text=Banco%20de%20Dados%3F-,Banco%20de%20dados%20definido,banco%20de%20dados%20(DBMS).
    https://thihenos.medium.com/sql-performance-1-a-matem%C3%A1tica-por-tr%C3%A1s-dos-bancos-de-dados-1ff6236162f7
    https://pt.wikipedia.org/wiki/Banco_de_dados_relacional

## Aula 10 - DIAGRAMA DE DADOS:
Seguir o link de leitura

    https://www.devmedia.com.br/modelagem-de-dados-tutorial/20398
    https://www.edrawsoft.com/pt/how-to-draw-database-model-diagram.html
    https://www.lucidchart.com/pages/pt/tutorial-de-criacao-e-estruturacao-de-banco-de-dados

## Aula 11 - CARACTERISTICAS DE BANCO DE DADOS RELACIONAL:
Seguir o link de leitura

    https://www.devmedia.com.br/bancos-de-dados-relacionais/20401
    https://natahouse.com/pt/bancos-relacionais-x-bancos-nao-relacionais-quando-usar-cada-um

## Aula 12 - MER MODELO ENTIDADE RELACIONAMENTO:
Seguir o link de leitura

    https://www.alura.com.br/artigos/mer-e-der-funcoes#:~:text=O%20que%20%C3%A9%20o%20MER,atributos%20e%20os%20seus%20relacionamentos.
    https://www.devmedia.com.br/mer-e-der-modelagem-de-bancos-de-dados/14332#:~:text=O%20Modelo%20Entidade%20Relacionamento%20(tamb%C3%A9m,elas%20se%20relacionam%20entre%20si%20(
    https://www.remessaonline.com.br/blog/mer-e-der-o-que-e-as-principais-diferencas-e-como-usar/

## Aula 13 - CARDINALIDADE:
Seguir o link para leitura

    https://www.devmedia.com.br/tecnologias-de-banco-de-dados-e-modelagem-de-dados/1660#:~:text=A%20cardinalidade%20%C3%A9%20um%20n%C3%BAmero,em%20quest%C3%A3o%20atrav%C3%A9s%20do%20relacionamento.
    https://pt.wikipedia.org/wiki/Cardinalidade_(modelagem_de_dados)
    https://www.ime.usp.br/~andrers/aulas/bd2005-1/aula7.html
    https://consultabd.wordpress.com/2019/08/28/cardinalidade/

## Aula 14 - SGBD:
Seguir o link para leitura

    https://es.wikipedia.org/wiki/Sistema_de_gesti%C3%B3n_de_bases_de_datos
    https://www.treinaweb.com.br/blog/o-que-e-um-sgbd#:~:text=Data%20Base%20Management%20System%20ou,as%20bases%20de%20dados%20utilizadas

## Aula 15 - TIPO DE DADOS:
Seguir o link para leitura

    https://docs.oracle.com/cd/B28359_01/server.111/b28318/datatype.htm#CNCPT012

Seguir o pdf de referência

    Data_types.pdf

## Aula 16 - ACID E CRUD:
- ACID - Seguir o link de leitura

    https://es.wikipedia.org/wiki/ACID
    https://blog.betrybe.com/tecnologia/acid-porque-usar/

- CRUD - Seguir o link de leitura

    https://developer.mozilla.org/pt-BR/docs/Glossary/CRUD
    https://coodesh.com/blog/dicionario/o-que-e-crud/#:~:text=CRUD%20%C3%A9%20usado%20na%20linguagem%20SQL&text=Trata%2Dse%20de%20um%20grupo,de%20um%20banco%20de%20dados.

## Aula 17 - CONSTRAINTS:
Seguir o pdf de leitura

    relatorio.pdf

Seguir o link de leitura

    https://www.w3schools.com/sql/sql_constraints.asp#:~:text=SQL%20constraints%20are%20used%20to%20specify%20rules%20for%20the%20data,action%2C%20the%20action%20is%20aborted.
    https://www.devmedia.com.br/artigo-sql-magazine-31-tutorial-sql-constraints/6761
