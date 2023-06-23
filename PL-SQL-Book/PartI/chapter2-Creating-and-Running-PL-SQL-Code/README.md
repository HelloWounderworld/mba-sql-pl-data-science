# Criando e Rondando Aplicações PL/SQL
Mesmo que nunca dêem uma segunda pensada a tarefas como design de sistema ou testes unitários, todos os programadores PL/SQL devem estar familiarizados com algumas tarefas operacionais básicas:

- Navegando no banco de dados

- Criando e editando código-fonte PL/SQL

- Compilando o código-fonte PL/SQL e corrigindo quaisquer erros de código (e, opcionalmente, avisos) indicados pelo compilador

- Executando o programa compilado a partir de algum ambiente

- Examinando os resultados da execução do programa (saída na tela, alterações em tabelas, etc.)

Ao contrário de linguagens independentes como C, o PL/SQL é hospedado dentro de um ambiente de execução Oracle (sendo uma linguagem incorporada), então existem algumas nuances inesperadas em todas essas tarefas: algumas são surpresas agradáveis, outras são consternações. Este capítulo irá mostrar como realizar essas tarefas no nível mais básico (usando o SQL*Plus), com um breve passeio pelas nuances incluídas. Ele conclui com alguns exemplos rápidos de chamadas ao PL/SQL de dentro de vários ambientes de programação comuns, como PHP e C. Para obter informações mais detalhadas sobre compilação e outras tarefas mais avançadas, consulte o Capítulo 20.

## Navegando no Banco de Dados:
Todos que optam por escrever programas PL/SQL o fazem para trabalhar com o conteúdo de um banco de dados Oracle. Portanto, não é surpresa que você precise saber como "navegar" no banco de dados Oracle onde seu código será executado. Você vai querer examinar as estruturas de dados (tabelas, colunas, sequências, tipos definidos pelo usuário, etc.) no banco de dados, bem como as assinaturas de quaisquer programas armazenados existentes que você irá invocar.

Você provavelmente também precisará saber algo sobre o conteúdo real (colunas, restrições, etc.) das tabelas.

Existem duas abordagens distintas que você pode adotar para navegar no banco de dados:

- Use um ambiente de desenvolvimento integrado (IDE, do inglês integrated development environment), um nome chique para um editor sofisticado, como Toad, SQL Developer, PL/SQL Developer ou SQL Navigator. Todos eles oferecem navegadores visuais que suportam navegação por ponto e clique.

- Execute scripts em um ambiente de linha de comando como o SQL*Plus, que consulta os conteúdos das visualizações do dicionário de dados como ALL_OBJECTS ou USER_OBJECTS (demonstrado posteriormente neste capítulo).

Eu recomendo fortemente que você utilize um ambiente de desenvolvimento integrado (IDE) gráfico. Se você tem experiência suficiente com o Oracle, pode estar viciado e ser bastante produtivo com seus scripts. Mas, para o restante de nós, uma interface gráfica é muito mais fácil de trabalhar e entender - e muito mais produtiva - do que os scripts.

O Capítulo 20 também oferece exemplos de uso de várias visualizações do dicionário de dados para trabalhar com sua base de código PL/SQL.

## Criando e editando o código recurso:
Hoje em dia, os programadores têm muitas opções de editores de código, desde o editor de texto mais simples até os ambientes de desenvolvimento mais exóticos. E eles fazem escolhas muito diferentes. Um dos autores deste livro, Steven Feuerstein, é bastante viciado no IDE Toad. Ele é um usuário muito típico, familiarizado talvez apenas com 10% de toda a funcionalidade e botões, mas dependendo muito desses recursos. Bill Pribyl, por outro lado, descreve a si mesmo como "algo peculiar, pois gosto de usar um editor de texto simples para escrever programas PL/SQL. Minha única concessão é que ele recua automaticamente o código conforme digito e exibe palavras-chave, comentários, literais e variáveis em cores diferentes".

