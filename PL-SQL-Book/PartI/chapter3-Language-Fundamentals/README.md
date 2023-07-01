# Fundamentos da Linguagem:
Toda linguagem - seja ela humana ou de computador - possui uma sintaxe, um vocabulário e um conjunto de caracteres. Para se comunicar dentro dessa linguagem, você precisa aprender as regras que governam o seu uso. Muitos de nós têm receio de aprender uma nova linguagem de programação. A mudança muitas vezes causa medo, mas, em geral, as linguagens de programação são muito simples, e o PL/SQL não é exceção. A dificuldade de conversar em linguagens baseadas em bytes não está na própria linguagem, mas sim no compilador ou computador com os quais estamos tendo a conversa. Os compiladores, em sua maioria, são bastante limitados. Eles não são seres criativos e conscientes. Não são capazes de ter pensamentos originais. Seu vocabulário é severamente limitado. Os compiladores apenas pensam seus pensamentos monótonos muito, muito rapidamente - e de forma muito inflexível.

Se alguém me perguntar "tem um trocado?", consigo interpretar facilmente essa frase e decidir como responder. Por outro lado, se eu instruir o PL/SQL a "me dar os próximos seis registros", não vou chegar muito longe em minha aplicação. Para usar a linguagem PL/SQL, é preciso ter atenção aos detalhes - em termos de sintaxe. Portanto, este capítulo aborda as regras fundamentais da linguagem que o ajudarão a conversar com o compilador PL/SQL - a estrutura de blocos PL/SQL, conjunto de caracteres, unidades léxicas e a palavra-chave PRAGMA.

## Estrutura de Bloco do PL/SQL
No PL/SQL, assim como na maioria das outras linguagens procedurais, o menor agrupamento significativo de código é conhecido como bloco. Um bloco é uma unidade de código que fornece limites de execução e escopo para declarações de variáveis e tratamento de exceções. O PL/SQL permite criar blocos anônimos (blocos de código sem nome) e blocos nomeados, que podem ser pacotes, procedimentos, funções, triggers ou tipos de objeto.

Um bloco PL/SQL possui até quatro seções diferentes, sendo apenas uma obrigatória:

- Header:
Usado apenas para blocos nomeados. O cabeçalho determina a forma como o bloco nomeado ou programa deve ser chamado. Opcional.

- Declaration section:
Identifica as variáveis, cursores e subblocos referenciados nas seções de execução e exceção. Opcional.

- Execution section:
Contém as declarações que o mecanismo de execução do PL/SQL irá executar em tempo de execução. Obrigatório.

- Exception section:
Trata exceções no processamento normal (avisos e condições de erro). Opcional.

A Figura 3-2 mostra um procedimento contendo as quatro seções dos elementos de um bloco. Este bloco em particular começa com a palavra-chave PROCEDURE e, como todos os blocos, termina com a palavra-chave END.

### Blocos Anônimos
Quando alguém deseja permanecer anônimo, essa pessoa fica sem nome. É a mesma coisa com o bloco anônimo em PL/SQL, que é mostrado na Figura 3-3: ele não possui uma seção de cabeçalho, começando em vez disso com DECLARE ou BEGIN. Isso significa que ele não pode ser chamado por nenhum outro bloco - não possui um identificador para referência. Em vez disso, os blocos anônimos servem como contêineres que executam instruções PL/SQL, geralmente incluindo chamadas a procedimentos e funções. Como um bloco anônimo pode ter suas próprias seções de declaração e exceção, os desenvolvedores frequentemente aninham blocos anônimos para fornecer um escopo para identificadores e tratamento de exceções dentro de um programa maior.

A sintaxe geral de um bloco anônimo PL/SQL é a seguinte:

    [ DECLARE   ... declaration statements ... ]
    BEGIN   ... one or more executable statements ...
    [ EXCEPTION
        ... exception handler statements ... ]
    END;

Os colchetes indicam uma parte opcional da sintaxe. Você deve ter as instruções BEGIN e END, e deve ter pelo menos uma instrução executável. Aqui estão alguns exemplos:

- Um bloco anônimo mínimo:

    BEGIN
        DBMS_OUTPUT.PUT_LINE(SYSDATE);
    END;

