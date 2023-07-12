# Criando e Rondando Aplicações PL/SQL
Mesmo que nunca dêem uma segunda pensada as tarefas como design de sistema ou testes unitários, todos os programadores PL/SQL devem estar familiarizados com algumas tarefas operacionais básicas:

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
        2     DBMS_OUTPUT.PUT_LINE('Hey look, man!');
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

OBS: Na minha revisão de estudos aqui, em vez de usar o "SET SERVEROUTPUT ON" usei "SET SERVEROUT ON". No exemplo acima, ambas tiveram a mesma funcionalidade com as mesmas respostas. Porém, aí veio a pergunta que não quer calar. Qual a diferença entre "SET SERVEROUTPUT" e o "SET SERVEROUT"? A explicação para isso é o seguinte

- SET SERVEROUT ON/OFF: Esta declaração é usada para controlar a exibição de mensagens geradas pelo comando DBMS_OUTPUT.PUT_LINE. Quando SET SERVEROUT ON é usado, as mensagens do DBMS_OUTPUT.PUT_LINE serão exibidas no ambiente em que o programa está sendo executado (por exemplo, SQL*Plus). Já quando SET SERVEROUT OFF é usado, as mensagens não serão exibidas. Por padrão, SET SERVEROUT OFF é definido.

- SET SERVEROUTPUT ON/OFF: Esta declaração é usada para controlar a exibição de resultados de comandos SQL durante a execução de um programa PL/SQL. Quando SET SERVEROUTPUT ON é usado, os resultados dos comandos SQL serão exibidos no ambiente em que o programa está sendo executado. Quando SET SERVEROUTPUT OFF é usado, os resultados não serão exibidos. Por padrão, SET SERVEROUTPUT OFF é definido.

Em resumo, "SET SERVEROUT ON/OFF" controla a exibição de mensagens geradas pelo "DBMS_OUTPUT.PUT_LINE", enquanto "SET SERVEROUTPUT ON/OFF" controla a exibição de resultados de comandos SQL.

Normalmente, eu coloco o comando SERVEROUTPUT no meu arquivo de inicialização (consulte "Carregando seu próprio ambiente personalizado automaticamente na inicialização" na página 35), fazendo com que ele seja ativado até que uma das seguintes situações ocorra:

- Você se desconecta, faz logoff ou encerra sua sessão.

- Você define explicitamente SERVEROUTPUT como OFF.

- O banco de dados Oracle descarta o estado da sessão, seja por sua solicitação ou devido a um erro de compilação (consulte "Recompilando unidades de programa inválidas" na página 773).

- Nas versões do Oracle até o Oracle9i Database Release 2, você emite um novo comando CONNECT; nas versões subsequentes, o SQL*Plus executa automaticamente seu arquivo de inicialização após cada CONNECT.

Quando você insere declarações SQL ou PL/SQL no SQL*Plus do console ou pseudo-GUI, o programa atribui um número a cada linha após a primeira. Existem dois benefícios para os números de linha: primeiro, eles ajudam você a designar qual linha editar com o editor de linha incorporado (que você pode usar algum dia); e segundo, se o banco de dados detectar um erro em seu código, geralmente ele reportará o erro acompanhado de um número de linha. Você terá muitas oportunidades para ver esse comportamento em ação.

Para informar ao SQL*Plus que você terminou de inserir uma declaração PL/SQL, geralmente é necessário incluir uma barra invertida (/) no final (veja a linha 4 no exemplo anterior). Embora em sua maioria inofensiva, a barra invertida possui algumas características importantes: (Importante!)

- O significado da barra invertida é "executar a declaração mais recentemente inserida", independentemente de a declaração ser SQL ou PL/SQL.

- A barra invertida é um comando exclusivo do SQL*Plus; não faz parte da linguagem PL/SQL, nem faz parte do SQL.

- Ela deve aparecer em uma linha separada; nenhum outro comando pode ser incluído na mesma linha.

- Na maioria das versões do SQLPlus anteriores ao Oracle9i Database, se você acidentalmente preceder a barra invertida com espaços, ela não funcionará! A partir do Oracle9i Database, o SQLPlus convenientemente ignora os espaços iniciais. Os espaços finais não importam em nenhuma versão.

Como recurso de conveniência, o SQL*Plus oferece aos usuários do PL/SQL um comando EXECUTE, que evita a digitação de BEGIN, END e da barra invertida. Portanto, o seguinte é equivalente ao pequeno programa que executei anteriormente: (Importante!)

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

Por exemplo: (Importante!)

    SQL> @abc.pkg

    Package created.

    Package body created.

    SQL>

O comportamento padrão é exibir apenas a saída das declarações individuais na tela; se você deseja ver o código-fonte original do arquivo, use o comando SQL*Plus SET ECHO ON.

No meu exemplo, usei uma extensão de arquivo .pkg. Se eu omitir a extensão, isso é o que acontece:

    SQL> @abc
    SP2-0310: unable to open file "abc.sql"

Como você pode ver, a extensão de arquivo padrão é sql. A propósito, o "SP2-0310" é o número de erro fornecido pela Oracle, e "SP2" significa que é exclusivo do SQLPlus. (Para obter mais detalhes sobre mensagens de erro do SQLPlus, consulte o Guia do Usuário e Referência do SQL*Plus da Oracle.)

### Qual é o atual diretório?
Sempre que você iniciar o SQLPlus a partir de um prompt de comando do sistema operacional, o SQLPlus considerará o diretório atual do sistema operacional como seu próprio diretório atual. Em outras palavras, se eu iniciar o SQL*Plus usando:

    C:\BOB\FILES> sqlplus

então todas as operações de arquivo dentro do SQL*Plus (como abrir ou executar um script) seriam padrão para o diretório C:\BOB\FILES.

Se você usar um atalho ou uma opção de menu para iniciar o SQLPlus, o diretório atual será o diretório associado ao mecanismo de inicialização pelo sistema operacional. Então, como você alteraria o diretório atual uma vez dentro do SQLPlus? Isso depende da versão. No programa de console, você não pode fazê-lo. Você precisa sair, alterar os diretórios no sistema operacional e reiniciar o SQL*Plus. Na versão GUI, no entanto, concluir um comando de menu Arquivo->Abrir ou Arquivo->Salvar terá o efeito colateral de alterar o diretório atual. (Parei aqui!)

Se o arquivo de script estiver em outro diretório, você pode preceder o nome do arquivo com o caminho:

    SQL> @/files/src/release/1.0/abc.pkg

