Host
Parte fisica da nossa aplicACAO

parte de criação.
 O que eu preciso fazer para criar? Como eu vou cuidar da parte de subir máquinas e servidores?
 é sobre cuidar do host, cuidar do local, realmente - físico ou virtual, onde os nossos sistemas vão estar.

 É como vamos lidar com os servidores.
 vamos ter vários servidores de aplicação, vários servidores de bancos de dados,
 processamento de tarefas em plano de fundo, processamento de mensagens e de agendamento de tarefas.
 precisamos manter isso em servidores.

 cada microsserviço pode ter vários componentes.
 Onde vamos armazenar? Ou como vamos fazer para mantermos todo esse sistema facilitando o desenvolvimento?

 Nós precisamos organizar bem, de forma que cada componente do nosso microsserviço tenha um lugar bem definido,
 que eles consigam se comunicar e nós consigamos fazer tanto desenvolvimento quanto deploy de forma facilitada.

 temos sistemas em cloud. Eles estão cada vez mais famosos hoje em dia. Azure, AWS e Google Cloud. Existem vários serviços de cloud onde você pode simplesmente também utilizar um script de build desses, um provisionador, para manter sua máquina pronta.
 existem tipos de máquinas já específicas para determinadas tarefas, que nem precisamos nos preocupar: load balancing, DNS, cache - existem máquinas específicas para isso em serviços de cloud.
  Isso facilita muito o nosso processo de deploy dando muitas ferramentas especializadas e a cada vez mais, um custo-benefício maior.

  Nós conseguimos ter algo muito customizável e várias ferramentas à nossa disposição,
  mas e para rodar na máquina da equipe de desenvolvimento? Como fazemos para rodarmos um ambiente local para desenvolvermos?
   hoje em dia, orquestradores de containers, Kubernetes, Docker Swarm
   nós conseguimos subir todos os microsserviços utilizando containers, é muito mais leve do que máquinas virtuais.  Docker,


Criando um novo Servico

processo de criação de um novo serviço
começando a separar o meu monólito em vários microsserviços,
utilizando arquitetura de microsserviços

Primeiro, antes de tudo, precisamos configurar um repositório
vários repositórios, um repositório ?
para cada microsserviço;
abordagem “monorepo”, onde todos os meus microsserviços estão no mesmo repositório?

É interessante que tenhamos algum padrão. Como nós vamos criar o próximo microsserviço? Nós podemos, por exemplo, ter um Dockerfile para criarmos todos os nossos serviços. Todos vão estar em máquinas desse tipo etc.

é muito importante que nós não só tenhamos testes, mas que esses testes sejam realmente confiáveis e que nós tenhamos uma boa pirâmide de testes, com muitos testes garantindo a nossa lógica.

Testes de unidade - que nós tenhamos testes que garantam a comunicação com outros microsserviços. Nossos testes de integração e que nós tenhamos alguns testes da aplicação como um todo, ou seja, testes end to end, para garantirmos que nossas entregas e nossos deploys não estejam causando nenhum problema.