- Um bloco anônimo funcionalmente semelhante, adicionando uma seção de declaração:

    DECLARE
        l_right_now VARCHAR2(9);
    BEGIN
        l_right_now := SYSDATE;
        DBMS_OUTPUT.PUT_LINE (l_right_now);
    END;

- O mesmo bloco, mas incluindo um manipulador de exceção:

    DECLARE
        l_right_now VARCHAR2(9);
    BEGIN
        l_right_now := SYSDATE;
        DBMS_OUTPUT.PUT_LINE (l_right_now);
    EXCEPTION
        WHEN VALUE_ERROR
        THEN
            DBMS_OUTPUT.PUT_LINE('I bet l_right_now is too small '
                || 'for the default date format!');
    END;

Blocos anônimos executam uma série de declarações e depois terminam, agindo assim como procedimentos. Na verdade, todos os blocos anônimos são procedimentos anônimos. Eles são usados em vários ambientes onde o código PL/SQL é executado diretamente ou incluído em algum programa nesse ambiente. Exemplos comuns incluem:

- Database triggers
Conforme discutido no Capítulo 19, triggers de banco de dados executam blocos anônimos quando certos eventos ocorrem.

- Ad hoc commands or script files
No SQLPlus ou em ambientes de execução similares, blocos anônimos são executados a partir de blocos digitados manualmente ou de scripts que chamam programas armazenados. Além disso, o comando EXECUTE do SQLPlus traduz seu argumento em um bloco anônimo, envolvendo-o entre as palavras-chave BEGIN e END.

- Compiled 3GL (third generation language) program
No Pro*C ou OCI, blocos anônimos podem ser a forma pela qual você pode incorporar chamadas a programas armazenados.

Em cada caso, o objeto de envolvimento - seja um trigger, um ambiente de linha de comando ou um programa compilado - fornece o contexto e possivelmente um meio de nomear o programa.

### Blocos Nomeados
Embora blocos PL/SQL anônimos sejam indispensáveis, a maioria do código que você escreverá estará em blocos nomeados. Você já viu alguns exemplos curtos de stored procedures neste livro (como na Figura 3-1), então você provavelmente sabe que a diferença está no cabeçalho. O cabeçalho de uma procedure se parece com isso:

    PROCEDURE [schema.]name [ ( parameter [, parameter ... ] ) ]
        [AUTHID {DEFINER | CURRENT_USER}]

O cabeçalho de uma função tem uma sintaxe similar, mas inclui a palavra-chave RETURN:

    FUNCTION [schema.]name [ ( parameter [, parameter ... ] ) ]
        RETURN return_datatype
        [AUTHID {DEFINER | CURRENT_USER}]
        [DETERMINISTIC]
        [PARALLEL ENABLE ...]
        [PIPELINED [USING...] | AGGREGATE USING...]

Como o Oracle permite que você invoque algumas funções de dentro de instruções SQL, o cabeçalho da função inclui mais componentes opcionais do que o cabeçalho do procedimento, correspondendo às dimensões de funcionalidade e desempenho do ambiente de execução do SQL.

Para uma discussão mais completa sobre procedimentos e funções, consulte o Capítulo 17.

### Blocos Aninhados
PL/SQL compartilha com Ada e Pascal a definição adicional de ser uma linguagem de estrutura de blocos, ou seja, blocos podem "aninhar-se" dentro de outros blocos. Em contraste, a linguagem C possui blocos, mas o C padrão não é estritamente de estrutura de blocos, pois seus subprogramas não podem ser aninhados.

Aqui está um exemplo em PL/SQL mostrando um procedimento contendo um bloco anônimo e aninhado:

    PROCEDURE calc_totals
    IS
        year_total NUMBER;
    BEGIN
        year_total := 0;
        /* Beginning of nested block */
        DECLARE
            month_total NUMBER;
        BEGIN
            month_total := year_total / 12;
        END set_month_total;
        /* End of nested block */

    END;

Os delimitadores /* e */ indicam comentários (consulte "Comentários" na página 75). Você pode aninhar blocos anônimos dentro de blocos anônimos em mais de um nível, como mostrado na Figura 3-4.

