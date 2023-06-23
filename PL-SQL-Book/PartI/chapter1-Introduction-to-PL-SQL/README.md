# Introduction to PL/SQL
PL/SQL significa "Procedural Language extensions to the Structured Query Language" (Extensões de Linguagem Procedural para a Linguagem de Consulta Estruturada). SQL é a linguagem agora ubíqua para consultar e atualizar - não importa o nome - bancos de dados relacionais. A Oracle Corporation introduziu o PL/SQL para superar algumas limitações do SQL e fornecer uma solução de programação mais completa para aqueles que buscavam construir aplicativos críticos para o sucesso das missões para serem executados no banco de dados Oracle. Este capítulo apresenta o PL/SQL, suas origens e suas várias versões. Ele oferece um resumo rápido do PL/SQL na versão mais recente do Oracle, Oracle Database 12c. Por fim, ele fornece um guia para recursos adicionais para desenvolvedores PL/SQL e algumas palavras de conselho.

## What Is PL/SQL?:
A linguagem PL/SQL da Oracle possui várias características distintivas:

- É uma linguagem altamente estruturada, legível e acessível:

    Se você é novo na programação, o PL/SQL é um ótimo lugar para começar. Você descobrirá que é uma linguagem fácil de aprender e rica em palavras-chave e estrutura que expressam claramente a intenção do seu código. Se você possui experiência em outras linguagens de programação, se adaptará facilmente à nova sintaxe.

- É uma linguagem padrão e portátil para o desenvolvimento Oracle:

    Se você escrever um procedimento ou função PL/SQL para ser executado no banco de dados Oracle em seu laptop, poderá mover esse mesmo procedimento para um banco de dados na rede corporativa e executá-lo lá sem nenhuma alteração (supondo a compatibilidade das versões do Oracle, é claro!). "Escreva uma vez, execute em qualquer lugar" foi o lema do PL/SQL muito antes do surgimento do Java. No entanto, para o PL/SQL, "em qualquer lugar" significa "em qualquer lugar onde haja um banco de dados Oracle".