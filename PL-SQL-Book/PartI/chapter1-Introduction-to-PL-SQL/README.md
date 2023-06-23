# Introdução ao PL/SQL
PL/SQL significa "Procedural Language extensions to the Structured Query Language" (Extensões de Linguagem Procedural para a Linguagem de Consulta Estruturada). SQL é a linguagem agora ubíqua para consultar e atualizar - não importa o nome - bancos de dados relacionais. A Oracle Corporation introduziu o PL/SQL para superar algumas limitações do SQL e fornecer uma solução de programação mais completa para aqueles que buscavam construir aplicativos críticos para o sucesso das missões para serem executados no banco de dados Oracle. Este capítulo apresenta o PL/SQL, suas origens e suas várias versões. Ele oferece um resumo rápido do PL/SQL na versão mais recente do Oracle, Oracle Database 12c. Por fim, ele fornece um guia para recursos adicionais para desenvolvedores PL/SQL e algumas palavras de conselho.

## O que é PL/SQL?:
A linguagem PL/SQL da Oracle possui várias características distintivas:

- É uma linguagem altamente estruturada, legível e acessível:

    Se você é novo na programação, o PL/SQL é um ótimo lugar para começar. Você descobrirá que é uma linguagem fácil de aprender e rica em palavras-chave e estrutura que expressam claramente a intenção do seu código. Se você possui experiência em outras linguagens de programação, se adaptará facilmente à nova sintaxe.

- É uma linguagem padrão e portátil para o desenvolvimento Oracle:

    Se você escrever um procedimento ou função PL/SQL para ser executado no banco de dados Oracle em seu laptop, poderá mover esse mesmo procedimento para um banco de dados na rede corporativa e executá-lo lá sem nenhuma alteração (supondo a compatibilidade das versões do Oracle, é claro!). "Escreva uma vez, execute em qualquer lugar" foi o lema do PL/SQL muito antes do surgimento do Java. No entanto, para o PL/SQL, "em qualquer lugar" significa "em qualquer lugar onde haja um banco de dados Oracle".

- É uma linguagem incorporada:

    O PL/SQL não foi projetado para ser usado como uma linguagem independente, mas sim para ser invocado a partir de um ambiente hospedeiro. Portanto, por exemplo, você pode executar programas PL/SQL de dentro do banco de dados (por meio, digamos, da interface SQL*Plus). Alternativamente, você pode definir e executar programas PL/SQL de dentro de um formulário ou relatório do Oracle Developer (essa abordagem é chamada de PL/SQL no lado do cliente). No entanto, você não pode criar um executável PL/SQL que seja executado por si só.

- É uma linguagem de banco de dados de alto desempenho e altamente integrada:

    Hoje em dia, você tem várias opções quando se trata de escrever software para ser executado no banco de dados Oracle. Você pode usar Java e JDBC; você pode usar Visual Basic e ODBC; você pode optar por Delphi, C++, e assim por diante. No entanto, você descobrirá que é mais fácil escrever código altamente eficiente para acessar o banco de dados Oracle em PL/SQL do que em qualquer outra linguagem. Em particular, a Oracle oferece aprimoramentos específicos do PL/SQL, como o comando FORALL, que pode melhorar o desempenho do banco de dados em uma ordem de grandeza ou mais.

## As origens de PL/SQL:
A Oracle Corporation tem uma história de liderança na indústria de software ao fornecer abordagens declarativas e não procedurais para o design de bancos de dados e aplicativos. A tecnologia do servidor Oracle está entre os bancos de dados relacionais mais avançados, poderosos e estáveis do mundo. Suas ferramentas de desenvolvimento de aplicativos, como o Oracle Forms, oferecem altos níveis de produtividade, baseando-se amplamente em uma abordagem de "pintar sua tela", na qual capacidades padrão extensivas permitem que os desenvolvedores evitem esforços intensos de programação personalizada.

## Os Primeiros Anos do PL/SQL:
Nos primeiros anos da Oracle, a abordagem declarativa do SQL, combinada com sua revolucionária tecnologia relacional, era suficiente para satisfazer os desenvolvedores. Mas à medida que a indústria amadurecia, as expectativas aumentavam e os requisitos se tornavam mais rigorosos. Os desenvolvedores precisavam entender a fundo os produtos. Eles precisavam incorporar fórmulas complicadas, exceções e regras em seus formulários e scripts de banco de dados.