A ideia de executar scripts em outros diretórios levanta uma questão interessante. E se abc.pkg estiver localizado neste outro diretório e, por sua vez, chamar outros scripts? Ele poderia conter as linhas:

    REM  Filename: abc.pkg
    @abc.pks
    @abc.pkb

(Qualquer linha que comece com REM é um comentário ou "observação" que o SQLPlus ignora.) A execução do script abc.pkg deve executar abc.pks e abc.pkb. Mas como não incluí informações de caminho, onde o SQLPlus irá procurar por esses outros arquivos? Vamos ver:

    C:\BOB\FILES> sqlplus
    ...
    SQL> @/files/src/release/1.0/abc.pkg
    SP2-0310: unable to open file "abc.pks"
    SP2-0310: unable to open file "abc.pkb"

O SQL*Plus procura apenas no diretório em que foi iniciado.

Para resolver esse problema, a Oracle criou o comando @@. Esses dois sinais de arroba significam que, durante essa chamada, "faça de conta que eu mudei o diretório atual para ser o do arquivo atualmente em execução". Portanto, a maneira preferida de escrever as chamadas no script abc.pkg é:

    REM  Filename: abc.pkg
    @@abc.pks
    @@abc.pkb

Agora eu obtenho:

    C:\BOB\FILES> sqlplus
    ...
    SQL> @/files/src/release/1.0/abc.pkg

    Package created.

    Package body created.

...como eu estava esperando.

### Outras tarefas de SQL*PLUS:
Existem dezenas de comandos específicos do SQLPlus, mas tenho espaço para mencionar apenas mais alguns que são particularmente importantes ou confusos. Para um tratamento completo deste venerável produto, obtenha uma cópia do livro Oracle SQLPlus: The Definitive Guide, de Jonathan Gennick, ou, para referência rápida, seu Oracle SQL*Plus Pocket Reference.

#### Configure suas preferências
Você pode alterar o comportamento do SQLPlus, assim como pode fazer com muitos ambientes de linha de comando, alterando o valor de algumas de suas variáveis e configurações integradas. Você já viu um exemplo disso, com o comando SET SERVEROUTPUT. Existem muitas variações do comando SET do SQLPlus, como SET SUFFIX (altera a extensão de arquivo padrão) e SET LINESIZE n (define o número máximo de caracteres em cada linha exibida antes de quebrar). Para ver todos os valores SET aplicáveis à sua sessão atual, use o comando:

    SQL> SHOW ALL

O SQLPlus também pode criar e manipular suas próprias variáveis em memória, e ele reserva algumas variáveis especiais que afetarão seu comportamento. Na verdade, existem dois tipos diferentes de variáveis no SQLPlus: DEFINE e bind variables. Para atribuir um valor a uma variável DEFINE, você pode usar o comando DEFINE:

    SQL> DEFINE x = "the answer is 42"

Para visualizar o valor de x, especifique:

    SQL> DEFINE x
    DEFINE X = "the answer is 42" (CHAR)

Você se referiria a essa variável usando um ampersand (&). O SQL*Plus faz uma substituição simples antes de enviar a declaração para o banco de dados Oracle, então você precisará usar aspas simples em torno da variável quando quiser usá-la como uma string literal:

    SELECT '&x' FROM DUAL;

Para variáveis de associação (bind variables), você primeiro declara a variável. Em seguida, você pode usá-la em PL/SQL e exibi-la usando o comando PRINT do SQL*Plus:

    SQL> VARIABLE x VARCHAR2(10)
    SQL> BEGIN
        2     :x := 'hullo';
        3  END;
        4  /

    PL/SQL procedure successfully completed.

    SQL> PRINT :x

    X
    --------------------------------
    hullo

Isso pode ficar um pouco confuso, porque agora existem duas variáveis "x" diferentes, uma que foi definida e outra que foi declarada:

    SQL> SELECT :x, '&x' FROM DUAL;
    old   1: SELECT :x, '&x' FROM DUAL
    new   1: SELECT :x, 'the answer is 42' FROM DUAL

    :X                               'THEANSWERIS42'
    -------------------------------- ----------------
    hullo                            the answer is 42

Lembre-se de que as DEFINEs são sempre cadeias de caracteres expandidas pelo SQL*Plus, enquanto as variáveis declaradas são usadas como verdadeiras variáveis de ligação (bind variables) em SQL e PL/SQL.

#### Salvando um output à um arquivo
Com frequência, você vai querer salvar a saída de uma sessão do SQLPlus em um arquivo - talvez porque esteja gerando um relatório, porque deseja ter um registro de suas ações ou porque está gerando comandos dinamicamente para executar posteriormente. Uma maneira fácil de fazer isso no SQLPlus é usar o comando SPOOL:

    SQL> SPOOL report
    SQL> @run_report

        ...output scrolls past and gets written to the file report.lst...

    SQL> SPOOL OFF

O primeiro comando, SPOOL report, indica ao SQL*Plus para salvar tudo a partir desse ponto no arquivo report.lst. A extensão do arquivo .lst é a padrão, mas você pode substituí-la fornecendo sua própria extensão no comando SPOOL:

    SQL> SPOOL report.txt

SPOOL OFF informa ao SQL*Plus para parar de salvar a saída e fechar o arquivo.

#### Saindo do SQL*PLUS
Para sair do SQL*Plus e retornar ao sistema operacional, utilize o comando EXIT:

    SQL> EXIT

Se você estiver gravando o log (spooling) quando sair, o SQL*Plus interromperá a gravação e fechará o arquivo de log (spool file).

O que acontece se você modificar alguns dados da tabela durante a sessão, mas sair antes de encerrar a transação com uma instrução explícita de controle de transação? Por padrão, sair do SQLPlus força um COMMIT, a menos que sua sessão termine com um erro SQL e você tenha emitido o comando SQLPlus WHENEVER SQLERROR EXIT ROLLBACK (consulte a seção "Tratamento de erros no SQL*Plus" na página 36).

Para desconectar do banco de dados, mas permanecer conectado ao SQL*Plus, use o comando DISCONNECT, que ficará assim na prática:

    SQL> DISCONNECT
    Disconnected from Personal Oracle Database 10g Release 10.1.0.3.0 - Production
    With the Partitioning, OLAP and Data Mining options
    SQL>

Você não precisa usar o DISCONNECT para trocar de conexões - você pode simplesmente emitir um CONNECT e o SQL*Plus irá encerrar a primeira conexão antes de conectar-se à nova. No entanto, há uma boa razão pela qual você pode querer desconectar antes de se reconectar: se você estiver usando autenticação do sistema operacional, o script pode se reconectar automaticamente... talvez para a conta errada. Já vi isso acontecer.

