# Zéfiro
## Arquitetura
### Versão 1.4

## Histórico de Revisão

| Data | Versão | Descrição | Autor |
|------|--------|-----------|-------|
|09/09/2020|1.0|Definição da arquitetura e tecnologias|Amanda Muniz e Vitor Cardoso|
|11/09/2020|1.1|Criação dos diagramas de pacotes|Amanda Muniz e Vitor Cardoso|
|13/09/2020|1.2|Criação do diagrama de classes e refatoração do diagrama de relações|Amanda Muniz, Luciana Ribeiro e Calebe Rios|
|20/09/2020|1.3|Criação dos tópicos 1, 3 e 4|Amanda Muniz|
|08/10/2020|1.4|Diagramação|Amanda Muniz|


# 1. Introdução
## 1.1 Finalidade
<p align="justify">&emsp;&emsp;Este documento tem como finalidade fornecer uma visão geral da arquitetura do Zéfiro, utilizando-se de diversas visões arquiteturais - tais como a visão de microsserviços e de diagramas - a fim de facilitar o entendimento dos processos e funcionamento de todo o sistema. Tem também como objetivo transmitir as decisões arquiteturais significativas tomadas em relação ao mesmo.</p>

## 1.2 Escopo
<p align="justify">&emsp;&emsp;Através desse documento, é possível obter um melhor entendimento da arquitetura do Zéfiro, permitindo ao leitor compreender o funcionamento de seu sistema, como também a abordagem utilizada para o seu desenvolvimento.</p>

## 1.3 Definições, Acrônimos e Abreviações
| Termo | Definição |
|--|--|
| API | Application Program Interface (Interface de Programação de Aplicações) |
| HTTP | HyperText Transfer Protocol (Protocolo de Transferência de Hipertexto) |