Outros termos que você pode ouvir para blocos aninhados são bloco fechado, bloco filho ou subbloco; o bloco PL/SQL externo pode ser chamado de bloco envolvente ou bloco pai.

Em geral, a vantagem de aninhar um bloco é que isso lhe dá uma maneira de controlar tanto o escopo quanto a visibilidade em seu código.

### Escopo
Em qualquer linguagem de programação, o termo escopo refere-se à forma de identificar qual "coisa" é referida por um determinado identificador. Se você tiver mais de uma ocorrência de um identificador, as regras de escopo da linguagem definem qual será usada. Controlar cuidadosamente o escopo do identificador não apenas aumentará seu controle sobre o comportamento em tempo de execução, mas também reduzirá a probabilidade de um programador modificar acidentalmente a variável errada.

No PL/SQL, variáveis, exceções, módulos e algumas outras estruturas são locais ao bloco que as declara. Quando o bloco para de ser executado, você não pode mais fazer referência a nenhuma dessas estruturas. Por exemplo, no procedimento calc_totals mencionado anteriormente, posso fazer referência a elementos do bloco externo, como a variável year_total, em qualquer parte do procedimento; no entanto, elementos declarados dentro de um bloco interno não estão disponíveis para o bloco externo.

Cada variável PL/SQL tem um escopo: a região de uma unidade de programa (bloco, subprograma ou pacote) na qual essa variável pode ser referenciada. Considere a seguinte definição de pacote:

    PACKAGE scope_demo
    IS
        g_global   NUMBER;

        PROCEDURE set_global (number_in IN NUMBER);
    END scope_demo;

    PACKAGE BODY scope_demo
    IS
        PROCEDURE set_global (number_in IN NUMBER)
        IS
            l_salary  NUMBER := 10000;
            l_count   PLS_INTEGER;
        BEGIN

            <<local_block>>
            DECLARE
                l_inner   NUMBER;
            BEGIN
                SELECT COUNT (*)
                INTO l_count
                FROM employees
                WHERE department_id = l_inner AND salary > l_salary;
            END local_block;

            g_global := number_in;
        END set_global;
    END scope_demo;

A variável scope_demo.g_global pode ser referenciada a partir de qualquer bloco em qualquer esquema que tenha autoridade EXECUTE no escopo_demo.

A variável l_salary pode ser referenciada apenas dentro do procedimento set_global.

A variável l_inner pode ser referenciada apenas dentro do bloco local ou aninhado; observe que usei o rótulo "local_block" para dar um nome a esse bloco aninhado.

### Qualifique todas as referências a variáveis e colunas em instruções SQL
Nenhuma das variáveis ou referências a colunas no último exemplo de código foi qualificada com o nome do escopo. Aqui está outra versão do mesmo corpo de pacote, mas desta vez com referências qualificadas (em negrito):

    PACKAGE BODY scope_demo
    IS
        PROCEDURE set_global (number_in IN NUMBER)
        IS
            l_salary  NUMBER := 10000;
            l_count   PLS_INTEGER;
        BEGIN

            <<local_block>>
            DECLARE
                l_inner   PLS_INTEGER;
            BEGIN
                SELECT COUNT (*)
                INTO set_global.l_count
                FROM employees e
                WHERE e.department_id = local_block.l_inner
                AND e.salary > set_global.l_salary;
            END local_block;

            scope_demo.g_global := set_global.number_in;
        END set_global;
    END scope_demo;

Com essas alterações, cada referência a uma coluna e variável é qualificada pelo alias da tabela, pelo nome do pacote, pelo nome da função ou pelo nome do bloco aninhado.

Agora você sabe que pode fazer isso, mas por que se preocupar? Existem várias razões muito boas:

- Para melhorar a legibilidade do seu código

- Para evitar bugs que podem surgir quando os nomes das variáveis são iguais aos nomes das colunas

- Para aproveitar ao máximo o rastreamento de dependências detalhado disponível no Oracle Database 11g

Vamos dar uma olhada mais detalhada nas duas primeiras razões. A terceira será descrita no Capítulo 20.

