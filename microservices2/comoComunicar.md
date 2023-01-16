Como Comunicar

como podemos fazer para que cada microsserviço saiba se comunicar com outro,
como que aplicações externas se comunicam com os nossos serviços etc.

 criando microsserviços, como podemos fazer para que cada microsserviço saiba se comunicar com outro, como que aplicações externas se comunicam com os nossos serviços etc.


 Primeiro, uma visão geral. Como vamos lidar com essa comunicação? Todo serviço pode se comunicar diretamente com qualquer outro serviço indiscriminadamente? O front-end vai chamar diretamente cada um dos nossos microsserviços? Ele pode fazer isso? Ele deve fazer isso? Como fazer para evitarmos isso?

 O ponto é: quando nós trabalhamos com microsserviços, o simples fato de  ter uma arquitetura baseada em microsserviços não dita nenhuma regra neste cenário.
 Então, não existe uma regra dizendo: “tais microsserviços não podem se comunicar, já outros podem. O front-end não pode se comunicar direto com o back-end de cada um dos microsserviços ou ele deve se comunicar”.

 Se todo microsserviço se comunica diretamente, indiscriminadamente, nós temos dependências descontroladas, nós temos dificuldade de atualização e acabamos dificultando o microsserviços independentes.

 Porque, se nós não sabemos quem está chamando o nosso microsserviço ou qual microsserviço chama qual, nós acabamos ficando preocupados do que pode ser, do que pode estar chamando o nosso microsserviço e o que pode chegar. São dependências descontroladas no sentido de não sabermos quais tipos de requisições vão chegar, então podemos acabar quebrando coisas se não nos preocuparmos ainda mais com contratos.
 Nós precisamos ter esse controle, até por motivos de segurança

o front-end não fala diretamente com cada um dos microsserviços.
Aqui no nosso cliente móvel, por exemplo, nosso aplicativo fala com nosso API Gateway.
Só que, na verdade, nós temos aqui o que são os edge services ou back-end for front-end, esse BFF.

Nós conhecemos isso como edge services nos padrões de microsserviços, que são basicamente API Gateways específicos para cada cliente. Repare que aqui nós temos um para clientes móveis e outros para clientes web. Talvez eles precisem de informações diferentes, agregadas ou serializadas de formas diferentes, enfim.

 aqui, como estamos utilizando esses API Gateways, nós temos pontos únicos de entrada na aplicação, que permitem o monitoramento de todas as entradas que chegam na nossa aplicação.

comunicação síncrona.
Quando nós estudamos desenvolvimento desde o início, nós começamos a aprender esse tipo de comunicação.

Imagine que o nosso microsserviço de catálogo precisa adicionar algo no carrinho de compras. Ele pode utilizar a comunicação síncrona. Como assim? Ele vai fazer uma requisição para o serviço de carrinho, e o serviço de carrinho vai processar e validar se esse produto realmente existe e se ele está na loja, vai inserir no mecanismo de persistência do carrinho, seja ele qual for, e vai devolver uma resposta informando: “olhe só, está salvo. Esse produto está adicionado ao carrinho”.

E aí, esse microsserviço de catálogo que estava exibindo o produto devolve para a aplicação informando - “olhe só, pedido do catálogo adicionado ao carrinho com sucesso”. Então temos aqui uma comunicação síncrona, linear.

 Só que esse tipo de comunicação tem um problema. problemas de performance, se você vai chamar diretamente outro serviço, qualquer e ha um problema nesse serviço me afeta diretamente. Se esse serviço estiver lento, minha resposta também vai ser lenta. Se esse serviço der erro, eu também vou dar erro, porque eu recebi uma resposta de erro; é o que eu vou passar para quem me chamou.

comunicação assincrona.

Vamos pensar aqui no cenário geral -
 existem casos onde faz sentido eu não precisar obter essa resposta imediatamente.
 Imagine que, quando eu fizesse uma compra, eu clicasse no botão “Comprar” e a página só terminasse de carregar quando o produto chegasse.
 Isso não faz o menor sentido!
 Alguns processos vão acontecendo, cada um no seu tempo, e eu vou sendo notificado depois.
 Então essa é a ideia por trás da comunicação assíncrona. Eu realizo um pedido e não espero a resposta.
 Quando tudo der certo eu recebo  um e-mail e avisa se deu tudo certo ou se deu problema, que eu venho consertar”. ok

para isso. Uma das técnicas é o CQRS,
que é command query responsibility segregation, que é a segregação de responsabilidade de comandos de ordens e de busca.
Quando eu vou cadastrar um pedido, eu faço um comando - “olhe só, estou fazendo um pedido,
me devolva”. A API que recebeu essa requisição devolve - “OK, eu aceito o seu pedido” - mas ela não diz que o pedido já foi criado,
que o pedido já foi processado ou que o pagamento foi feito. Nada! Ela só informa – “eu aceito o seu pedido e vou trabalhar com ele aqui em plano de fundo”.

Uma outra possibilidade, além de background tasks, é utilizar eventos através de mensagerias ou plataformas de stream como o Kafka, por exemplo
pedido, eu vou e digo: “quero fazer um pedido”. Você me informa: “OK, eu aceito o seu pedido” e manda este evento: “um pedido foi feito, para algum serviço de mensagens, um Rabbit MQ, um Pub/Sub do Google/um Kafka”. Você envia isso para algum serviço de mensagens.

Esse serviço de mensagens vai notificar quem quiser ouvir que um pedido foi feito. E aí, você pode ter, inclusive, microsserviços separados para verificar se isso foi fraude, para verificar se esse produto existe em estoque w para efetivamente processar o pagamento. Várias coisas podem acontecer de forma assíncrona, ou seja, não serial.
Uma não precisa esperar a outra para acontecer.