#### Editando uma declaração
O SQL*Plus mantém a declaração mais recentemente emitida em um buffer, e você pode editar essa declaração usando o editor de linha incorporado ou um editor externo de sua escolha. Para começar, vou mostrar como configurar e usar um editor externo.

Use o comando EDIT para fazer com que o SQLPlus salve o buffer de comando atual em um arquivo, pause temporariamente o SQLPlus e invoque o editor:

    SQL> EDIT

Por padrão, o arquivo será salvo com o nome "afiedt.buf", mas você pode alterar isso com o comando SET EDITFILE. Ou, se você deseja editar um arquivo existente, basta fornecer o nome como argumento para o comando EDIT:

    SQL> EDIT abc.pkg

Depois de salvar o arquivo e sair do editor, a sessão do SQL*Plus lerá o conteúdo do arquivo recém-editado em seu buffer e, em seguida, continuará.

Os editores externos padrão que o Oracle assume são:

- ed para Unix, Linux e sistemas relacionados

- Notepad para variantes do Microsoft Windows

Embora a seleção dos editores padrão esteja codificada no arquivo executável sqlplus, você pode facilmente alterar o editor atual atribuindo seu próprio valor à variável _EDITOR do SQL*Plus. Aqui está um exemplo que eu uso com frequência:

    SQL> DEFINE _EDITOR = /bin/vi

onde /bin/vi é o caminho completo para um editor popular entre alguns estranhos. Recomendo usar o caminho completo do editor aqui, por motivos de segurança.

Se você realmente deseja usar o editor de linha incorporado do SQL*Plus (e pode ser muito útil), os comandos essenciais que você precisa conhecer são:

- L

    Lista as declarações mais recentes

- n

    Cria n linhas de declaração nas linhas atuais.

- DEL

    Deleta a linha atual.

- C/old/new/

    Na linha atual, altera a primeira ocorrência de "antigo" para "novo". O delimitador (neste caso, uma barra para frente) pode ser qualquer caractere arbitrário.

- n text

    Define o texto como o texto atual da linha n.

- I

    Insere uma linha abaixo da linha atual. Para inserir uma nova linha antes da linha 1, use um comando de linha zero (por exemplo, 0 texto).

#### Carregando automaticamente o seu próprio ambiente personalizado na inicialização.
Para personalizar o ambiente do SQLPlus e fazer com que ele atribua suas preferências de uma sessão para outra, você vai querer editar um ou ambos os scripts de inicialização automática. A maneira como o SQLPlus se comporta na inicialização é a seguinte:

- Ele procura pelo arquivo $ORACLE_HOME/sqlplus/admin/glogin.sql e, se encontrado, executa quaisquer comandos contidos nele. Este script de login "global" se aplica a todos que executam o SQL*Plus a partir desse Oracle home, não importa em qual diretório eles iniciem.

- Em seguida, ele executa o arquivo login.sql no diretório atual, caso exista.

O script de inicialização pode conter os mesmos tipos de comandos que qualquer outro script do SQL*Plus: comandos SET, instruções SQL, comandos de formatação de colunas e assim por diante.

A presença de ambos os arquivos não é obrigatória. Se ambos os arquivos estiverem presentes, o glogin.sql é executado primeiro, seguido pelo login.sql. Em caso de preferências ou variáveis conflitantes, a última configuração é considerada válida.

Aqui estão algumas das minhas configurações favoritas para o login.sql:

    REM Number of lines of SELECT statement output before reprinting headers
    SET PAGESIZE 999

    REM Width of displayed page, expressed in characters
    SET LINESIZE 132

    REM Enable display of DBMS_OUTPUT messages. Use 1000000 rather than
    REM "UNLIMITED" for databases earlier than Oracle Database 10g Release 2
    SET SERVEROUTPUT ON SIZE UNLIMITED FORMAT WRAPPED

    REM Change default to "vi improved" editor
    DEFINE _EDITOR = /usr/local/bin/vim

    REM Format misc columns commonly retrieved from data dictionary
    COLUMN segment_name FORMAT A30 WORD_WRAP
    COLUMN object_name FORMAT A30 WORD_WRAP

    REM Set the prompt (works in SQL*Plus
    REM in Oracle9i Database or later)
    SET SQLPROMPT "_USER'@'_CONNECT_IDENTIFIER > "

### Tratamento de Erros no SQL*Plus
A maneira como o SQLPlus comunica o sucesso depende da classe de comando que você está executando. Com a maioria dos comandos específicos do SQLPlus, você pode calibrar o sucesso pela ausência de uma mensagem de erro. Comandos SQL e PL/SQL bem-sucedidos, por outro lado, geralmente resultam em algum tipo de feedback textual positivo.

Se o SQLPlus encontrar um erro em uma instrução SQL ou PL/SQL, por padrão, ele reportará o erro e continuará o processamento. Esse comportamento é desejável quando você está trabalhando interativamente. No entanto, ao executar um script, há muitos casos em que você desejará que um erro faça com que o SQLPlus seja encerrado. Use o seguinte comando para fazer isso acontecer:

    SQL> WHENEVER SQLERROR EXIT SQL.SQLCODE

A partir desse momento na sessão atual, o SQLPlus será encerrado se o servidor de banco de dados retornar quaisquer mensagens de erro em resposta a uma instrução SQL ou PL/SQL. A parte SQL.SQLCODE significa que, quando o SQLPlus é encerrado, ele define o código de retorno para um valor diferente de zero, que você pode detectar no ambiente de chamada. Caso contrário, o SQL*Plus sempre termina com um código de retorno 0, o que pode falsamente implicar que o script teve sucesso.

Outra forma dessa comando é:

    SQL> WHENEVER SQLERROR EXIT SQL.SQLCODE ROLLBACK

Isso significa que você também deseja que o SQL*Plus reverta quaisquer alterações não confirmadas antes de sair.

### Por que você vai amar e odiar o SQL*Plus
Além das características que você acabou de ler, a seguir estão algumas características específicas do SQL*Plus que você aprenderá a conhecer e amar:

- Com o SQL*Plus, você pode executar programas em lote, fornecendo argumentos específicos do aplicativo na linha de comando sqlplus e referenciando-os no script usando &1 (primeiro argumento), &2 (segundo argumento), etc.

- O SQL*Plus oferece suporte completo e atualizado para todos os comandos SQL e PL/SQL. Isso pode ser importante quando você está usando recursos exclusivos do Oracle. Ambientes de terceiros podem não oferecer cobertura de 100%; por exemplo, alguns têm demorado a adicionar suporte para os tipos de objeto do Oracle, que foram introduzidos há alguns anos.