#### Melhore a legibilidade
Praticamente toda instrução SQL incorporada em programas PL/SQL contém referências a colunas e variáveis. Em pequenas e simples instruções SQL, é relativamente fácil distinguir entre essas diferentes referências. No entanto, na maioria das aplicações, você encontrará instruções SQL muito longas e extremamente complexas que contêm dezenas ou até centenas de referências a colunas e variáveis.

Se você não qualificar essas referências, é muito mais difícil distinguir de relance entre variáveis e colunas. Com esses qualificadores, o código se auto-documenta claramente a origem dessas referências.

"Espere um minuto", posso ouvir você dizer. "Nós usamos convenções de nomenclatura claramente definidas para distinguir entre colunas e variáveis. Todas as nossas variáveis locais começam com 'l_', então sabemos imediatamente se o identificador é uma variável local."

Isso é uma ideia muito boa; todos nós devemos ter (e seguir) convenções estabelecidas para que os nomes de nossos identificadores revelem informações adicionais sobre eles (por exemplo, se é um parâmetro ou uma variável? Qual é o seu tipo de dados?).

No entanto, embora úteis, as convenções de nomenclatura não são suficientes para garantir que, ao longo do tempo, o compilador PL/SQL sempre interpretará seus identificadores como você pretendia.

#### Evitar bugs por meio de qualificadores
Se você não qualificar as referências a todas as variáveis PL/SQL em suas instruções SQL incorporadas, o código que funciona corretamente hoje pode deixar de funcionar no futuro. E pode ser muito difícil descobrir o que deu errado.

Considere novamente esta instrução SQL incorporada que não qualifica suas referências:

    SELECT COUNT (*)
        INTO l_count
        FROM employees
        WHERE department_id = l_inner AND salary > l_salary;

Hoje, l_salary se refere inequivocamente à variável l_salary declarada no procedimento set_global. Testo meu programa - funciona! E então ele vai para produção e todos estão felizes.

Dois anos se passam e os usuários pedem ao nosso DBA para adicionar uma coluna à tabela employees para registrar algo descrito como "salário limitado". O DBA decide nomear essa coluna como "l_salary".

Você consegue ver o problema?

Dentro de uma instrução SQL incorporada, o banco de dados Oracle sempre tenta resolver referências de identificadores não qualificados primeiro como colunas em uma das tabelas especificadas. Se não encontrar correspondência, ele tentará resolver a referência como uma variável PL/SQL em escopo. Com a coluna l_salary adicionada à tabela employees, minha referência não qualificada a l_salary na instrução SELECT não será mais resolvida como a variável PL/SQL. Em vez disso, o banco de dados a interpretará como a coluna da tabela. A consequência?

Meu pacote scope_demo ainda compila sem erros, mas a cláusula WHERE dessa consulta não se comportará como eu espero. O banco de dados não usará o valor da variável l_salary, mas sim comparará o valor da coluna salary em uma linha da tabela employees com o valor da coluna l_salary nessa mesma linha.

Isso pode ser um bug muito difícil de rastrear e corrigir! Em vez de depender apenas de convenções de nomenclatura para evitar "colisões" entre identificadores, você também deve qualificar as referências a todos os nomes de colunas e variáveis nessas instruções SQL incorporadas. Assim, seu código terá menos probabilidade de se comportar erraticamente no futuro, à medida que suas tabelas subjacentes evoluem.

### Visibilidade
Uma vez que uma variável está em escopo, outra propriedade importante é a sua visibilidade, ou seja, se você pode se referir a ela usando apenas seu nome ou se precisa adicionar um prefixo na frente dela.

#### Identificadores visíveis
Primeiro, gostaria de fazer uma observação sobre o caso trivial:

    DECLARE
        first_day DATE;
        last_day DATE;
    BEGIN
        first_day := SYSDATE;
        last_day := ADD_MONTHS (first_day, 6);
    END;

Como as variáveis first_day e last_day são declaradas no mesmo bloco em que são usadas, posso convenientemente me referir a elas usando apenas seus identificadores "não qualificados", também conhecidos como identificadores visíveis. Um identificador visível pode se referir a qualquer um dos seguintes:

