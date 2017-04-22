Estrutura de Projetos da OPS
============================

Para manter o foco de desenvolvimento dos projetos da OPS, este documento visa detalhar a estrutura de projetos que a organização adota para debater, criar e manter os mesmos. Este documento deverá ser atualizado conforme as necessidades detectadas e melhorias apontadas pela comunidade, de forma ser usado como ponto comum de pesquisa onde haja dúvidas já debatidas sobre a estrutura organizacional dos projetos.

Antes de criar um projeto deve ser definidos e documentados seguintes aspectos do mesmo:

* **Objetivo do projeto**: Qual problema especificamente este deve resolver
* **Linguagem predominante**: A linguagem principal que será utilizada no desenvolvimento
* **Segurança de dados**: Detalhes que não podem ser expostos no código fonte do projeto
* **Armazenamento de dados**: Qual estrutura irá armazenar os dados quando projeto estiver em uma instância ou mais
* **Acessibilidade**: Será acessível apenas via outros projetos da OPS ou terá um domínio público?
* **Forma de publicação**: Se este irá usar hookies no github ou terá uma equipe responsável pela publicação nos servidores

Tendo estes dados bem definidos o projeto poderá ser criado na organização e a equipe irá tentar manter, sempre que houver dúvidas sobre o rumo do mesmo, o documento existente no comitê e que deve ter uma referencia no `README.md` do projeto deverá ser consultado para esclarecer, ou ser atualizado conforme as novas necessidades.

Modularidade
------------

Os projetos da OPS, por serem open-source e envolver equipes remotas de pessoas que não compartilham ambiente físico e tem como meio de comunicação sistemas que podem atrasar durante dias respostas e atrapalhar na integração de sistemas, precisam ter os projetos bem modulares para que esse atrito seja reduzido o máximo possível permitindo que os projetos evoluam sem envolver uma grande manutenção em seus similares.

Para isso, a divisão em camadas de projeto é uma maneira muito eficaz, tendo um ponto de integração que deverá comunicar com os demais projetos por meio de API via protocolo HTTP ou hibridos de HTTP dentro de túnel SSH, para operações que necessitem maior segurança.

A estrutura geral será:

* **Dispositivos de backend**: São projetos que são acessados por ativação ou agendamento, que devem realizar a aquisição e atualização de dados utilizados pela OPS.
* **Backend**: Deverá ter acesso ao banco de dados da OPS, se encarregando de armazenar dados proveniente de dispositivos e prover dados aos Frontend.
* **Frontend**: Deverá consumir dados do Backend e interagir com ele simplificando e humanizando a forma de interação dos usuários com os dados existentes no Backend.

Backend
-------

Este deve ser composto de apenas *um* projeto, o qual deve conter acesso a base de dados e demais dispositivos de backend que deverão ser registrados no mesmo, seus protocolos de comunicação, autenticação, etc deverão ser discutidos no projeto de Backend, assim como a linguagem utilizada para sua implementação.

Dispositivos de Backend
-----------------------

Podem ser vários projetos, isso visa ramificar e agilizar a produção, pois sites do governo não seguem padrões de desenvolvimento, então onde uma solução pode funcionar muito bem utilizando PHP para fazer o scraping dos dados, em outra pode necessitar de recursos avançados como Phantomjs ou outros, para resolver as necessidades e acessar os dados desejados. Assim como projetos que podem inclusive montar emails atraves de templates para solicitação de dados de parlamentares.

Contudo todos estes diferentes projetos devem se comunicar de maneira padronizada com o Backend, podendo ser necessário não apenas requisições mas também gatilhos que avisem o Backend a situação da tarefa que este desempenha.

Um exemplo de gatilho é caso o site tenha um captcha para acessar determinada página. O dispositivo pode enviar o captcha ao backend para que seja exibido ao usuário que solicitou os dados. Após preenchimento permitir que o scraper finalize sua operação de aquisição de dados.

Frontend
--------

São considerados frontend todos projetos que vão permitir a pessoas utilizarem dispositivos como computadores, smartphones, tablets, etc, para consumir dados do Backend e iniciar operações de aquisição de novos dados, ou registrar informações manuais no Backend.

As implementações de Frontend não devem depender do Backend para serem entregues, mas sim para comunicar com o mesmo. 

Por exemplo, o Backend não deve necessariamente renderizar nenhum HTML, mas sim entregar dados sempre em formatos comuns a todos os dispositivos como JSON, XML ou YML. Após traduzidos esses dados, o Frontend deverá aplicar essas informações em fragmentos e renderiza-los em um dispositivo. Eliminando assim totalmente a dependência do Backend para existir, apenas necessitando-o para prover seus dados.

Observação sobre **SEO**: Apesar dos spiders hoje em dia lerem sites dinâmicamente gerados por JavaScript, existem limitações quanto as partes que dependem de requisições XHR e via WebSocket, para resolver isso pode ser uma boa solução o uso de entrega de páginas pré renderizadas quando o agente da requisição se identificar como tal.
