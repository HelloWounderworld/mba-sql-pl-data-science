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

    Esta é a seção de declaração do procedimento. Observe que, em vez de usar a palavra-chave DECLARE, como no exemplo anterior, eu uso a palavra-chave IS (ou AS) para separar o cabeçalho das declarações.

- Linha 6-15:

    Aqui está um exemplo de um loop simples. Este loop depende de uma instrução EXIT (veja a linha 11) para encerrar o loop; loops FOR e WHILE especificam a condição de término de forma diferente.

- Linha 7:

    Aqui, eu faço a chamada para a função account_balance para obter o saldo desta conta. Isso é um exemplo de chamada a um programa reutilizável dentro de outro programa reutilizável. A linha 13 demonstra a chamada de outra procedure dentro desta procedure.

- Linha 9-14:

    Aqui está um IF statement que pode ser interpretado da seguinte forma: se o saldo da conta cair abaixo de $1.000, pare de alocar fundos para cobrir contas. Caso contrário, aplique o saldo ao próximo pagamento.

## Quando as coisas dão errado:
A linguagem PL/SQL oferece um mecanismo poderoso tanto para gerar quanto para tratar erros. No procedimento a seguir, obtenho o nome e o saldo de uma conta com base em seu ID. Em seguida, verifico se o saldo está muito baixo. Se estiver, eu gero explicitamente uma exceção, o que interrompe a continuação do programa:

    1  PROCEDURE check_account (
    2     account_id_in IN accounts.id%TYPE)
    3  IS
    4     l_balance_remaining       NUMBER;
    5     l_balance_below_minimum   EXCEPTION;
    6     l_account_name            accounts.name%TYPE;
    7  BEGIN
    8     SELECT name
    9       INTO l_account_name
    10       FROM accounts
    11      WHERE id = account_id_in;
    12
    13     l_balance_remaining := account_balance (account_id_in);
    14
    15     DBMS_OUTPUT.PUT_LINE (
    16        'Balance for ' || l_account_name ||
    17         ' = ' || l_balance_remaining);
    18
    19     IF l_balance_remaining < 1000
    20     THEN
    21        RAISE l_balance_below_minimum;
    22     END IF;
    23
    24  EXCEPTION
    25     WHEN NO_DATA_FOUND
    26     THEN
    27        -- No account found for this ID
    28        log_error (...);
    29        RAISE;
    30     WHEN l_balance_below_minimum
    31     THEN
    32        log_error (...);
    33        RAISE VALUE_ERROR;
    34  END;

Vamos dar uma olhada mais detalhada nos aspectos de tratamento de erros deste código na tabela a seguir.

- Linha 5:

    Eu declaro minha própria exceção, chamada l_balance_below_minimum. A Oracle fornece um conjunto de exceções pré-definidas, como DUP_VAL_ON_INDEX, mas eu preciso de algo específico para minha aplicação, então devo defini-lo eu mesmo neste caso.

- Linha 8-11:

    Esta consulta recupera o nome da conta. Se não houver nenhuma conta para este ID, o banco de dados levanta a exceção pré-definida NO_DATA_FOUND, fazendo com que o programa pare.

- Linha 19-22:

    Se o saldo estiver muito baixo, eu levanto explicitamente minha própria exceção porque encontrei um problema grave com esta conta.

- Linha 24:

    A palavra-chave EXCEPTION indica o fim da seção executável e o início da seção de exceção, na qual os erros são tratados.

- Linha 25-28:

    Esta é a seção de tratamento de erro para a situação em que a conta não é encontrada. Se a exceção NO_DATA_FOUND foi levantada, ela é capturada aqui e o erro é registrado com o procedimento log_error. Em seguida, eu levanto novamente a mesma exceção, para que o bloco externo saiba que não houve correspondência para aquele ID de conta.

- Linha 30-33:

    Esta é a seção de tratamento de erro para a situação em que o saldo da conta ficou muito baixo (minha exceção específica do aplicativo). Se l_balance_below_minimum for levantada, ela é capturada aqui e o erro é registrado. Em seguida, eu levanto a exceção VALUE_ERROR, definida pelo sistema, para notificar o bloco externo do problema.