Em 1988, a Oracle Corporation lançou a versão 6 do Oracle, um avanço importante em sua tecnologia de banco de dados relacional. Um componente-chave dessa versão era a chamada opção procedural, ou PL/SQL. Aproximadamente na mesma época, a Oracle lançou a tão esperada atualização para o SQLForms versão 2.3 (o nome original do produto agora conhecido como Oracle Forms ou Forms Developer). O SQLForms v3 incorporou o mecanismo PL/SQL pela primeira vez no lado das ferramentas, permitindo que os desenvolvedores codificassem sua lógica procedural de maneira natural e direta.

Essa primeira versão do PL/SQL era muito limitada em suas capacidades. No lado do servidor, você só podia usar o PL/SQL para construir scripts de processamento em lote, compostos por instruções procedurais e SQL. Você não conseguia criar um aplicativo modular ou armazenar regras de negócio no servidor. No lado do cliente, o SQL*Forms v3.0 permitia que você criasse procedimentos e funções, embora o suporte a funções não fosse documentado e, portanto, não fossem utilizadas por muitos desenvolvedores por anos. Além disso, essa versão do PL/SQL não implementava suporte a matrizes e não podia interagir com o sistema operacional (para entrada ou saída). Estava longe de ser uma linguagem de programação completa.

Mas, apesar de todas as suas limitações, o PL/SQL foi recebido calorosamente, até mesmo entusiasticamente, pela comunidade de desenvolvedores. A necessidade de codificar uma simples instrução IF dentro do SQL*Forms era forte. A demanda por processamento em lote de várias instruções SQL era avassaladora.

O que poucos desenvolvedores perceberam na época era que a motivação original e a visão por trás do PL/SQL iam além do desejo de controle programático em produtos como o SQL*Forms. Logo no início do ciclo de vida do banco de dados e das ferramentas da Oracle, a Oracle Corporation reconheceu duas fraquezas fundamentais em sua arquitetura: falta de portabilidade e problemas com autoridade de execução.

## Aplicação de Portabilidade Melhorada:
A preocupação com a portabilidade pode parecer estranha para aqueles de nós familiarizados com as estratégias de marketing e técnicas da Oracle Corporation. Uma das características marcantes da solução da Oracle desde o início dos anos 1980 era sua portabilidade. Na época em que o PL/SQL surgiu, o banco de dados baseado em C era executado em muitos sistemas operacionais e plataformas de hardware diferentes. O SQLPlus e o SQLForms se adaptavam facilmente a várias configurações de terminais. No entanto, apesar dessa cobertura, ainda havia muitos aplicativos que precisavam do controle mais sofisticado e granular oferecido por linguagens hospedeiras como COBOL, C e FORTRAN. Assim que um desenvolvedor saía das ferramentas Oracle neutras em termos de portabilidade, o aplicativo resultante deixava de ser portátil.

A linguagem PL/SQL foi (e continua sendo) projetada para ampliar a gama de requisitos de aplicativos que podem ser tratados completamente em ferramentas de programação independentes do sistema operacional. Hoje, o Java e outras linguagens de programação oferecem portabilidade semelhante. No entanto, o PL/SQL se destaca como um pioneiro nessa área e, é claro, continua permitindo que os desenvolvedores escrevam código de aplicativo altamente portátil.

## Melhorada a Autoridade de Execução e Integridade de Transação:
Uma questão ainda mais fundamental do que a portabilidade era a autoridade de execução. O banco de dados e a linguagem SQL permitem controlar rigorosamente o acesso e as alterações em uma tabela de banco de dados específica. Por exemplo, com o comando GRANT, você pode garantir que apenas determinadas funções e usuários possam realizar uma atualização em uma determinada tabela. No entanto, esse comando GRANT não pode garantir que um usuário faça a sequência correta de alterações em uma ou mais tabelas que são comumente necessárias na maioria das transações comerciais.