Os editores mais sofisticados fazem muito mais do que recuar o código e colorir palavras-chave; eles também oferecem depuradores gráficos, realizam preenchimento automático de palavras-chave, mostram uma prévia dos subprogramas dos pacotes à medida que você digita seus nomes, exibem parâmetros de subprogramas e destacam a linha e a coluna específicas onde o compilador relatou um erro. Alguns editores também possuem recursos de "hiperlink" que permitem navegar rapidamente para a declaração de uma variável ou subprograma. No entanto, a necessidade da maioria desses recursos é comum a muitas linguagens compiladas.

O que é único sobre o PL/SQL é o fato de que o código-fonte dos programas armazenados deve ser carregado no banco de dados antes de poder ser compilado e executado. Essa cópia no banco de dados geralmente pode ser recuperada por um programador que possui permissões suficientes. Imediatamente, podemos reconhecer uma série de questões relacionadas ao gerenciamento de código, incluindo:

- Como e onde um programador encontra a "cópia original" de um programa armazenado?

- Ela fica armazenada no disco ou apenas no banco de dados?

- Como e com que frequência fazemos backups?

- Como gerenciamos o acesso de vários desenvolvedores ao código? Ou seja, usamos um sistema de controle de versão de software?

Essas perguntas devem ser respondidas antes de iniciar o desenvolvimento de um aplicativo, preferencialmente, fazendo escolhas sobre quais ferramentas de software farão esse trabalho para você. Embora não haja um único conjunto de ferramentas ou processos que funcionem melhor para todas as equipes de desenvolvimento, posso dizer que sempre armazeno o código fonte "original" em arquivos - sugiro fortemente que você não use o SGBD como repositório de código.

Na próxima seção, vou demonstrar como você pode usar o SQL*Plus para realizar muitas tarefas básicas para o desenvolvimento do PL/SQL. Essas mesmas tarefas podem ser concluídas em seu IDE.

## SQL*PLUS
O avô dos front-ends Oracle, o SQL*Plus da Oracle, fornece um interpretador de linha de comando tanto para SQL quanto para PL/SQL. Ou seja, ele aceita comandos do usuário, os envia para o servidor Oracle e exibe os resultados.

Muitas vezes criticado por sua interface de usuário, o SQLPlus é uma das minhas ferramentas favoritas do Oracle. Na verdade, gosto da falta de recursos extravagantes e menus. Irônicamente, quando comecei a usar o Oracle (por volta de 1986), o antecessor desse produto tinha um nome ousado: UFI - User-Friendly Interface (Interface Amigável ao Usuário). Duas décadas depois, mesmo a versão mais recente do SQLPlus ainda não é provável que ganhe prêmios de facilidade de uso, mas pelo menos não trava com frequência.

Ao longo dos anos, a Oracle ofereceu diferentes versões do SQL*Plus, incluindo:

- Como um programa de console:

    Este é um programa que é executado a partir de um shell ou prompt de comando (um ambiente que às vezes é chamado de console).

- Como um programa pseudo-GUI:

    Esta forma do SQL*Plus está disponível apenas no Microsoft Windows. Eu a chamo de "pseudo-GUI" porque se parece bastante com o programa do console, mas com fontes bitmaps; poucos outros recursos a distinguem do programa do console. Cuidado: a Oracle tem ameaçado descontinuar este produto há anos, e ele não foi realmente atualizado desde o Oracle8i Database.

- Através do iSQL*Plus:

    Este programa é executado a partir de um navegador da web conectado a uma máquina intermediária que executa o servidor HTTP da Oracle e o servidor iSQL*Plus.

A partir do Oracle Database 11g, a Oracle disponibiliza apenas o programa de console (sqlplus.exe).

Normalmente, eu prefiro o programa de console porque:

- Ele tende a desenhar a tela mais rapidamente, o que pode ser significativo para consultas com muita saída.

- Ele possui um histórico de linha de comando mais completo (pelo menos nas plataformas Microsoft Windows).

- Ele possui uma maneira muito mais fácil de alterar características visuais, como fonte, cor e tamanho do buffer de rolagem.

- Ele está disponível praticamente em todos os lugares onde o servidor Oracle ou as ferramentas do cliente estão instaladas.

### Começando com SQL*PLUS:
Para iniciar a versão console do SQL*Plus, você pode simplesmente digitar "sqlplus" no prompt do sistema operacional (indicado por "OS>"):

    OS> sqlplus