Há, é claro, muito mais a ser dito sobre o PL/SQL - é por isso que você tem centenas de páginas adicionais de material para estudar neste livro! Esses exemplos iniciais, no entanto, devem dar uma ideia do tipo de código que você escreverá com o PL/SQL, alguns dos seus elementos sintáticos mais importantes e a facilidade com que se pode escrever - e ler - o código PL/SQL.

## Sobre as versões PL/SQL:
Cada versão do banco de dados Oracle vem com sua própria versão correspondente do PL/SQL. À medida que você utiliza versões mais atualizadas do PL/SQL, uma ampla gama de funcionalidades estará disponível para você. Um dos maiores desafios como programadores PL/SQL é simplesmente manter-se atualizado. Precisamos constantemente nos educar sobre as novas funcionalidades em cada versão - descobrindo como usá-las e aplicá-las em nossas aplicações, e determinando quais novas técnicas são tão úteis que devemos modificar as aplicações existentes para aproveitá-las ao máximo.

Tabela 1-1: resumem os principais elementos de cada uma das versões (passadas e presentes) do PL/SQL no banco de dados. (Observação: nas primeiras versões do banco de dados, os números de versão do PL/SQL eram diferentes dos números de versão do banco de dados, mas desde o Oracle8 Database, eles têm sido idênticos.) A tabela oferece uma visão geral das novas funcionalidades disponíveis em cada versão. Após a tabela, você encontrará descrições mais detalhadas do "que há de novo" no PL/SQL na versão mais recente do Oracle, Oracle Database 12c.

Analise a Tabela do livro que estou seguindo na página 11.

## Recursos para Desenvolvedores PL/SQL:
A primeira edição deste livro foi publicada pela O'Reilly em 1995. Naquela época, "Oracle PL/SQL Programming" causou um grande impacto. Foi o primeiro livro independente (ou seja, não proveniente da Oracle) sobre PL/SQL, e atendeu a uma necessidade clara e intensamente sentida pelos desenvolvedores ao redor do mundo. Desde então, recursos como livros, ambientes de desenvolvimento, utilitários e sites para programadores PL/SQL têm proliferado. (É claro que este livro ainda é de longe o mais importante e valioso desses recursos!)

As seguintes seções descrevem de forma muito breve muitos desses recursos. Ao aproveitar ao máximo esses recursos, muitos dos quais estão disponíveis gratuitamente ou a um custo relativamente baixo, você melhorará significativamente sua experiência de desenvolvimento (e o código resultante).

### A Série PL/SQL da O'Reilly:
Ao longo dos anos, a série PL/SQL da Oracle da O'Reilly tem crescido e incluído uma longa lista de livros. Aqui, resumimos os livros atualmente disponíveis. Por favor, visite a área Oracle do site da O'Reilly para obter informações mais completas.

- Oracle PL/SQL Programming, by Steven Feuerstein with Bill Pribyl:

    O volume de 1.300 páginas que você está lendo agora. O companheiro de mesa de muitos programadores profissionais de PL/SQL, este livro foi projetado para abranger todos os recursos da linguagem PL/SQL. A versão atual abrange até o Oracle Database 11g Release 2.

- Learning Oracle PL/SQL, by Bill Pribyl with Steven Feuerstein:

    Uma introdução comparativamente suave à linguagem, ideal para novos programadores e aqueles que conhecem uma linguagem diferente de PL/SQL.

- Oracle Pl/SQL Best Practice, by Steven Feuerstein:

    Um livro relativamente curto que descreve dezenas de melhores práticas que o ajudarão a produzir código PL/SQL de alta qualidade. Ter este livro é como ter um documento de "lições aprendidas" escrito por um especialista interno em PL/SQL. A segunda edição apresenta um conteúdo completamente reescrito que ensina as melhores práticas seguindo os desafios de uma equipe de desenvolvimento que escreve código para a fictícia empresa My Flimsy Excuse.

- Oracle PL/SQL Developer's Workbook, by Steven Feuerstein with Andrew Odewahn:

    Contém uma série de perguntas e respostas destinadas a ajudar programadores PL/SQL a desenvolver e testar seu entendimento da linguagem. Este livro abrange recursos PL/SQL até o Oracle8i Database, mas é claro que a maioria desses exercícios também se aplica a versões posteriores do banco de dados.