Então aqui nós temos um caso real de comunicação assíncrona. Eu fiz o pedido, logo a página já carregou informando — “seu pedido está sendo processado” — e isso tudo vai sendo feito depois.


E quando algum desses dois falha? Tanto a comunicação síncrona quanto a assíncrona? Como eu vou lidar com falhas?

Lidando com Falhas
Como diz a lei de Murphy - se existe a mais remota possibilidade de algo dar errado, vai dar.
tem operações muito intensas de redes, existe muita comunicação de rede entre um servidor e outro. Então as chances de dar algum problema são muito grandes, porque comunicação em rede é muito falha. É muito mais fácil uma rede cair ou uma rede ficar indisponível, do que o serve pifar ou alguma coisa do tipo.

Chamadas de rede são propensas à falha, então precisamos lidar de forma muito robusta com falhas quando estamos trabalhando com microsserviços. Cada abordagem pode causar falhas diferentes e cada uma dessas falhas pode ter soluções diferentes.

microsserviço de carrinho não está funcionando  na minha loja, se eu não consigo adicionar no carrinho, eu não consigo comprar, vai dar erro. Eu não consigo pular essa etapa nem nada do tipo.
O que eu posso fazer para tentar prevenir outras falhas e problema de performance? Ao invés de chamar diretamente o meu microsserviço de carrinho, eu posso adicionar um proxy na frente.
Basicamente, você vai colocar um serviço na frente - pode ser o próprio Nginx ou serviços mais específicos - e ele vai ficar passando essa requisição para o microsserviço.

Se quando ele passar essa requisição, na hora que ele pegar de volta para te devolver, ele perceber que foi um erro, o que ele vai fazer? Quando ele receber uma requisição de novo, ele não vai mandar mais para aquele microsserviço porque esse erro pode demorar para ser retornado, então nós teremos problemas de performance.

Se estiver dando erro e nós continuarmos fazendo chamadas, podemos gerar outros erros e sobrecarregarmos o servidor. Então esse proxy não vai deixar a requisição passar e vai te devolver logo, igual a um curto-circuito, ou
circuit breaker.
Então, para evitar uma sobrecarga da rede quando tem alguma volatilidade muito alta,  Então nós temos um curto-circuito.

Esse conceito é trazido para a comunicação de redes, então você tem isso: um proxy que fica na frente e serve de curto-circuito. Deu erro, ele abre esse curto-circuito. O que acontece? Ele não deixa as requisições passarem mais.
Depois de um tempo que pode ser configurável. Ele tenta fazer a requisição de novo, ele tenta passar. Se continuar dando erro, ele abre esse curto-circuito de novo, espera um tempo maior.

E com isso, enquanto as respostas estão sendo retornadas com erro rápido pelo circuit breaker, sem chegar no servidor que está com problema, nós podemos agir ativamente indo lá, reiniciando o servidor, vendo o que aconteceu de errado etc. Dessa forma, nós conseguimos lidar com falhas.

“mas e em caso de comunicação assíncrona,
  Onde a comunicação não está acontecendo diretamente?” Então não posso fazer cache porque é uma comunicação assíncrona, é um processo que eu sei que é demorado, pode ser sensível. O circuit breaker não faz sentido, porque está rolando no plano de fundo, não é alguém toda hora mandando mensagem.

  Então nós podemos utilizar algumas abordagens.
    retry - pode resolver o problema.
      Às vezes você tentou entregar uma mensagem e o consumidor não estava pronto para receber, ele estava em um momento de dar um timing muito rápido, ficou um segundo fora e você entregou na hora. Então você tenta de novo e às vezes isso já resolve.
    parecido com um circuit breaker,
    um retry com back-off,
     ou seja, você dá uma afastada, espera um pouco e depois tenta de novo - que é basicamente o que o circuit breaker faz.
    Tentou de novo, não deu certo e esperou um tempo maior. Até que depois de um tempo, de determinadas tentativas,
      manda essa mensagem para mensagem de filas mortas ou ignoradas, não processadas.
     Aqui, fica um registro de mensagens que falharam ao ser entregues e com isso , os humanos,  ir lá e verificar o que aconteceu de erro para corrigir esse problema, porque isso indica um bug.
  isso tudo pode ser tratado automaticamente por serviços já existentes. Serviços de mensageria, via de regra, já possuem esses mecanismos sem precisarmos escrever código nenhum.
  Eles já estão com esses mecanismos prontos, codificados, super testados e prontos para  utilizar. um Kafka, um Rabbit MQ, Zero MQ

E quando trabalhamos com comunicação assíncrona, nós precisamos estar prontos para receber mensagens fora de ordem.
  Lembra naquele cenário em que o pagamento só pode ser processado depois que validar os dados?
  Talvez a mensagem de processar o pagamento chegue antes. Então, eu preciso sempre verificar se eu estou pronto para responder essa mensagem.
  Se não, eu posso negar a mensagem, simplesmente não processar ela na hora.
  Aí vai entrar o mecanismo de retry com back-off. Eu posso informar – “tente mandar essa mensagem de novo depois de um tempo”. Isso tudo é possível.

  E as mensagens podem ser recebidas de forma duplicada. Pode acontecer por erro, por eu ter mandado a mesma mensagem duas vezes, a mensageria duplicar essa mensagem por algum motivo. Isso é muito incomum, mas pode acontecer. Ou uma mensagem ter sido processada até um ponto e algo deu erro, então você devolve a mensagem para processar o restante depois.

  Então nós precisamos atingir um conceito chamado de idempotência.
   Isso é um conceito da programação funcional, que diz que se você chamar duas vezes a mesma função, o mesmo pedaço de código, se você executar a mesma coisa várias vezes - o resultado tem que ser sempre o mesmo.





