- O SQL*Plus é executado em todas as mesmas plataformas de hardware e sistema operacional em que o servidor Oracle é executado.

Mas, como acontece com qualquer ferramenta, também haverá algumas irritações:

- Nas versões do console do SQLPlus, o buffer de comandos é limitado ao comando mais recentemente usado; o SQLPlus não oferece um histórico de comandos mais extenso.

- Com o SQL*Plus, não há recursos modernos de interpretador de comandos, como preenchimento automático de palavras-chave ou sugestões sobre quais objetos de banco de dados estão disponíveis enquanto você digita um comando.

- A ajuda online consiste em uma documentação mínima do conjunto de comandos do SQL*Plus. (Use o comando HELP para obter ajuda sobre um comando específico.)

- Não é possível alterar o diretório atual uma vez que você tenha iniciado o SQLPlus. Isso pode ser irritante ao abrir ou salvar scripts se você não gosta de digitar caminhos completos. Se você descobrir que está em um diretório inconveniente, precisará sair do SQLPlus, alterar de diretório e reiniciar o SQL*Plus.

- A menos que eu decida usar o recurso perigoso do SQLPATH, o SQL*Plus procura apenas no diretório de inicialização pelo login.sql; seria melhor se ele também procurasse no meu diretório pessoal pelo script de inicialização.

A conclusão é que o SQL*Plus é um pouco uma ferramenta para "programadores de verdade" que não é nem acolhedora nem amigável. No entanto, é ubíqua, não apresenta falhas e provavelmente terá suporte enquanto houver uma Oracle Corporation.

## Realizando tarefas essenciais do PL/SQL
Vamos nos concentrar nos pontos principais de criação, execução, exclusão e gerenciamento de programas PL/SQL, utilizando o SQL*Plus como frontend. Não espere encontrar muitos detalhes aqui; encare esta seção como uma visão geral dos tópicos que serão abordados com mais detalhes nos capítulos seguintes.

### Criando um Programa Armazenado
Para criar um novo programa PL/SQL armazenado, você usa uma das instruções CREATE do SQL. Por exemplo, se você deseja criar uma função armazenada que conta as palavras em uma string, você pode fazer isso usando a instrução CREATE FUNCTION:

    CREATE FUNCTION wordcount (str IN VARCHAR2)
        RETURN PLS_INTEGER
    AS
        declare local variables here
    BEGIN
        implement algorithm here
    END;
    /

Assim como nos blocos simples BEGIN-END mostrados anteriormente, executar essa declaração a partir do SQL*Plus requer uma barra invertida no final de uma linha separada.

Supondo que o DBA tenha concedido a você o privilégio CREATE PROCEDURE do Oracle (que também concede o privilégio de criar funções), essa declaração faz com que o Oracle compile e armazene essa função armazenada em seu esquema. Se seu código for compilado com sucesso, você provavelmente verá uma mensagem de sucesso como esta:

    Function created.

Se outro objeto de banco de dados, como uma tabela ou pacote, chamado wordcount, já existir em seu esquema do Oracle, a instrução CREATE FUNCTION falhará com a mensagem de erro ORA-00955: nome já está sendo usado por um objeto existente. Esse é um motivo pelo qual o Oracle oferece a opção OR REPLACE, que você provavelmente vai querer usar em 99% das vezes:

    CREATE OR REPLACE FUNCTION wordcount (str IN VARCHAR2)
        RETURN PLS_INTEGER
    AS same as before

A opção OR REPLACE evita os efeitos colaterais de excluir e recriar o programa; em outras palavras, preserva quaisquer privilégios de objeto que você tenha concedido a outros usuários ou funções. Felizmente, ela substitui apenas objetos do mesmo tipo e não excluirá automaticamente uma tabela chamada wordcount só porque você decidiu criar uma função com esse nome.

Assim como blocos anônimos usados mais de uma vez, os programadores geralmente armazenam esses comandos em arquivos no sistema operacional. Eu poderia criar um arquivo wordcount.fun para essa função e usar o comando @ do SQL*Plus para executá-lo:

    SQL> @wordcount.fun

    Function created.

Como mencionado anteriormente, o SQL*Plus não exibe, por padrão, o conteúdo dos scripts. Você pode usar SET ECHO ON para ver o código-fonte sendo exibido na tela, incluindo os números de linha atribuídos pelo banco de dados; essa configuração pode ser útil ao solucionar problemas. Vamos introduzir um erro no programa comentando uma declaração de variável (linha 4):

    /* File on web: wordcount.fun */
    SQL> SET ECHO ON
    SQL> @wordcount.fun
    SQL> CREATE OR REPLACE FUNCTION wordcount (str IN VARCHAR2)
        2     RETURN PLS_INTEGER
        3  AS
        4  /* words PLS_INTEGER := 0;  ***Commented out for intentional error*** */
        5     len PLS_INTEGER := NVL(LENGTH(str),0);
        6     inside_a_word BOOLEAN;
        7  BEGIN
        8     FOR i IN 1..len + 1
        9     LOOP
        10        IF ASCII(SUBSTR(str, i, 1)) < 33 OR i > len
        11        THEN
        12           IF inside_a_word
        13           THEN
        14              words := words + 1;
        15              inside_a_word := FALSE;
        16           END IF;
        17        ELSE
        18           inside_a_word := TRUE;
        19        END IF;
        20     END LOOP;
        21     RETURN words;
        22  END;
        23  /

    Warning: Function created with compilation errors.

Esta mensagem nos informa que a função foi criada, mas que houve erros de compilação que a tornam inoperável. Conseguimos armazenar o código-fonte no banco de dados; agora precisamos extrair os detalhes do erro do banco de dados. A maneira mais rápida de ver o texto completo da mensagem de erro é usar o comando SHOW ERRORS do SQL*Plus, abreviado como SHO ERR:

    SQL> SHO ERR
    Errors for FUNCTION WORDCOUNT:
    LINE/COL ERROR
    -------- ----------------------------------------------
    14/13    PLS-00201: identifier 'WORDS' must be declared
    14/13    PL/SQL: Statement ignored
    21/4     PL/SQL: Statement ignored
    21/11    PLS-00201: identifier 'WORDS' must be declared

O compilador detectou ambas as ocorrências da variável, relatando os números exatos de linha e coluna. Para obter mais detalhes sobre qualquer erro baseado no servidor, você pode procurá-lo pelo seu identificador - PLS-00201 neste caso - no documento "Database Error Messages" da Oracle.