- Oracle Built-in Packages, by Steven Feuerstein, Charles Dye, and John Beresniewicz:

    Um guia de referência para os pacotes predefinidos que a Oracle fornece com o servidor de banco de dados principal. O uso desses pacotes muitas vezes pode simplificar o difícil e domar o impossível. Este livro abrange recursos até o Oracle8 Database, mas as explicações detalhadas e os exemplos dos pacotes incluídos ainda são muito úteis nas versões posteriores.

- Oracle PL/SQL for DBAs, by Arup Nanda and Steven Feuerstein:

    A linguagem PL/SQL se torna cada vez mais importante para os DBAs da Oracle a cada nova versão do banco de dados. Existem duas razões principais para isso. Primeiro, grandes quantidades de funcionalidades do DBA são disponibilizadas por meio de uma API de pacotes PL/SQL. Para usar essa funcionalidade, você também precisa escrever e executar programas PL/SQL. Segundo, é fundamental que os DBAs tenham conhecimento prático de PL/SQL para que possam identificar problemas no código criado pelos desenvolvedores. Este livro oferece uma abundância de material que ajudará os DBAs a se familiarizarem rapidamente, para que possam aproveitar ao máximo o PL/SQL e concluir suas tarefas.

- Oracle PL/SQL Language Pocket Reference, by Steven Feuerstein, Bill Pribyl, and Chip Dawes:

    Um livro de referência rápida pequeno, mas muito útil, que pode caber no seu bolso do casaco. Ele resume a sintaxe da linguagem PL/SQL básica até o Oracle Database 11g.

- Oracle PL/SQL Built-ins Pocket Reference, y Steven Feuerstein, John Beresniewicz, and Chip Dawes:

    Outro guia útil e conciso que resume as funções e pacotes incorporados até o Oracle8 Database.

### PL/SQL na internet:
Existem também muitos recursos online para programadores PL/SQL. Esta lista se concentra principalmente nos recursos para os quais os coautores fornecem ou gerenciam o conteúdo.

- Steven Feuerstein’s PL/SQL Obsession:

    https://www.toadworld.com/

    PL/SQL Obsession é o portal online de Steven para recursos de PL/SQL, incluindo todas as suas apresentações de treinamento e código de suporte, utilitários gratuitos (alguns listados aqui), gravações em vídeo e muito mais.

- PL/SQL Challenge:

    www.plsqlchallenge.com

    O PL/SQL Challenge é um site que promove "aprendizado ativo" - em vez de ler passivamente um livro ou uma página da web, você faz testes sobre PL/SQL, SQL, lógica, Design de Banco de Dados e Oracle Application Express, testando assim o seu conhecimento.

- PL/SQL Channel:

    http://www6.plsqlchannel.com/

    O PL/SQL Channel oferece uma biblioteca com mais de 27 horas de treinamento em vídeo sobre a linguagem Oracle PL/SQL, todos gravados por Steven Feuerstein.

- Oracle Technology Network:

    https://www.oracle.com/technical-resources/

    O Quest Error Manager (QEM) é uma estrutura que o ajudará a padronizar o gerenciamento de erros em um aplicativo baseado em PL/SQL. Com o QEM, você pode registrar, levantar e relatar erros por meio de uma API que facilita para todos os desenvolvedores realizar o gerenciamento de erros da mesma maneira, com o mínimo de esforço. As informações de erro são registradas nas tabelas de instância (informações gerais sobre o erro) e contexto (pares de nome/valor específicos do aplicativo).

- oracle-developer.net:

    Mantido por Adrian Billington (que escreveu a seção no Capítulo 21 sobre funções de tabela com pipelines), este site é um recurso para desenvolvedores de banco de dados Oracle, que contém uma excelente coleção de artigos, tutoriais e utilitários. Adrian oferece tratamentos detalhados de novos recursos em cada versão do Oracle Database, repletos de exemplos, scripts de análise de desempenho e muito mais.

- ORACLE-BASE:

    https://oracle-base.com/

    ORACLE-BASE é outro recurso fantástico para os tecnólogos Oracle, construído e mantido por um único especialista em Oracle: Tim Hall. Tim é um Oracle ACE Director, membro da rede OakTable e foi escolhido como Oracle ACE do Ano de 2006 pelo Oracle Magazine Editor's Choice Awards. Ele está envolvido em trabalhos de DBA, design e desenvolvimento com bancos de dados Oracle desde 1994. Veja em http://oracle-base.com.