Isso funciona tanto para sistemas operacionais baseados em Unix quanto para sistemas operacionais Microsoft. O SQL*Plus deve exibir um banner de inicialização e, em seguida, solicitar um nome de usuário e senha:

    SQL*Plus: Release 11.1.0.6.0 - Production on Fri Nov 7 10:28:26 2008

    Copyright (c) 1982, 2007, Oracle.  All rights reserved.

    Enter user-name: bob
    Enter password: swordfish

    Connected to:
    Oracle Database 11g Enterprise Edition Release 11.1.0.6.0 - 64bit

    SQL>

Ver o prompt "SQL>" é um sinal de que a instalação está configurada corretamente. (A senha não será exibida na tela.)

Você também pode iniciar o SQL*Plus com o nome de usuário e senha na linha de comando:

    OS> sqlplus bob/swordfish

Eu não recomendo isso, porque alguns sistemas operacionais fornecem uma maneira para outros usuários verem seus argumentos de linha de comando, o que lhes permitiria ler sua senha. Em sistemas multiusuários, você pode, em vez disso, usar a opção /NOLOG para iniciar o SQL*Plus sem se conectar ao banco de dados e, em seguida, fornecer o nome de usuário e senha por meio do comando CONNECT:

    OS> sqlplus /nolog

    SQL*Plus: Release 11.1.0.6.0 - Production on Fri Nov 7 10:28:26 2008

    Copyright (c) 1982, 2007, Oracle.  All rights reserved.
    SQL> CONNECT bob/swordfish
    SQL> Connected.

Se o computador em que você está executando o SQLPlus também possui uma instalação Oracle Net2 devidamente configurada, e você foi autorizado pelo administrador do banco de dados a se conectar a bancos de dados remotos (ou seja, servidores de banco de dados em outros computadores), você pode se conectar a esses outros bancos de dados a partir do SQLPlus. Para fazer isso, é necessário conhecer um identificador de conexão Oracle Net (também conhecido como nome de serviço) que você deve fornecer juntamente com seu nome de usuário e senha. Um identificador de conexão pode ser assim:

    hqhr.WORLD

Para usar esse identificador, você pode acrescentá-lo ao seu nome de usuário e senha, separados por um sinal de arroba (@):

    SQL> CONNECT bob/swordfish@hqhr.WORLD
    SQL> Connected.

Ao iniciar a versão pseudo-GUI do SQL*Plus, fornecer suas credenciais é simples, embora ele chame o identificador de conexão de "cadeia do host". Se você deseja se conectar a um servidor de banco de dados em execução na máquina local, basta deixar o campo "Cadeia do Host" em branco.

Depois de iniciar o SQL*Plus, você pode realizar várias tarefas. Aqui estão algumas das mais comuns:

- Executar uma instrução SQL.

- Compilar e armazenar um programa PL/SQL no banco de dados.

- Executar um programa PL/SQL.

- Executar um comando específico do SQL*Plus.

- Executar um script que contenha uma combinação das tarefas anteriores.

Vamos dar uma olhada nessas tarefas nas seções seguintes.

### Executando uma declaração SQL:
O terminador padrão no SQL*Plus para declarações SQL é o ponto e vírgula (;), mas você pode alterar esse caractere terminador.

Na versão console do SQL*Plus, a consulta:

    SELECT isbn, author, title FROM books;

produz uma saída semelhante à mostrada na Figura 2-1.

### Executando um programa PL/SQL:
Então, aqui vamos nós (por favor, rufem os tambores). Vamos digitar um pequeno programa PL/SQL no SQL*Plus:

    SQL> BEGIN
        2     DBMS_OUTPUT.PUT_LINE('Hey look, ma!');
        3  END;
        4  /

    PL/SQL procedure successfully completed.

    SQL>

Ops. Embora tenha sido concluído com sucesso, esse programa específico deveria invocar o programa interno do PL/SQL que ecoa algum texto de volta. O comportamento um tanto irritante do SQLPlus é suprimir essa saída por padrão. Para exibi-la corretamente, você precisa usar um comando do SQLPlus para ativar o SERVEROUTPUT:

    SQL> SET SERVEROUTPUT ON
    SQL> BEGIN
        2     DBMS_OUTPUT.PUT_LINE('Hey look, Ma!');
        3  END;
        4  /
    Hey look, Ma!

    PL/SQL procedure successfully completed.

    SQL>