Nos bastidores, o comando SHOW ERRORS é apenas uma consulta à visualização USER_ERRORS no dicionário de dados do Oracle. Você pode consultar essa visualização por conta própria, mas geralmente não é necessário (consulte a barra lateral a seguir).

### Mostra outros erros
Muitos programadores do Oracle conhecem apenas uma forma do comando SQL*Plus:

    SQL> SHOW ERRORS

e eles acreditam erroneamente que precisam consultar diretamente a visualização USER_ERRORS para ver algo além das mensagens de erro da compilação mais recente. No entanto, você pode acrescentar ao comando SHOW ERRORS uma categoria de objeto e um nome, e ele exibirá os erros mais recentes para qualquer objeto:

    SQL> SHOW ERRORS category [schema.]object

Por exemplo, para visualizar os erros mais recentes da função wordcount, especifique:

    SQL> SHOW ERRORS FUNCTION wordcount

Use cautela ao interpretar a saída:

    No errors.

Essa mensagem na verdade significa uma das três coisas: (1) o objeto foi compilado com sucesso; (2) você forneceu a categoria errada (por exemplo, função em vez de procedimento); ou (3) nenhum objeto com esse nome existe.

A lista completa de categorias que esse comando reconhece varia de acordo com a versão, mas inclui as seguintes:

    DIMENSION
    FUNCTION
    JAVA SOURCE
    JAVA CLASS
    PACKAGE
    PACKAGE BODY
    PROCEDURE
    TRIGGER
    TYPE
    TYPE BODY
    VIEW

É prática comum adicionar um comando SHOW ERRORS após cada declaração CREATE em um script que cria um programa PL/SQL armazenado. Portanto, um modelo de "boas práticas" para construir programas armazenados no SQL*Plus pode começar com esta forma:

    CREATE OR REPLACE program-type
    AS
        your code
    END;
    /

    SHOW ERRORS

(Normalmente, não incluo SET ECHO ON em scripts, mas digito esse comando na linha de comando quando necessário.)

Quando seu programa contém um erro que o compilador pode detectar, o CREATE ainda fará com que o banco de dados Oracle armazene o programa no banco de dados, embora em um estado inválido. No entanto, se você digitar incorretamente parte da sintaxe do CREATE, o banco de dados não conseguirá entender o que você está tentando fazer e não armazenará o código no banco de dados.

### Executing a Stored Program
Já examinamos duas maneiras diferentes de invocar um programa armazenado: envolvê-lo em um bloco PL/SQL simples ou usar o comando EXECUTE do SQL*Plus. Você também pode usar programas armazenados dentro de outros programas armazenados. Por exemplo, você pode invocar uma função como wordcount em qualquer local onde possa usar uma expressão inteira. Aqui está uma breve ilustração de como eu poderia testar a função wordcount com uma entrada estranha (CHR(9) é um caractere ASCII "tab"):

    BEGIN
        DBMS_OUTPUT.PUT_LINE('There are ' || wordcount(CHR(9)) || ' words in a tab');
    END;
    /

Eu incorporei wordcount como parte de uma expressão e forneci-a como argumento para DBMS_OUTPUT.PUT_LINE. Aqui, o PL/SQL automaticamente converte o inteiro em uma string para poder concatená-lo com outras duas expressões literais. O resultado é:

    There are 0 words in a tab

Você também pode invocar muitas funções PL/SQL dentro de instruções SQL. Aqui estão vários exemplos de como você pode usar a função wordcount:

- Aplicar a função em uma lista SELECT para calcular o número de palavras em uma coluna de tabela:

    SELECT isbn, wordcount(description) FROM books;

- Utilize a instrução CALL compatível com o padrão ANSI, vinculando a saída da função a uma variável do SQL*Plus e exiba o resultado:

    VARIABLE words NUMBER
    CALL wordcount('some text') INTO :words;
    PRINT :words

- Da mesma forma que acima, execute a função de um banco de dados remoto definido na conexão de banco de dados test.newyork.ora.com:

    CALL wordcount@test.newyork.ora.com('some text') INTO :words;

- Execute a função, pertencente ao esquema bob, enquanto estiver conectado a qualquer esquema que possua autorização apropriada:

    SELECT bob.wordcount(description) FROM books WHERE id = 10007;

### Exibindo Programas Armazenados:
Mais cedo ou mais tarde, você vai querer obter uma lista dos programas armazenados de sua propriedade, e talvez também precise visualizar a versão mais recente do código-fonte do programa que o Oracle salvou em seu dicionário de dados. Essa é uma tarefa que você encontrará muito mais fácil se usar algum tipo de assistente de navegação baseado em GUI, mas se você não tiver essa ferramenta, não é tão difícil escrever algumas instruções SQL que extrairão as informações desejadas do dicionário de dados.

Por exemplo, para ver uma lista completa de seus programas (e tabelas, índices, etc.), consulte a visão USER_OBJECTS, como neste exemplo:

    SELECT * FROM USER_OBJECTS;

Essa visão mostra o nome, tipo, horário de criação, horário da última compilação, status (válido ou inválido) e outras informações úteis.

Se tudo o que você precisa é um resumo da interface chamável de um programa PL/SQL no SQL*Plus, o comando mais fácil de usar é DESCRIBE:

    SQL> DESCRIBE wordcount
    FUNCTION wordcount RETURNS BINARY_INTEGER
        Argument Name                  Type                    In/Out Default?
        ------------------------------ ----------------------- ------ --------
        STR                            VARCHAR2                IN

DESCRIBE também funciona em tabelas, visões, tipos de objeto, procedimentos e pacotes. Para ver o código-fonte completo de seus programas armazenados, consulte USER_SOURCE ou TRIGGER_SOURCE. (A consulta dessas visões do dicionário de dados é discutida em mais detalhes no Capítulo 20.)

### Gerenciando Privilégios e Sinônimos para Programas Armazenados
Quando você cria um programa PL/SQL, normalmente apenas você ou o DBA podem executá-lo. Para dar a outro usuário a autoridade para executar seu programa, emita uma declaração GRANT:

    GRANT EXECUTE ON wordcount TO scott;

Para remover o privilégio, use REVOKE:

    REVOKE EXECUTE ON wordcount FROM scott;

Você também pode conceder o privilégio EXECUTE a uma função (role):

    GRANT EXECUTE ON wordcount TO all_mis;

Ou, se apropriado, você poderia permitir que qualquer usuário do banco de dados atual execute o programa:

    GRANT EXECUTE ON wordcount TO PUBLIC;