## Algumas dicas:
Desde 1995, quando a primeira edição deste livro foi publicada, tive a oportunidade de treinar, auxiliar e trabalhar com dezenas de milhares de desenvolvedores PL/SQL. No processo, aprendi muito e também adquiri algumas percepções sobre a forma como todos nós realizamos nosso trabalho no mundo do PL/SQL. Espero que você não ache cansativo se eu compartilhar alguns conselhos sobre como você pode trabalhar de forma mais eficaz com essa poderosa linguagem de programação.

### Não tenha tanta pressa!
Quase sempre estamos trabalhando com prazos apertados ou correndo atrás de um contratempo ou outro. Não temos tempo a perder e muito código para escrever. Então, vamos direto ao assunto, certo?

Errado. Se mergulharmos rapidamente nas profundezas da construção de código, convertendo servilmente os requisitos em centenas, milhares ou até dezenas de milhares de linhas de código, acabaremos com uma bagunça total que é quase impossível de depurar e manter. Não responda aos prazos iminentes com pânico; você tem mais chances de cumprir esses prazos se fizer um planejamento cuidadoso.

Eu recomendo fortemente que você resista a essas pressões de tempo e garanta o seguinte antes de iniciar um novo aplicativo, ou até mesmo um programa específico em um aplicativo:

- Elabore casos de teste e scripts de teste antes de escrever seu código:

    Você deve determinar como deseja verificar uma implementação bem-sucedida antes de escrever uma única linha de código. Se você fizer isso, é mais provável que acerte a interface de seus programas, pois isso o ajudará a identificar completamente o que seu programa precisa fazer.

- Estabeleça regras claras sobre como os desenvolvedores escreverão as instruções SQL no aplicativo:

    Em geral, eu recomendo que os desenvolvedores individuais não escrevam uma grande quantidade de SQL. Em vez disso, essas consultas de uma única linha e inserções e atualizações devem ser "ocultas" por trás de procedimentos e funções pré-construídas e totalmente testadas (isso é chamado de encapsulamento de dados). Esses programas podem ser otimizados, testados e mantidos de forma muito mais eficaz do que as instruções SQL (muitas delas redundantes) espalhadas por todo o código.

- Estabeleça regras claras sobre como os desenvolvedores lidarão com exceções na aplicação:

    Todos os desenvolvedores de uma equipe devem levantar, tratar e registrar erros da mesma forma. A melhor maneira de fazer isso é criar um único pacote de tratamento de erros que oculte todos os detalhes de como um registro de erros é mantido, determine como as exceções são levantadas e propagadas através de blocos aninhados e evite a codificação rígida de exceções específicas da aplicação. Certifique-se de que todos os desenvolvedores usem esse pacote e que não escrevam seu próprio código complicado, demorado e propenso a erros para tratamento de erros.

- Utilize o design top-down (também conhecido como refinamento passo a passo) para limitar a complexidade dos requisitos com os quais você deve lidar em determinado momento:

    Se você seguir essa abordagem, você perceberá que as seções executáveis dos seus módulos serão mais curtas e mais fáceis de entender, o que torna seu código mais fácil de manter e aprimorar ao longo do tempo. O uso de módulos locais ou aninhados desempenha um papel fundamental ao seguir esse princípio de design.

Essas são apenas algumas das coisas importantes a se ter em mente antes de começar a escrever todo esse código. Apenas lembre-se: no mundo do desenvolvimento de software, a pressa não apenas leva a desperdício, mas também garante uma generosa oferta de bugs e fins de semana perdidos.

### Não tenha medo de pedir ajuda!
Se você é um profissional de software, é provável que seja uma pessoa bastante inteligente. Você estudou muito, aprimorou suas habilidades e agora ganha muito bem escrevendo código. Você consegue resolver quase qualquer problema que lhe é apresentado, e isso te enche de orgulho. Infelizmente, seu sucesso também pode torná-lo egoísta, arrogante e relutante em buscar ajuda quando está confuso. Essa dinâmica é um dos aspectos mais perigosos e destrutivos do desenvolvimento de software.

O software é escrito por seres humanos; portanto, é importante reconhecer que a psicologia humana desempenha um papel fundamental no desenvolvimento de software. A seguir, apresentamos um exemplo.