## 1.4 Referências
> JACKSON, Cam; Micro Frontends; Disponível em: <[https://martinfowler.com/articles/micro-frontends.html](https://martinfowler.com/articles/micro-frontends.html)>; Acesso em 10 de setembro de 2020;

> LEWIS, James; FOWLER, Martin; Microsserviços em poucas palavras; Disponível em: <[https://www.thoughtworks.com/pt/insights/blog/microservices-nutshell](https://www.thoughtworks.com/pt/insights/blog/microservices-nutshell)>; Acesso em 20 de setembro de 2020.

> GEERS, Michael; Micro Frontends extending the microsservice idea to frontend development; Disponível em <[https://micro-frontends.org/](https://micro-frontends.org/)>; Acesso em 10 de setembro de 2020.

> DEMEDYUK, Ihor; TSYBULSKYI, Nazar; Flutter vs Native vs React-Native: Examining performance. Disponível em: <[https://medium.com/swlh/flutter-vs-native-vs-react-native-examining-performance-31338f081980](https://medium.com/swlh/flutter-vs-native-vs-react-native-examining-performance-31338f081980)>; Acesso em 10 de setembro de 2020;

> JAYARAM, Prashanth; When to Use (and Not to Use) MongoDB; Disponível em <[https://dzone.com/articles/why-mongodb#:~:text=The%20motivation%20of%20the%20MongoDB,BSON%20documents%20to%20store%20data](https://dzone.com/articles/why-mongodb#:~:text=The%20motivation%20of%20the%20MongoDB,BSON%20documents%20to%20store%20data)>; Acesso em 10 de setembro de 2020;

> Introdução Express/Node. MDN, 2020; Disponível em: <[https://developer.mozilla.org/pt-BR/docs/Learn/Server-side/Express_Nodejs/Introdu%C3%A7%C3%A3o](https://developer.mozilla.org/pt-BR/docs/Learn/Server-side/Express_Nodejs/Introdu%C3%A7%C3%A3o)>; Acesso em 10 de setembro de 2020;

> APIs de geolocalização. Google Maps Platform; Disponível em: <[https://cloud.google.com/maps-platform](https://cloud.google.com/maps-platform)>; Acesso em 10 de setembro de 2020;

> What is Alexa? Amazon Alexa Official Site. Disponível em: <[https://developer.amazon.com/pt-BR/alexa](https://developer.amazon.com/pt-BR/alexa)>; Acesso em 10 de setembro de 2020;


# 2. Representação Arquitetural

## 2.1 Diagrama de Relações

![](./img/relacao.png)

<p align="justify">&emsp;&emsp;O estilo arquitetural de microsserviços é uma abordagem que visa implementar uma aplicação como uma suíte de pequenos serviços. Onde cada um executa um processo próprio e se comunica, geralmente, com requests HTTP. Em 2016, o termo micro frontend foi falado pela primeira vez no Thoughtworks Technology Radar, com o intuito de estender o conceito de microsserviços para o desenvolvimento frontend, onde cada uma desses “serviços” precisam ser completamente isolados dos outros com tecnologias e objetivos próprios.</p>

<p align="justify">&emsp;&emsp;Tendo em vista as principais características desses dois estilos arquiteturais o software Zéfiro será criado com base neles. Onde teremos um microsserviço para o backend, chamado de Zéfiro API e dois micro frontends sendo eles, o Zéfiro APP e o Zéfiro Alexa Skills. Cada um desses três serviços terão seu próprio repositório, de forma que estes possuam ambiente de desenvolvimento, tecnologias, integração contínua e deploy específicos.</p>

<p align="justify">&emsp;&emsp;O software Zéfiro será dividido em três serviços independentes:</p>

-   Zéfiro APP
    
-   Zéfiro Alexa Skills
    
-   Zéfiro API

<p align="justify">&emsp;&emsp;Para o desenvolvimento do software, faz-se necessário o consumo de dados de fontes externas, sendo elas:</p>

-   Google Maps API
    

## 2.2 Representação dos Serviços

### 2.2.1 Zéfiro APP

<p align="justify">&emsp;&emsp;O Zéfiro APP será uma aplicação mobile responsável pelo contato direto com o usuário. Esta precisará seguir uma arquitetura da informação bem definida e garantir acessibilidade. Ela é responsável também por exibir um gráfico com o histórico do indicador de qualidade do ar, apresentar informações sobre quais elementos o usuário está respirando naquele momento e um mapa com as estações de monitoramento do ar. Precisa ainda enviar notificação para o usuário e exibir um alerta de fumaças.</p>

### 2.2.2 Zéfiro Alexa Skills

<p align="justify">&emsp;&emsp;O Zéfiro Alexa Skills será uma aplicação que faz interação com o usuário por meio de comandos de voz. Ela será responsável por responder como está a qualidade do ar, com base na faixa de qualidade do ar internacional, qual foi a qualidade do ar nos últimos sete dias e quais são os elementos químicos que o usuário está respirando no momento do seu pedido.</p>

### 2.2.3 Zéfiro API
<p align="justify">&emsp;&emsp;
O Zéfiro API é responsável por lidar com o core do projeto, - monitoramento da qualidade do ar. Para isso ele possui diversas funcionalidades. A principal delas é o cálculo da qualidade do ar, feita de acordo com a faixa de qualidade do ar internacional e utilizando as informações dos poluentes coletados, para que com isso possa existir a criação de gráficos que serão apresentados ao usuário.</p>

<p align="justify">&emsp;&emsp;Além do cálculo, as informações de quais poluentes estão presentes, suas quantidades e o indicativo de fumaça serão disponibilizados para o usuário. Além disso, o Zéfiro APP precisará fazer o envio de notificações ao usuário sempre que a qualidade do ar estiver baixa.</p>

<p align="justify">&emsp;&emsp;A última funcionalidade presente neste serviço é a exibição de um mapa contendo todas as estações de monitoramento do ar e seus respectivos status. Para isso ser feito será necessário o consumo da Google Maps API, de forma que auxilie a criação deste mapa de forma mais segura.</p>

## 2.3 Tecnologias

### 2.3.1 Flutter

<p align="justify">&emsp;&emsp;O Flutter é o framework construído pela Google com objetivo de facilitar o desenvolvimento de aplicativos móveis, multiplataforma. Utiliza o Dart como linguagem de programação.
As principais alternativas à escolha do flutter são: React-Native e desenvolvimento nativo. Ao comparar as alternativas apresentadas o flutter foi escolhido pois, apresenta melhor desempenho em alguns aspectos como memória e uso de CPU, principalmente comparado ao React-Native. Já em comparação com o desenvolvimento nativo, apesar do desempenho ser muito parecido, o flutter vence pela possibilidade do desenvolvimento multiplataforma, exigindo menos recursos para alcançar um público maior. Além dos aspectos técnicos de cada abordagem, foi levada em conta a familiaridade de parte da equipe com o flutter.</p>

### 2.3.2 MongoDB

<p align="justify">&emsp;&emsp;O MongoDB é uma base de dados baseada em NoSQL, orientada à objetos, que são mantidos como documentos dentro de coleções, em vez de colunas dentro de tabelas, como é feito em bancos relacionais. O MongoDB apresenta características como: alta disponibilidade, alta performance, fácil escalabilidade, flexibilidade e possui recursos para auxiliar aplicações baseadas em dados geoespaciais, tais como o Zéfiro. Além dos aspectos técnicos do MongoDB, foi levada em conta a experiência da equipe com esta tecnologia.</p>

### 2.3.3 NodeJS

<p align="justify">&emsp;&emsp;Node Js é um ambiente de execução, open-source, que permite o desenvolvimento de aplicações utilizando o JavaScript como linguagem de programação. As principais vantagens da escolha do Node Js são: Performance, disponibilidade e variedade de pacotes reutilizáveis, comunidade/ecossistema muito ativo, e alta disponibilidade de documentação. Além destas vantagens, o fato da equipe possuir experiência com esta tecnologia, também motivou a escolha.</p>

### 2.3.4 Alexa

<p align="justify">&emsp;&emsp;A Alexa é um serviço de voz baseado em nuvem da Amazon. É compatível com diversos dispositivos, e permite que o usuário interaja com a tecnologia, de forma mais intuitiva. O Alexa Skill Kit será utilizado no desenvolvimento do Zéfiro Alexa Skill, disponibilizando ao usuário uma interface alternativa para uso das funcionalidades do Zéfiro.</p>

### 2.3.5 Google Maps API

<p align="justify">&emsp;&emsp;Trabalhar com dados relacionados ao monitoramento da qualidade do ar, através de estações distribuídas geograficamente, traz a necessidade da obtenção dos respectivos dados geográficos. O Google Maps Platform possui diversos serviços para fornecimento deste tipo de dado, e o valor cobrado é proporcional ao uso. É uma plataforma de alta disponibilidade e confiabilidade, além de fornecer um crédito mensal gratuito, disponibiliza serviços para fornecimento de mapas estáticos e dinâmicos, gratuitamente, dentro da taxa de uso estabelecida, para uso em dispositivos móveis.</p>

# 3. Metas e Restrições de Arquitetura

## 3.1 Restrições Tecnológicas

<p align="justify">&emsp;&emsp;Para o desenvolvimento do Zéfiro serão utilizadas as seguintes tecnologias:</p>

- Alexa Skills Kit: Conjuntos de ferramentas disponibilizados pela Amazon usados para a criação de novas skills.
- Dart: Linguagem base utilizada no Flutter.
- Flutter: Framework para desenvolvimento mobile.
- Javascript: Linguagem base utilizada no NodeJS.
- NodeJS: Plataforma de aplicação utilizada no desenvolvimento do backend.
- MongoDB: Software utilizado para o banco de dados.

# 4. Visão Lógica

## 4.1 Visão Geral

<p align="justify">&emsp;&emsp;O software Zéfiro é construído utilizando a tecnologia Flutter na linguagem Dart e o kit de skills da Alexa, sobre a plataforma NodeJS em linguegem Javascript na API. O objetivo da Alexa Skills Kit é disponibilizar ferramentas para a criação de softwares que extraiam a intenção do usuário através de comandos de voz e retornem algo de valor. O Zéfiro terá uma versão mobile e uma versão por comando de voz que usarão dados recebidos do Zéfiro API. Este será desenvolvido na plataforma NodeJS, que é um ambiente de tempo de execução que executa o código em Javascript para escrever ferramentas de linha de comando e para scripst do lado do servidor, capaz de executar uma entrada/saída assícronna, que permite que outro processamento continue antes que a transmissão tenha encerrado. </p>

## 4.2 Pacotes de Design Significativos do Ponto de Vista da Arquitetura

### 4.2.1 Diagrama de pacotes

#### 4.2.1.1 Diagrama de pacotes Zéfiro-APP

![](./img/pacote1.png)

<p align="justify">&emsp;&emsp;A organização interna do serviço de front-end será feito utlizando quatro pacotes principais, o <i>lib</i>, o <i>tests</i>, o <i>android</i> e o <i>iOS</i>. Os dois primeiros são os que guardaram toda a lógica e código fonte do Zéfiro-APP. Enquanto as pastas <i>android</i> e <i>iOS</i> guardarão a lógica responsável por fazer o aplicativo funcionar nos dois sistemas.</p>

#### 4.2.1.2 Diagrama de pacotes Zéfiro-API

![](./img/pacote2.png)

<p align="justify">&emsp;&emsp;O serviço de backend Zéfiro-API será organizado com uma pasta principal, chamada de <i>src</i> e outras seis pastas para melhor divisão do código-fonte. O pacote <i>db</i> é onde ficarão as conexões com o banco de dados MongoDB; o <i>models</i> guardará as classes com seus respectivos métodos; o <i>requests</i> terá todas as requisições que o Zéfiro-API precisará fazer para sistemas externos; o <i>tests</i> terá os testes unitários feitos no sistema; o <i>schemas</i> guardará as tabelas do banco de dados; e, por fim, o <i>utils</i> terá todo e qualquer código que auxilie no funcionamento do Zéfiro-API.</p>

### 4.2.2 Diagrama de Classes

![](./img/classes.png)

<p align="justify">&emsp;&emsp;Para o desenvolvimento do software Zéfiro, será necessário a criação de duas classes, <i>Station</i> e <i>Notification</i>. A primeira destas é responsável por guardar os dados que serão recebidos das estações de monitoramente via requisição HTTP. Ela é a classe principal do sistema, pois é ela que guarda o cerne do sistema. O cálculo do índice de qualidade do ar, a lista quantidade de poluentes no ar, a lista de estações e a criação dos gráficos serão métodos dela. Já a segunda classe, <i>Notification</i>, será responsável por lidar com os três tipos de notificações existentes no software. Ela não terá atributos, pois as informações necessários para seus metódos serão recebidos tanto da classe Station quanto da requisição do Zéfiro-APP.</p>

### 4.2.3 Diagrama de Classes

![](./img/sequencia.png)

<p align="justify">&emsp;&emsp;O diagrama de sequência descreve tanto a interação do usuário com o sistema como a interação entre serviços internos e externos. Todas as atividades que deverão ser realizadas pelo Zéfiro estão descritas de forma sequencial por meio de atividades de pedido e retorno. Além disso, indica a duração total que cada serviço precisa para realizar todas as atividades das quais é responsável.</p> 