Se você conceder um privilégio a um indivíduo como Scott e a um papel do qual esse usuário é membro (digamos, all_mis), e também conceder a permissão a PUBLIC, o banco de dados lembrará todas as três concessões até que sejam revogadas. Qualquer uma das concessões é suficiente para permitir que o indivíduo execute o programa, então, se você decidir que não deseja que Scott o execute, é necessário revogar o privilégio de Scott, revogá-lo de PUBLIC e, por fim, revogá-lo do papel all_mis (ou revogar esse papel de Scott).

Para visualizar uma lista de privilégios que você concedeu a outros usuários e papéis, você pode consultar a visualização do dicionário de dados USER_TAB_PRIVS_MADE. De forma um tanto contra-intuitiva, os nomes dos programas PL/SQL aparecem na coluna table_name:

    SQL> SELECT table_name, grantee, privilege
        2    FROM USER_TAB_PRIVS_MADE
        3   WHERE table_name = 'WORDCOUNT';

    TABLE_NAME                     GRANTEE                        PRIVILEGE
    ------------------------------ ------------------------------ -----------
    WORDCOUNT                      PUBLIC                         EXECUTE
    WORDCOUNT                      SCOTT                          EXECUTE
    WORDCOUNT                      ALL_MIS                        EXECUTE

Quando Scott tiver o privilégio EXECUTE no wordcount, ele provavelmente desejará criar um sinônimo para o programa para evitar ter que prefixá-lo com o nome do esquema que o possui:

    SQL> CONNECT scott/tiger
    Connected.
    SQL>CREATE OR REPLACE SYNONYM wordcount FOR bob.wordcount;

Agora ele pode executar o programa em seus programas referindo-se apenas ao sinônimo:

    IF wordcount(localvariable) > 100 THEN...

Isso é bom, porque se o proprietário da função mudar, apenas o sinônimo (e não qualquer programa armazenado) precisa ser modificado.

É possível criar um sinônimo para um procedimento, função, pacote ou tipo definido pelo usuário. Sinônimos para procedimentos, funções ou pacotes podem ocultar não apenas o esquema, mas também o banco de dados real; você pode criar um sinônimo para programas remotos tão facilmente quanto para programas locais. No entanto, os sinônimos só podem ocultar identificadores de esquema e banco de dados; você não pode usar um sinônimo no lugar de um subprograma empacotado.

Remover um sinônimo é fácil:

    DROP SYNONYM wordcount;

### Removendo um programa armazenado.
Se você realmente não precisa mais de um determinado programa armazenado, você pode removê-lo usando o comando DROP do SQL:

    DROP FUNCTION wordcount;

Você pode excluir um pacote, que pode ser composto por até dois elementos (uma especificação e um corpo), na sua totalidade:

    DROP PACKAGE pkgname;

Ou você pode excluir apenas o corpo sem invalidar a respectiva especificação:

    DROP PACKAGE BODY pkgname;

Sempre que você exclui um programa que é chamado por outros programas, os chamadores são marcados como INVÁLIDOS.

### Ocultando o código-fonte de um programa armazenado.
Quando você cria um programa PL/SQL conforme descrito anteriormente, o código-fonte estará disponível em texto claro no dicionário de dados, e qualquer DBA pode visualizá-lo ou até mesmo modificá-lo. Para proteger segredos comerciais ou evitar a adulteração do seu código, você pode querer alguma forma de ofuscar o seu código-fonte PL/SQL antes de entregá-lo.

O Oracle fornece um utilitário de linha de comando chamado "wrap" que converte muitas declarações CREATE em uma combinação de texto comum e hexadecimal. Não é uma verdadeira criptografia, mas vai longe para ocultar seu código. Aqui estão algumas partes extraídas de um arquivo ocultado:

    FUNCTION wordcount wrapped
    0
    abcd
    abcd ...snip...
    1WORDS:
    10:
    1LEN:
    1NVL:
    1LENGTH:
    1INSIDE_A_WORD:
    1BOOLEAN: ...snip...
    a5 b 81 b0 a3 a0 1c 81
    b0 91 51 a0 7e 51 a0 b4
    2e 63 37 :4 a0 51 a5 b a5
    b 7e 51 b4 2e :2 a0 7e b4
    2e 52 10 :3 a0 7e 51 b4 2e
    d :2 a0 d b7 19 3c b7 :2 a0
    d b7 :2 19 3c b7 a0 47 :2 a0

Se você precisa de uma criptografia real - por exemplo, para fornecer informações como uma senha que realmente precisa ser segura - não deve depender dessa funcionalidade.

Obs: O Oracle oferece uma maneira de incorporar criptografia real em seus próprios aplicativos usando o pacote embutido DBMS_CRYPTO (ou DBMS_OBFUSCATION_TOOLKIT) em versões anteriores ao Oracle Database 10g; consulte o Capítulo 23 para obter informações sobre o DBMS_CRYPTO.

Para obter mais informações sobre o utilitário "wrap", consulte o Capítulo 20.

## Ambientes de Edição para PL/SQL
Como mencionei anteriormente, você pode usar um ambiente de edição e execução "de menor denominador comum" como o SQL*Plus, ou pode utilizar um ambiente de desenvolvimento integrado (IDE) que oferece interfaces gráficas abrangentes para melhorar sua produtividade. Esta seção lista algumas das ferramentas IDE mais populares. Não recomendo nenhuma ferramenta específica; você deve definir cuidadosamente sua lista de requisitos e prioridades para tal ferramenta e depois verificar qual delas atende melhor às suas necessidades.

- Toad: Oferecido pela Quest Software, o Toad é, de longe, a IDE PL/SQL mais popular. Suas versões gratuita e comercial são usadas por centenas de milhares de desenvolvedores.

- SQL Navigator: Também oferecido pela Quest Software, o SQL Navigator é usado por dezenas de milhares de desenvolvedores que adoram a interface e os recursos de produtividade do produto.

- PL/SQL Developer: O PL/SQL Developer, vendido pela Allround Automations, é o favorito de muitos desenvolvedores PL/SQL. Ele é construído em torno de uma arquitetura de plug-in, para que terceiros possam oferecer extensões ao produto base.

- SQL Developer: Após anos de pouco ou nenhum suporte para edição PL/SQL, a Oracle Corporation criou o SQL Developer como um "fork" da ferramenta base JDeveloper. O SQL Developer é gratuito e cada vez mais robusto.

Existem muitas outras IDEs PL/SQL disponíveis, mas as mencionadas são algumas das melhores e mais populares.