Joe, o desenvolvedor sênior em uma equipe de seis pessoas, está com um problema em seu programa. Ele estuda o código por horas, cada vez mais frustrado, mas não consegue identificar a origem do bug. Ele jamais pensaria em pedir ajuda a seus colegas, pois acredita que todos têm menos experiência do que ele. No entanto, quando Joe finalmente fica sem saída, ele "desiste". Suspirando, ele pega o telefone e liga para um ramal: "Sandra, você poderia vir aqui e dar uma olhada no meu programa? Tenho um problema que simplesmente não consigo resolver." Sandra aparece e, com um rápido olhar para o programa de Joe, aponta o que deveria ter sido óbvio para ele há muito tempo. Hurra! O programa é consertado e Joe expressa gratidão, mas na verdade ele está secretamente envergonhado.

Pensamentos como "Por que eu não percebi isso?" e "Se eu tivesse passado mais cinco minutos fazendo meu próprio debug, teria encontrado o problema" passam pela mente de Joe. Isso é compreensível, mas também muito teimoso. A questão é que muitas vezes não somos capazes de identificar nossos próprios problemas porque estamos muito próximos do nosso próprio código. Às vezes, tudo o que precisamos é de uma nova perspectiva, a visão relativamente objetiva de alguém que não tem nada em jogo. Isso não tem nada a ver com senioridade, expertise ou competência.

Sugerimos fortemente que você estabeleça as seguintes diretrizes em sua organização:

- Recompense as admissões de ignorância:

    Esconder o que você não sabe sobre um aplicativo ou seu código é muito perigoso. Desenvolva uma cultura que valorize perguntas e solicitações de ajuda.

- Peça ajuda:

    Se você não conseguir identificar a origem de um bug em 30 minutos, peça imediatamente por ajuda. Você até pode estabelecer um sistema de "companheiros", onde cada pessoa é designada para ser procurada em caso de necessidade. Não permita que você mesmo (ou outros no seu grupo) passe horas batendo a cabeça em busca de respostas sem sucesso.

- Estabeleça um processo formal de revisão de código entre pares:

    Não permita que nenhum código seja enviado para QA ou produção sem ser lido e criticado (de maneira positiva e construtiva) por um ou mais desenvolvedores do seu grupo.

### Adote uma abordagem criativa, até mesmo radical:
Todos nós tendemos a cair em rotinas, em quase todos os aspectos de nossas vidas. As pessoas são criaturas de hábito: você aprende a escrever código de uma maneira; você assume certas limitações sobre um produto; você descarta soluções possíveis sem um exame sério porque você simplesmente sabe que não pode ser feito. Os desenvolvedores ficam totalmente preconceituosos em relação aos próprios programas e muitas vezes não de maneira positiva. Eles frequentemente são ouvidos dizendo coisas como:

- "Não pode rodar mais rápido do que isso; é um porco."

- "Não consigo fazê-lo funcionar do jeito que o usuário quer; isso terá que esperar pela próxima versão."

- "Se eu estivesse usando o produto X, Y ou Z, seria fácil. Mas com essas coisas, tudo é uma luta."

Mas a realidade é que seu programa quase sempre pode rodar um pouco mais rápido. E a tela, de fato, pode funcionar exatamente como o usuário deseja. E embora cada produto tenha suas limitações, pontos fortes e fraquezas, você nunca deveria ter que esperar pela próxima versão. Não é muito mais satisfatório poder dizer ao seu terapeuta que você enfrentou o problema de frente, não aceitou desculpas e criou uma solução?

Como fazer isso? Saia dos limites das suas visões fixas e dê uma nova olhada no mundo (ou talvez apenas na sua estação de trabalho). Reavalie os hábitos de programação que você desenvolveu. Seja criativo - afaste-se dos métodos tradicionais, das abordagens muitas vezes limitadas e mecânicas constantemente reforçadas em nossos ambientes de trabalho.

Experimente algo novo: faça experiências com o que possa parecer uma abordagem radicalmente diferente do normal. Você ficará surpreso com o quanto aprenderá e crescerá como programador e solucionador de problemas. Ao longo dos anos, tenho me surpreendido repetidamente com o que realmente é possível quando eu paro de dizer "Você não pode fazer isso!" e, em vez disso, apenas assinto silenciosamente e murmuro: "Agora, se eu fizer dessa maneira..."
