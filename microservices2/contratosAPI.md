Contratos Microservices
Um microsserviço, por via de regra, é uma parte de uma aplicação maior, ele é uma micro parte de uma aplicação

quando estamos arquitetando microsserviços, quando estamos pensando em quais microsserviços vão existir
e o que cada um vai ter, nós já temos que ter em mente que existem
contratos entre microsserviços.

Quando um microsserviço expõe uma API, quando ele expõe uma interface pública de comunicação com a sua aplicação, ele está assinando um contrato. Ele está dizendo: “olhe só, cliente que vai acessar a minha API, eu estou me comprometendo a te fornecer estas funcionalidades desta forma aqui”.

Se eu vou mudar de linguagem de programação, se eu vou mudar de banco de dados que eu estou utilizando ou se eu vou trocar de servidor próprio para um servidor em cloud, isso não importa. Nós temos que manter o nosso contrato. Nossa interface tem que continuar funcionando com o cliente.

Aqui nós temos algumas formas de mantermos esse contrato e algumas técnicas de mantermos esse contrato e a evolução.

  Se  atualizar uma dependência, a API deve  continuar  funcionando com essa nova versão de dependência. Isso  é o mínimo que se espera.

  Algumas outras coisas que podemos fazer, modificações aditivas. O que isso quer dizer? Somente adicionarmos funcionalidades, nunca modificarmos como uma funcionalidade é feita ou consumida e nunca removermos funcionalidades.
  Nós também podemos adicionar novos campos em cada recurso.
  Esse campo precisa ser opcional, porque alguns podem não passar esse campo,
  já que o  contrato original não fornecia esse campo.

  Novos campos podem ser adicionados, só que de forma opcional.
  Até porque um campo a mais, não é grande problema. Se você manda um campo a mais para o seu cliente, não é um grande problema. Mas se você passa a esperar algo que não chega do cliente, aí nós temos um problema.

  Nós temos que poder fazer o deploy dele individualmente sem problema. Ele realmente precisa ser independente. Só que, tornando-o independente, nós precisamos ainda assim manter os nossos contratos.

  microsserviços devem ser independentes, mas devem respeitar os contratos.

  a abordagem monolith first. O ideal é que, se você está criando uma nova aplicação, você comece pela abordagem monolítica. Você cria uma única aplicação para servir tudo que você tem que servir. Conforme a complexidade vai aumentando e você realmente precisa de um microsserviço, você vai identificar os módulos de cada parte desta aplicação.

  Então, por isso a ideia é que você comece com a abordagem monolítica, para que você conheça o seu domínio, para que você implemente os problemas e para que você resolva os problemas reais e corrigia os bugs.

  E a partir dos problemas solucionados, os problemas técnicos nós resolvemos com microsserviços, porque qualquer problema de negócio é resolvido tanto com uma abordagem monolítica como uma arquitetura de microsserviços.

  Identificar barreiras entre serviços é uma tarefa árdua e infelizmente não há uma regra definitiva de como fazer isso. Porém há estudos que nos dão um bom norte sobre isso.
  Existe um conceito de full cycle developer que é justamente isso, qualquer pessoa está apta a trabalhar com todas as partes de uma aplicação
  Nós precisamos definir esse padrão para garantirmos que determinadas coisas vão ser feitas, que ninguém vai esquecer e que vão ser feitas como deveriam.
  Para isso, a padronização vai ajudar porque alguém vai pensar muito nisso uma vez e depois todos os microsserviços vão seguir essa abordagem.