## Chamando PL/SQL de Outras Linguagens
Mais cedo ou mais tarde, você provavelmente desejará chamar PL/SQL a partir de C, Java, Perl, PHP ou de qualquer outro lugar. Isso parece um pedido razoável, mas se você já trabalhou com integração de linguagens antes, pode estar familiarizado com algumas das complexidades de combinar tipos de dados específicos de cada linguagem - especialmente tipos de dados compostos, como arrays, registros e objetos - além das diferenças na semântica de parâmetros ou extensões de fornecedor para interfaces de programação de aplicativos "padrão", como a Conectividade de Banco de Dados Aberta (ODBC) da Microsoft.

Vou mostrar alguns exemplos muito breves de como chamar PL/SQL do mundo externo. Digamos que eu tenha escrito uma função PL/SQL que recebe um ISBN expresso como uma string e retorna o título do livro correspondente:

    /* File on web: booktitle.fun */
    FUNCTION booktitle (isbn_in IN VARCHAR2)
        RETURN VARCHAR2
    IS
        l_title books.title%TYPE;
        CURSOR icur IS SELECT title FROM books WHERE isbn = isbn_in;
    BEGIN
        OPEN icur;
        FETCH icur INTO l_title;
        CLOSE icur;
        RETURN l_title;
    END;

No SQL*Plus, eu poderia chamá-lo de várias maneiras diferentes. A forma mais curta seria a seguinte:

    SQL> EXEC DBMS_OUTPUT.PUT_LINE(booktitle('0-596-00180-0'))
    Learning Oracle PL/SQL

    PL/SQL procedure successfully completed.

Em seguida, vou mostrar como eu poderia chamar essa função nos seguintes ambientes:

- C, usando o pré-compilador da Oracle (Pro*C)

- Java, usando JDBC

- Perl, usando Perl DBI e DBD::Oracle

- PHP

- PL/SQL Server Pages

Esses exemplos são muito artificiais - por exemplo, o nome de usuário e senha são codificados diretamente, e os programas simplesmente exibem a saída no stdout. Além disso, nem vou tentar descrever cada linha de código. No entanto, esses exemplos darão uma ideia dos padrões que você pode encontrar em diferentes linguagens.

### C: usando o pré-compilador da Oracle (Pro*C)
A Oracle fornece pelo menos duas interfaces em linguagem C para o Oracle: uma chamada OCI (Oracle Call Interface), que é em grande parte usada por especialistas, e outra chamada ProC. O OCI fornece centenas de funções das quais você deve codificar operações de baixo nível, como abrir, analisar, vincular, definir, executar, buscar... e isso é apenas para uma única consulta. Como o programa OCI mais simples que faz algo interessante tem cerca de 200 linhas de código, pensei em mostrar um exemplo usando o ProC. O Pro*C é uma tecnologia de pré-compilador que permite construir arquivos de origem contendo uma combinação de C, SQL e PL/SQL. Você executa o seguinte programa através do programa "proc" da Oracle, e será gerado código C:

    /* File on web: callbooktitle.pc */
    #include <stdio.h>
    #include <string.h>
    EXEC SQL BEGIN DECLARE SECTION;
        VARCHAR uid[20];
        VARCHAR pwd[20];
        VARCHAR isbn[15];
        VARCHAR btitle[400];
    EXEC SQL END DECLARE SECTION;
    EXEC SQL INCLUDE SQLCA.H;
    int sqlerror();
    int main()
    {
        /* VARCHARs actually become a struct of a char array and a length */
        strcpy((char *)uid.arr,"scott");
        uid.len = (short) strlen((char *)uid.arr);
        strcpy((char *)pwd.arr,"tiger");
        pwd.len = (short) strlen((char *)pwd.arr);
        /* this is a cross between an exception and a goto */
        EXEC SQL WHENEVER SQLERROR DO sqlerror();
        /* connect and then execute the function */
        EXEC SQL CONNECT :uid IDENTIFIED BY :pwd;
        EXEC SQL EXECUTE
        BEGIN
            :btitle := booktitle('0-596-00180-0');
        END;
        END-EXEC;
        /* show me the money */
        printf("%s\n", btitle.arr);
        /* disconnect from ORACLE */
        EXEC SQL COMMIT WORK RELEASE;
        exit(0);
    }
    sqlerror()
    {
        EXEC SQL WHENEVER SQLERROR CONTINUE;
        printf("\n% .70s \n", sqlca.sqlerrm.sqlerrmc);
        EXEC SQL ROLLBACK WORK RELEASE;
        exit(1);
    }

Como você pode ver, o ProC não é uma abordagem pela qual os puristas da linguagem suspirarão. E acredite em mim, você não vai querer mexer no código C que isso gera. No entanto, muitas empresas descobrem que o ProC (ou Pro*Cobol, ou qualquer uma das várias outras linguagens que o Oracle suporta) serve como um ponto intermediário razoável entre, por exemplo, o Visual Basic (muito lento e desajeitado) e o OCI (muito difícil).

A própria documentação da Oracle oferece a melhor fonte de informações sobre o Pro*C.

### Java: usando JDBC
Assim como no caso do C, a Oracle oferece várias abordagens diferentes para se conectar ao banco de dados. A abordagem de SQL embutido, conhecida como SQLJ, é semelhante à outra tecnologia de pré-compilador da Oracle, embora um pouco mais amigável ao depurador. Uma abordagem mais popular e centrada em Java é conhecida como JDBC (que na verdade não significa nada em particular), embora a interpretação usual seja "Java Database Connectivity" (Conectividade de Banco de Dados Java):

    /* File on web: Book.java */
    import java.sql.*;

    public class Book
    {
        public static void main(String[] args) throws SQLException
        {
            // initialize the driver and try to make a connection

            DriverManager.registerDriver (new oracle.jdbc.driver.OracleDriver ());
            Connection conn =
            DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:o92", "scott", "tiger");

            // prepareCall uses ANSI92 "call" syntax
            CallableStatement cstmt = conn.prepareCall("{? = call booktitle(?)}");

            // get those bind variables and parameters set up
            cstmt.registerOutParameter(1, Types.VARCHAR);
            cstmt.setString(2, "0-596-00180-0");

            // now we can do it, get it, close it, and print it
            cstmt.executeUpdate();
            String bookTitle = cstmt.getString(1);
            conn.close();
            System.out.println(bookTitle);
        }
    }

Este exemplo em particular utiliza o driver thin, que oferece ótima compatibilidade e facilidade de instalação (todas as funcionalidades do protocolo de rede estão contidas em uma biblioteca Java), em detrimento do desempenho da comunicação. Uma abordagem alternativa seria usar o que é conhecido como driver OCI. Não se preocupe: não é necessário nenhum conhecimento avançado de programação para utilizá-lo, apesar do nome!