Normalmente, eu coloco o comando SERVEROUTPUT no meu arquivo de inicialização (consulte "Carregando seu próprio ambiente personalizado automaticamente na inicialização" na página 35), fazendo com que ele seja ativado até que uma das seguintes situações ocorra:

- Você se desconecta, faz logoff ou encerra sua sessão.

- Você define explicitamente SERVEROUTPUT como OFF.

- O banco de dados Oracle descarta o estado da sessão, seja por sua solicitação ou devido a um erro de compilação (consulte "Recompilando unidades de programa inválidas" na página 773).

- Nas versões do Oracle até o Oracle9i Database Release 2, você emite um novo comando CONNECT; nas versões subsequentes, o SQL*Plus executa automaticamente seu arquivo de inicialização após cada CONNECT.

Quando você insere declarações SQL ou PL/SQL no SQL*Plus do console ou pseudo-GUI, o programa atribui um número a cada linha após a primeira. Existem dois benefícios para os números de linha: primeiro, eles ajudam você a designar qual linha editar com o editor de linha incorporado (que você pode usar algum dia); e segundo, se o banco de dados detectar um erro em seu código, geralmente ele reportará o erro acompanhado de um número de linha. Você terá muitas oportunidades para ver esse comportamento em ação.

Para informar ao SQL*Plus que você terminou de inserir uma declaração PL/SQL, geralmente é necessário incluir uma barra invertida (/) no final (veja a linha 4 no exemplo anterior). Embora em sua maioria inofensiva, a barra invertida possui algumas características importantes:

- O significado da barra invertida é "executar a declaração mais recentemente inserida", independentemente de a declaração ser SQL ou PL/SQL.

- A barra invertida é um comando exclusivo do SQL*Plus; não faz parte da linguagem PL/SQL, nem faz parte do SQL.

- Ela deve aparecer em uma linha separada; nenhum outro comando pode ser incluído na mesma linha.

- Na maioria das versões do SQLPlus anteriores ao Oracle9i Database, se você acidentalmente preceder a barra invertida com espaços, ela não funcionará! A partir do Oracle9i Database, o SQLPlus convenientemente ignora os espaços iniciais. Os espaços finais não importam em nenhuma versão.

Como recurso de conveniência, o SQL*Plus oferece aos usuários do PL/SQL um comando EXECUTE, que evita a digitação de BEGIN, END e da barra invertida. Portanto, o seguinte é equivalente ao pequeno programa que executei anteriormente:

    SQL> EXECUTE DBMS_OUTPUT.PUT_LINE('Hey look, Ma!')

Um ponto e vírgula final é opcional, mas eu prefiro omiti-lo. Como acontece com a maioria dos comandos do SQL*Plus, EXECUTE pode ser abreviado e é insensível a maiúsculas e minúsculas, então a maioria do uso interativo fica reduzida a:

    SQL> EXEC dbms_output.put_line('Hey look, Ma!')

### Executando um Script:
Quase qualquer declaração que funcione interativamente no SQLPlus pode ser armazenada em um arquivo para execução repetida. A maneira mais fácil de executar esse script é usar o comando @ do SQLPlus. Por exemplo, isso executa todos os comandos no arquivo abc.pkg:

    SQL> @abc.pkg

O arquivo deve estar localizado no meu diretório atual (ou em algum lugar do SQLPATH).

Se você preferir palavras em vez de arrobas, pode usar o comando equivalente START:

    SQL> START abc.pkg

e você obterá resultados idênticos. De qualquer forma, esse comando faz com que o SQL*Plus execute as seguintes ações:

- Abra o arquivo chamado abc.pkg.

- Tente executar sequencialmente todas as declarações SQL, PL/SQL e SQL*Plus no arquivo.

- Ao concluir, feche o arquivo e retorne ao prompt do SQLPlus (a menos que o arquivo invoque a instrução EXIT, o que fará com que o SQLPlus seja encerrado).