A linguagem PL/SQL oferece um controle rígido e gerenciamento sobre transações lógicas. Uma forma como o PL/SQL faz isso é por meio da implementação da autoridade de execução. Em vez de conceder a uma função ou usuário a autoridade para atualizar uma tabela, você concede privilégios apenas para executar um procedimento, que controla e fornece acesso às estruturas de dados subjacentes. O procedimento pertence a um esquema diferente do banco de dados Oracle (o "definidor" do programa), que, por sua vez, recebe os privilégios de atualização reais nessas tabelas necessárias para realizar a transação. O procedimento, portanto, se torna o "guardião" da transação. A única maneira que um programa (seja um aplicativo Oracle Forms ou um executável Pro*C) pode executar a transferência é por meio do procedimento. Dessa forma, a integridade geral da transação do aplicativo é garantida.

A partir do Oracle8i Database, a Oracle adicionou considerável flexibilidade ao modelo de autoridade de execução do PL/SQL ao oferecer a cláusula AUTHID. Com AUTHID, você pode continuar executando seus programas no modelo de direitos do definidor descrito anteriormente, ou pode escolher AUTHID CURRENT_USER (direitos do invocador), caso em que os programas são executados sob a autoridade do esquema invocador (atual). Os direitos do invocador são apenas um exemplo de como o PL/SQL amadureceu e se tornou mais flexível ao longo dos anos.

## Humildes Origens, Melhoria Constante:
Tão poderoso quanto o SQL é, ele simplesmente não oferece a flexibilidade e o poder que os desenvolvedores precisam para criar aplicativos completos. A linguagem PL/SQL da Oracle garante que possamos permanecer inteiramente dentro do ambiente Oracle independente do sistema operacional e ainda escrever aplicativos altamente eficientes que atendam aos requisitos de nossos usuários.

O PL/SQL percorreu um longo caminho desde suas humildes origens. Com o PL/SQL 1.0, era comum os desenvolvedores terem que dizer a seus gerentes: "Você não pode fazer isso com o PL/SQL". Hoje, essa afirmação mudou de fato para desculpa. Se você se deparar com um requisito e se encontrar dizendo: "Não há como fazer isso", por favor, não repita isso ao seu gerente. Em vez disso, aprofunde-se na linguagem ou explore a variedade de pacotes PL/SQL oferecidos pela Oracle. É extremamente provável que o PL/SQL hoje permita que você faça praticamente tudo o que você precisa fazer.

Ao longo dos anos, a Oracle Corporation demonstrou seu compromisso com o PL/SQL, sua linguagem de programação proprietária líder. Com cada nova versão do banco de dados, a Oracle também fez melhorias constantes e fundamentais na própria linguagem PL/SQL. Ela adicionou uma grande variedade de pacotes fornecidos (ou embutidos) que estendem a linguagem PL/SQL de várias maneiras e direções. Ela introduziu capacidades orientadas a objetos, implementou uma variedade de estruturas de dados semelhantes a arrays, aprimorou o compilador para otimizar nosso código e fornecer avisos sobre possíveis problemas de qualidade e desempenho, e, em geral, melhorou a abrangência e a profundidade da linguagem.

A próxima seção apresenta alguns exemplos de programas PL/SQL que irão familiarizá-lo com os conceitos básicos da programação PL/SQL.

## Então isto é PL/SQL:
Se você é completamente novo em programação ou em trabalhar com PL/SQL (ou mesmo SQL, para o caso), aprender PL/SQL pode parecer uma perspectiva intimidadora. Se este for o caso, não se preocupe! Tenho confiança de que você encontrará isso mais fácil do que imagina. Existem duas razões para o meu otimismo:

- As linguagens de programação em geral não são tão difíceis de aprender, pelo menos em comparação com uma segunda ou terceira língua humana. A razão disso é simplesmente que os computadores não são particularmente inteligentes (eles "pensam" - realizam operações - rapidamente, mas não de forma criativa). Devemos confiar em uma sintaxe muito rígida para dizer ao computador o que queremos que ele faça. Portanto, a linguagem resultante também é rígida (sem exceções!) e, portanto, mais fácil para nós aprendermos.

- PL/SQL realmente é uma linguagem fácil, comparada a outras linguagens de programação. Ela se baseia em um design altamente estruturado em forma de "bloco", com diferentes seções, todas identificadas por palavras-chave explícitas e autoexplicativas.

Vamos dar uma olhada em alguns exemplos que demonstram alguns elementos-chave da estrutura e funcionalidade do PL/SQL.