- Um identificador declarado no bloco atual.

- Um identificador declarado em um bloco que envolve o bloco atual.

- Um objeto de banco de dados independente (tabela, visualização, sequência, etc.) ou objeto PL/SQL (procedimento, função, tipo) que você possui.

- Um objeto de banco de dados independente ou objeto PL/SQL no qual você possui a privilégio adequado e que é o alvo de um sinônimo do Oracle que você pode ver.

- Uma variável de índice de loop (visível e em escopo apenas dentro do corpo do loop).

O PL/SQL também permite a possibilidade de se referir a itens em escopo que não são diretamente visíveis, como a próxima seção descreve.

#### Identificadores qualificados
Um exemplo comum de um identificador que não é visível é qualquer coisa declarada em uma especificação de pacote, como uma variável, tipo de dado, procedimento ou função. Para referenciar um desses elementos fora do pacote, você precisa apenas prefixá-lo com um qualificador pontuado, semelhante à forma como você qualificaria um nome de coluna com o nome de sua tabela. Por exemplo:

- price_util.compute_means
Um programa chamado compute_means dentro do pacote price_util

- math.pi
Uma constante chamada pi, declarada e inicializada no pacote math

(Embora as descrições indiquem que tipo de globais são, você não pode necessariamente dizer apenas olhando - definitivamente um argumento a favor de boas convenções de nomenclatura!)

Você pode usar um qualificador adicional para indicar o proprietário do objeto. Por exemplo:

    scott.price_util.compute_means

poderia se referir ao procedimento compute_means no pacote price_util, de propriedade da conta de usuário Oracle scott.

#### Qualificar nomes de identificadores com nomes de módulos.
Quando necessário, o PL/SQL oferece muitas maneiras de qualificar um identificador para que uma referência ao identificador possa ser resolvida. Usando pacotes, por exemplo, você pode criar variáveis com escopo global. Suponha que eu crie um pacote chamado company_pkg e declare uma variável chamada last_company_id na especificação desse pacote, da seguinte forma:

    PACKAGE company_pkg
    IS
        last_company_id NUMBER;
        ...
    END company_pkg;

Em seguida, posso fazer referência a essa variável fora do pacote, desde que eu prefixe o nome do identificador com o nome do pacote:

    IF new_company_id = company_pkg.last_company_id THEN

Por padrão, um valor atribuído a uma dessas variáveis de nível de pacote persiste durante a duração da sessão atual do banco de dados; ele não sai de escopo até que a sessão seja desconectada.

Também posso qualificar o nome de um identificador com o módulo no qual ele é definido:

    PROCEDURE calc_totals
    IS
        salary NUMBER;
    BEGIN
        ...
        DECLARE
            salary NUMBER;
        BEGIN
            salary := calc_totals.salary;
        END;
        ...
    END;

A primeira declaração de "salary" cria um identificador cujo escopo é o procedimento inteiro. No bloco aninhado, porém, eu declaro outro identificador com o mesmo nome. Portanto, quando faço referência à variável "salary" dentro do bloco interno, ela será sempre resolvida primeiro em relação à declaração no bloco interno, onde essa variável é visível sem nenhuma qualificação. Se eu quiser fazer referência à variável "salary" em todo o procedimento dentro do bloco interno, devo qualificar o nome da variável com o nome do procedimento (calc_totals.salary).

Essa técnica de qualificar um identificador também funciona em outros contextos. Considere o que acontecerá quando você executar um procedimento como este (order_id é a chave primária da tabela "orders"):

    PROCEDURE remove_order (order_id IN NUMBER)
    IS
    BEGIN
        DELETE orders WHERE order_id = order_id; -- Oops!
    END;

Este código irá excluir tudo na tabela "orders" independentemente do "order_id" que você passar. A razão disso é que a resolução de nomes do SQL corresponde primeiro aos nomes das colunas em vez dos identificadores PL/SQL. A cláusula WHERE "order_id = order_id" é sempre verdadeira, então todos os seus dados desaparecem. Uma maneira de corrigir isso seria:

    PROCEDURE remove_order (order_id IN NUMBER)
    IS
    BEGIN
        DELETE orders WHERE order_id = remove_order.order_id;
    END;