### Perl: usando Perl DBI e DBD::Oracle
Muito amado pela comunidade de administração de sistemas, Perl é um tanto quanto a mãe de todas as linguagens de código aberto. Agora na versão 5.10, ele faz praticamente tudo e parece rodar em qualquer lugar. E com ferramentas de autoconfiguração bacanas como o CPAN (Comprehensive Perl Archive Network), é fácil instalar módulos fornecidos pela comunidade, como a Interface de Banco de Dados (DBI) e o respectivo driver do Oracle, DBD::Oracle.

    /* File on web: callbooktitle.pl */
    #!/usr/bin/perl

    use strict;
    use DBI qw(:sql_types);

    # either make the connection or die
    my $dbh = DBI->connect(
        'dbi:Oracle:o92',
        'scott',
        'tiger',
        {
            RaiseError => 1,
            AutoCommit => 0
        }
    ) || die "Database connection not made: $DBI::errstr";

    my $retval;

    # make parse call to Oracle, get statement handle
    eval {
        my $func = $dbh->prepare(q{
            BEGIN
                :retval := booktitle(isbn_in => :bind1);
            END;
        });

    # bind the parameters and execute
        $func->bind_param(":bind1", "0-596-00180-0");
        $func->bind_param_inout(":retval", \$retval, SQL_VARCHAR);
        $func->execute;
    };

    if( $@ ) {
        warn "Execution of stored procedure failed: $DBI::errstr\n";
        $dbh->rollback;
    } else {
        print "Stored procedure returned: $retval\n";
    }

    # don't forget to disconnect
    $dbh->disconnect;

Perl é uma daquelas linguagens em que é vergonhosamente fácil escrever código que é impossível de ler. Não é uma linguagem especialmente rápida ou compacta, mas existem versões compiladas que pelo menos abordam o problema de velocidade.

Para obter mais informações sobre Perl e Oracle, consulte "Programming the Perl DBI" de Alligator Descartes e Tim Bunce. Existem também muitos livros excelentes sobre a linguagem Perl, sem mencionar as informações online em perl.com (um site da O'Reilly), perl.org e cpan.org.

### PHP: Usando Extensões Oracle
Se você é do tipo de pessoa que pode usar o servidor web gratuito e extremamente popular conhecido como Apache, você também pode gostar de usar a linguagem de programação gratuita e extremamente popular conhecida como PHP. Comumente usada para criar páginas da web dinâmicas, o PHP também pode ser usado para construir aplicativos GUI ou executar programas de linha de comando. Como você pode imaginar, a Oracle é um dos muitos ambientes de banco de dados que funcionam com o PHP; de fato, a Oracle Corporation fez parceria com a Zend para fornecer uma distribuição "aprovada" do banco de dados Oracle com o PHP.

Observação: Observe que se você deseja suporte para o PHP, precisará obtê-lo da comunidade de usuários ou de uma empresa como a Zend. A Oracle Corporation não atende chamadas de suporte para o PHP.

Este exemplo usa a família de funções PHP conhecida como OCI8. Não deixe que o "8" no nome o engane - ele deve funcionar com tudo, desde o Oracle7 até o Oracle Database 11g.

    /* File on web: callbooktitle.php */
    <?PHP
        // Initiate the connection to the o92 database
        $conn = OCILogon ("scott", "tiger", "o92");

        // Make parse call to Oracle, get statement identity
        $stmt = OCIParse($conn, "begin :res := booktitle('0-596-00180-0'); end;");

        // Show any errors
        if (!$stmt) {
            $err = OCIError();
            echo "Oops, you broke it: ".$err["message"];
            exit;
        }

        // Bind 200 characters of the variable $result to placeholder :res
        OCIBindByName($stmt, "res", &$result, 200);

        // Execute
        OCIExecute($stmt);

        // Stuff the value into the variable
        OCIResult($stmt,$result);

        // Display on stdout
        echo "$result\n";

        // Relax
        OCILogoff($conn);
    ?>

Quando executado na linha de comando, parece algo assim:

    $ php callbooktitle.php
    Learning Oracle PL/SQL

A propósito, essas funções Oracle OCI não estão disponíveis no PHP por padrão, mas não deve ser muito difícil para o administrador do sistema reconstruir o PHP com as extensões Oracle.

Você pode encontrar mais informações sobre o PHP em php.net ou em um dos muitos livros da O'Reilly sobre o assunto. Para dicas específicas do PHP para Oracle, visite a Oracle Technology Network.

### PL/SQL Server Pages
Embora o ambiente de PL/SQL Server Pages (PSP) seja proprietário da Oracle, achei importante mencioná-lo porque é uma maneira rápida de criar uma página da web. O PSP é outra tecnologia de pré-compilador que permite incorporar PL/SQL em páginas HTML. A construção <%= %> aqui significa "processar isso como PL/SQL e retornar o resultado para a página":

    /* File on web: favorite_plsql_book.psp */
    <%@ page language="PL/SQL" %>
    <%@ plsql procedure="favorite_plsql_book" %>
    <HTML>
        <HEAD>
            <TITLE>My favorite book about PL/SQL</TITLE>
        </HEAD>
        <BODY>
            <%= booktitle( '0-596-00180-0') %>
        </BODY>
    </HTML>

Quando corretamente instalada em um servidor web conectado a um banco de dados Oracle, esta página é exibida como na Figura 2-3.

Eu sou bastante apegado às PL/SQL Server Pages como uma boa maneira de criar rapidamente sites orientados a dados.

Para obter mais informações sobre PL/SQL Server Pages, consulte o livro "Learning Oracle PL/SQL", que é escrito pelos autores do livro que você está lendo agora.

### E em outros lugares?
Você viu como usar o PL/SQL no SQL*Plus e em vários outros ambientes e linguagens de programação comuns. Ainda existem mais lugares e maneiras de usar o PL/SQL:

- Incorporado em COBOL ou FORTRAN e processado com o pré-compilador da Oracle.

- Chamado do Visual Basic, usando algum tipo de ODBC.

- Chamado da linguagem de programação Ada, por meio de uma tecnologia chamada SQL*Module.

- Executado automaticamente como triggers em eventos no banco de dados Oracle, como atualizações de tabelas.

- Agendado para executar periodicamente dentro do banco de dados Oracle, por meio do pacote fornecido DBMS_SCHEDULER.

- No banco de dados TimesTen, um banco de dados em memória adquirido pela Oracle Corporation, cujo conteúdo pode ser manipulado com código PL/SQL, assim como o banco de dados relacional.

Infelizmente, não consigo abordar todos esses tópicos neste livro.