## Integração com SQL:
Um dos aspectos mais importantes do PL/SQL é sua integração total com o SQL. Você não precisa depender de nenhum software intermediário, como ODBC (Open Database Connectivity) ou JDBC (Java Database Connectivity), para executar instruções SQL em seus programas PL/SQL. Em vez disso, basta inserir o comando UPDATE ou SELECT em seu código, como mostrado aqui:

    1  DECLARE
    2     l_book_count INTEGER;
    3
    4  BEGIN
    5     SELECT COUNT(*)
    6       INTO l_book_count
    7       FROM books
    8      WHERE author LIKE '%FEUERSTEIN, STEVEN%';
    9
    10     DBMS_OUTPUT.PUT_LINE (
    11        'Steven has written (or co-written) ' ||
    12         l_book_count ||
    13         ' books.');
    14
    15     -- Oh, and I changed my name, so...
    16     UPDATE books
    17        SET author = REPLACE (author, 'STEVEN', 'STEPHEN')
    18      WHERE author LIKE '%FEUERSTEIN, STEVEN%';
    19  END;

Vamos dar uma olhada mais detalhada neste código na tabela a seguir.

- Linha 1-3:

    Esta é a seção de declaração deste chamado bloco PL/SQL "anônimo", no qual declaro uma variável inteira para armazenar o número de livros que eu escrevi ou coescrevi. (Falarei muito mais sobre a estrutura do bloco PL/SQL no Capítulo 3.)

- Linha 4:

    A palavra-chave BEGIN indica o início da minha seção de execução - o código que será executado quando eu passar este bloco para o SQL*Plus.

- Linha 5-8:

    Eu executo uma consulta para determinar o número total de livros que eu escrevi ou coescrevi. A linha 6 é de especial interesse: a cláusula INTO mostrada aqui na verdade não faz parte da instrução SQL, mas serve como ponte entre o banco de dados e as variáveis locais do PL/SQL.

- Linha 10-13:

    Eu uso o procedimento embutido DBMS_OUTPUT.PUT_LINE (ou seja, um procedimento no pacote DBMS_OUTPUT fornecido pela Oracle) para exibir o número de livros.

- Linha 15:

    This single-line comment explains the purpose of the UPDATE.

- Linha 16-18:

    Decidi alterar a grafia do meu primeiro nome para "Stephen", então faço uma atualização na tabela de livros. Aproveito a função REPLACE incorporada para localizar todas as ocorrências de "STEVEN" e substituí-las por "STEPHEN".

## Controle e Lógica Condicional:
PL/SQL oferece uma variedade completa de instruções que nos permitem controlar de forma muito precisa quais linhas de nossos programas são executadas. Essas instruções incluem:

- Declarações IF e CASE:

    Essas implementam lógica condicional; por exemplo, "Se o número de páginas de um livro for maior que 1.000, então..."

- Um conjunto completo de controles de repetição ou iteração:

    Isso inclui o loop FOR, o loop WHILE e o loop simples.

- A declaração GOTO:

    Sim, o PL/SQL até oferece um GOTO que permite que você faça um desvio incondicional de uma parte do seu programa para outra. Isso não significa, no entanto, que você deva realmente usá-lo.

Aqui está um procedimento (um bloco de código reutilizável que pode ser chamado pelo nome) que demonstra algumas dessas características:

    1  PROCEDURE pay_out_balance (
    2     account_id_in IN accounts.id%TYPE)
    3  IS
    4     l_balance_remaining NUMBER;
    5  BEGIN
    6     LOOP
    7        l_balance_remaining := account_balance (account_id_in);
    8
    9        IF l_balance_remaining < 1000
    10        THEN
    11           EXIT;
    12        ELSE
    13           apply_balance (account_id_in, l_balance_remaining);
    14        END IF;
    15     END LOOP;
    16  END pay_out_balance;

Vamos dar uma olhada mais detalhada neste código na tabela a seguir.

- Linha 1-2:

    Este é o cabeçalho de um procedimento que paga o saldo de uma conta para cobrir contas pendentes. A linha 2 é a lista de parâmetros do procedimento, neste caso consistindo de um único valor de entrada (o número de identificação da conta).

- Linha 3-4:
