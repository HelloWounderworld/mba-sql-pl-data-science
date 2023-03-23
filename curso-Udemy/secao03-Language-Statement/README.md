# Seção 03: LANGUAGE STATEMENTS:
Realizar as leituras dos links e ir colocandos os pontos importantes nas minhas notas e realizar testes!

## Aula 01 - INTRODUÇÃO LANGUAGE STATEMENTS:
Seguir o link para leitura

    https://www.javatpoint.com/sql-tutorial
    https://www.geeksforgeeks.org/sql-ddl-dql-dml-dcl-tcl-commands/
    https://docs.oracle.com/cd/B14156_01/doc/B13812/html/sqcmd.htm

Vamos deixar um ponto bem claro aqui sobre o SQL.

Ele não é um sistem de Banco de dados, mas sim é uma linguagem de consulta.

Bom, visto isso, então vem a pergunta, onde estou conseguindo consultar os dados dos comandos que são imputados quando eu estou mexendo na Oracle? A resposta está na minha própria pergunta kkkkkk

Sim, a própria Oracle, nesse caso, está sendo o banco de dados que estou usando e estamos usando o SQL para conseguir consultar os dados armazenados dentro da Oracle. Assim como, o mesmo seria possível fazer nos outros bancos de dados como MySQL, MongoDB, PostgreSQL, SQL Server, DB2, etc...

### O que é SQL?
SQL é uma forma abreviada da linguagem de consulta estruturada e é pronunciada como SQL ou, às vezes, como See-Quell.

Creio que para as pessoas que já conhecem um pouco sobre banco de dados, devem ter tido algumas dúvidas acima quando falei que a SQL, sendo ela uma linguagem de consulta, pode ser aplicável em um conjunto de listas de banco de dados que mencionei acima. Sendo que dentro dessa lista constava alguns bancos de dados não relacionais, sendo que o próprio banco de dados não relacionais, ela já possui, em grande parte, a própria linguagem para realizar a consulta/requisição nela. De fato, a dúvida é bem pertinente, pois vale ressaltar aqui que a linguagem de consulta estruturada, SQL, ele serve, essencialmente, para banco de dados relacionais. Ou seja, é voltada especialmente dados que estão em sua forma estruturados (em forma de tabela, tipo excel). Ela também é projetado para processamento de fluxo em RDSMS.

Bom, para quem quiser saber mais sobre como surgiu o SQL, basta procurar por RDSMS, pois isso é referenciado dos autores chamado EF Codd, onde consta o artigo dele que originou tudo (codd.pdf), pois foi com base do artigo do Codd que foi lido por dois pesquisadores da IBM que permitiu o surgimento dessa linguagem estruturada.

Essa linguagem de consulta tornou-se o padrão da ANSI no ano de 1986 e da ISO no ano de 1987.

Bom, se você deseja conseguir um emprego na área de ciência de dados, essa é a linguagem de consulta mais importante a ser aprendida. Grandes empresas como Facebook, Instagram e LinkedIn usam SQL para armazenar os dados no back-end.

### Por que SQL?
Atualmente, o SQL é amplamente utilizado em ciência e análise de dados. A seguir estão as razões que explicam por que é amplamente utilizado:

- O uso básico do SQL para profissionais de dados e usuários do SQL é inserir, atualizar e excluir os dados do banco de dados relacional.

- O SQL permite que os profissionais e usuários de dados recuperem os dados dos sistemas de gerenciamento de banco de dados relacional.

- Também os ajuda a descrever os dados estruturados.

- Ele permite que os usuários do SQL criem, eliminem e manipulem o banco de dados e suas tabelas.

- Também ajuda na criação da exibição, do procedimento armazenado e das funções no banco de dados relacional.

- Ele permite que você defina os dados e modifique os dados armazenados no banco de dados relacional.

- Ele também permite que os usuários do SQL definam as permissões ou restrições nas colunas da tabela, exibições e procedimentos armazenados.

### Processos de SQL
A linguagem de consulta estruturada contém os quatro componentes a seguir em seu processo:

- Despachante de consultas

- Mecanismo de otimização

- Mecanismo de consulta clássico

- Mecanismo de consulta SQL, etc.

Pesquisar mais à fundo de cada um dos processos e entender a definição de cada uma e tomar notas disso depois.

### Alguns comandos SQL
Os comandos SQL ajudam na criação e gerenciamento do banco de dados. Os comandos SQL mais comuns e altamente usados ​​são mencionados abaixo:

- comando CREATE:
Este comando ajuda na criação do novo banco de dados, nova tabela, exibição de tabela e outros objetos do banco de dados.

- comando UPDATE:
Este comando ajuda a atualizar ou alterar os dados armazenados no banco de dados.

- Comando EXCLUIR:
Este comando ajuda a remover ou apagar os registros salvos das tabelas do banco de dados. Ele apaga tuplas únicas ou múltiplas das tabelas do banco de dados.

- Comando SELECIONAR:
Este comando ajuda a acessar as linhas únicas ou múltiplas de uma ou várias tabelas do banco de dados. Também podemos usar este comando com a cláusula WHERE.

- comando DROP:
Este comando ajuda a excluir toda a tabela, exibição de tabela e outros objetos do banco de dados.

- comando INSERT:
Este comando ajuda a inserir os dados ou registros nas tabelas do banco de dados. Podemos inserir facilmente os registros em uma ou várias linhas da tabela.

Vale a pena, depois, dar uma olhada sobre o comparativo entre SQL e NoSQL.

## Aula 02 - DML:
Seguir o link para leitura

    http://www.bosontreinamentos.com.br/bancos-de-dados/comandos-dml-sql-e-sua-sintaxe/
    https://docs.getdbt.com/terms/dml#:~:text=Data%20Manipulation%20Language%20(DML)%20is,level%20data%20from%20database%20tables
    https://docs.oracle.com/cd/B14156_01/doc/B13812/html/sqcmd.htm#CHDJCBDH

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