Isso força o parser a fazer a coisa certa. (Isso funcionará mesmo se você tiver uma função em um pacote chamada remove_order.order_id.)

O PL/SQL faz um esforço considerável e estabeleceu muitas regras para determinar como resolver esses conflitos de nome. Embora seja bom estar ciente dessas questões, você geralmente estará muito melhor se não precisar confiar nessas diretrizes. Crie código defensivamente! Se você não quer qualificar cada variável para mantê-la única, precisará usar convenções de nomenclatura cuidadosas para evitar esse tipo de colisão de nomes.

#### Programas aninhados
Para concluir a discussão sobre aninhamento, escopo e visibilidade, o PL/SQL também oferece um recurso especialmente importante conhecido como programa aninhado. Um programa aninhado é um procedimento ou função que aparece completamente dentro da seção de declaração do bloco externo. De forma significativa, o programa aninhado pode fazer referência a quaisquer variáveis e parâmetros declarados anteriormente no bloco externo, como demonstrado neste exemplo:

    PROCEDURE calc_totals (fudge_factor_in IN NUMBER)
    IS
        subtotal NUMBER := 0;
        /* Beginning of nested block (in this case a procedure). Notice
        |  we're completely inside the declaration section of calc_totals.
        */
        PROCEDURE compute_running_total (increment_in IN PLS_INTEGER)
        IS
        BEGIN
            /* subtotal, declared above, is both in scope and visible */
            subtotal := subtotal + increment_in * fudge_factor_in;
        END;
        /* End of nested block */
    BEGIN
        FOR month_idx IN 1..12
        LOOP
            compute_running_total (month_idx);
        END LOOP;
        DBMS_OUTPUT.PUT_LINE('Fudged total for year: ' || subtotal);
    END;

Programas aninhados podem tornar seu programa mais legível e fácil de manter, além de permitir que você reutilize a lógica que aparece em vários lugares no bloco. Para obter mais informações sobre esse tópico, consulte o Capítulo 17.

## O Conjunto de Caracteres PL/SQL
Um programa PL/SQL consiste em uma sequência de instruções, cada uma composta por uma ou mais linhas de texto. Os caracteres precisos disponíveis para você dependerão do conjunto de caracteres do banco de dados que você está usando. Por exemplo, a Tabela 3-1 ilustra os caracteres disponíveis no conjunto de caracteres US7ASCII.

- Letters: A–Z, a–z

- Digits: 0–9

- Symbols: ~ ! @ # $ % * () _ − + = | : ; “ ‘ < > , . ? / ^

- Whitespace: Tab, space, newline, carriage return

Cada palavra-chave, operador e token em PL/SQL é formado por várias combinações de caracteres neste conjunto de caracteres. Agora você só precisa descobrir como juntar todos eles!

E agora, algumas curiosidades reais sobre o PL/SQL. A documentação da Oracle, assim como edições anteriores deste livro, lista o ampersand, as chaves e os colchetes como parte do conjunto de caracteres padrão:

    & { } [ ]

Embora todos os caracteres sejam permitidos em strings literais, a Oracle não parece usar esses cinco caracteres específicos em nenhuma parte visível do PL/SQL. Além disso, não há uma maneira direta de usar esses caracteres em identificadores definidos pelo programador.

Independentemente da sua memória para essas curiosidades, é importante lembrar que o PL/SQL é uma linguagem que não diferencia maiúsculas de minúsculas. Ou seja, não importa como você digita as palavras-chave e identificadores; letras maiúsculas são tratadas da mesma forma que letras minúsculas, a menos que estejam envolvidas por delimitadores que as tornem uma string literal. Por convenção, os autores deste livro preferem usar letras maiúsculas para palavras-chave incorporadas à linguagem (e certos identificadores usados pela Oracle como nomes de funções e pacotes incorporados) e letras minúsculas para identificadores definidos pelo programador.

Uma série desses caracteres - tanto isoladamente quanto em combinação com outros caracteres - tem um significado especial no PL/SQL. A Tabela 3-2 lista esses símbolos especiais:


