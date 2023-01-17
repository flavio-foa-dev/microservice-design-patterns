git clone --recursive https://github.com/CViniciusSDias/alura-ms.git
local dos servicos para estudo

 precisar configurar uma conta do gmail para realizar esse envio.
 Para isso, defina no docker-compose.yml as variáveis
 GMAIL_USER
 GMAIL_PASSWORD



- projeto real que usa microsserviços;
- separação de componentes;
- comunicação assíncrona acontecendo entre serviços.

- organização de projetos e multi vs;
- vantagens e desvantagens de multrepo;
- conceito de submódulos do Git.
- Analisar a infraestrutura de um projeto com microsserviços;
- tornar serviços independentes;
- como pensar nos 12 fatores pode nos ajudar.

os 12 fatores
twelve factor apps

Jenkins,
Poder ser instalado em qualquer lugar.
Essa característica é do Jenkins. Essa é a definição de "on-premise", que é uma infra própria.

Travis CI
Poder usar em outro servidor (como Bitbucket ou GitLab) sem custo.
Para projetos open source fora do GitHub podemos usar o Travis CI sem nenhum custo nem preocupação com infra on-premise.

GitHub Actions.

- cada projeto pode ter seu processo de build;
- ferramentas como Jenkins, Travis CI e GitHub Actions;
- workflow no GitHub Actions;
- exigindo pull requests e reviews.

cron e um servico.
Através do cron nós podemos agendar tarefas para rodar diariamente, semanalmente e até de minuto em minuto.

- cada projeto pode ter uma arquitetura e design de código diferentes;
- como podemos executar tarefas de plano de fundo;
- como funciona o envio de mensagens usando RabbitMQ.
- possibilidade de ter mais de uma aplicação front-end;
- Optimistic and Pessimistic UI Rendering;
- conceito de micro frontends.