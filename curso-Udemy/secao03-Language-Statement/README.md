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

### Vantagens do SQL
Bom, principalmente, para áreas que envolve ciências de dados ou, de modo mais geral, que envolve a necessidade de organizar e analisar um grande volume de dados, o SQL, aplicado para banco de dados relacional, acaba sendo a mais vantajosa, por conta da sua estrutura simples de códificação, o que não exige tanto esforço, e pela sua alta velocidade de requisição.

Organizando em tópicos, mais ou menos, ficaria assim:

- Nenhuma programação necessária:
O SQL não requer um grande número de linhas de codificação para gerenciar os sistemas de banco de dados. Podemos acessar e manter facilmente o banco de dados usando regras sintáticas SQL simples. Essas regras simples tornam o SQL amigável.

- Processamento de consulta de alta velocidade:
Uma grande quantidade de dados é acessada de forma rápida e eficiente a partir do banco de dados usando consultas SQL. As operações de inserção, exclusão e atualização de dados também são realizadas em menos tempo.

- Linguagem Padronizada:
O SQL segue os padrões ISO e ANSI estabelecidos há muito tempo, que oferecem uma plataforma uniforme em todo o mundo para todos os seus usuários.

- Portabilidade:
A linguagem de consulta estruturada pode ser facilmente usada em computadores desktop, laptops, tablets e até smartphones. Também pode ser usado com outros aplicativos de acordo com os requisitos do usuário.

- Linguagem interativa:
Podemos facilmente aprender e compreender a linguagem SQL. Também podemos usar essa linguagem para comunicação com o banco de dados porque é uma linguagem de consulta simples. Essa linguagem também é utilizada para receber as respostas de consultas complexas em poucos segundos.

- Mais de uma visualização de dados:
A linguagem SQL também ajuda a fazer as múltiplas visualizações da estrutura do banco de dados para os diferentes usuários do banco de dados.

### Desvantagens do SQL
São elas:

- Custo:
O custo de operação de algumas versões do SQL é alto. É por isso que alguns programadores não podem usar a linguagem de consulta estruturada.

- A interface é complexa:
Outra grande desvantagem é que a interface da linguagem de consulta estruturada é difícil, o que torna difícil para os usuários SQL usá-la e gerenciá-la.

- Controle parcial de banco de dados:
As regras de negócios estão ocultas. Portanto, os profissionais de dados e usuários que usam essa linguagem de consulta não podem ter controle total do banco de dados.

### Categorizando os tipos de comandos
Bom, vimos acima que o SQL ele tem inúmeros tipos de comandos, donde foi apresentados as mais usuais. Porém, ficaria mais fácil entender ao todo a estrutura do SQL se organizados elas nas seguintes categorias, que é o tema foco dessa seção:

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
