Lidando com deploy
entregas automatizadas

quando trabalhamos com microsserviços, é simplesmente impossível fazermos isso de forma manual. Por quê, são várias entregas que temos que fazer. Nós temos que gerar o produto várias vezes. São vários microsserviços que precisamos fazer nesse processo e cada microsserviço tem vários componentes.

Quando  trabalhamos com microsserviços nós tendemos a fazer mais entregas, nós tendemos a fazer atualizações mais constantes.  o trabalho manual é inviável.

é interessante e praticamente obrigatório que se tenha uma
pipeline de release,
ou seja, um processo, uma linha de produção até chegarmos a uma entrega, produção, um deploy.

que um processo manual de deploy em uma aplicação monolítica pode ser aceito,
porém em uma arquitetura de microsserviços não.

ambientes de execução que vamos ter durante o processo de entrega e depois deploy.
desenvolvimento, que pode ser a máquina da pessoa que está fazendo o código para que eu consiga criar novas funcionalidades, fazer debug para encontrar problemas etc. Então, o ambiente de desenvolvimento é um ambiente importantíssimo

sabemos que precisamos automatizar o processo e que esse processo automatizado tem que ser parametrizado para que ele possa ser automatizado, para que o meu ambiente de desenvolvimento de forma automatizada suba um container se conectando ao Rabbit MQ e um ambiente de produção que se conecte ao Google


estratégia de deploy. A entrega foi feita,
tudo foi testado e está tudo correto.
Vamos colocar realmente em produção!

estratégias de deploy.

não podemos tirar o sistema do ar e colocar outra versão, se não nós temos um downtime, o nosso projeto vai ficar inacessível. e ele está fora do ar. Você tem que atualizar para aparecer de novo. Isso é meio chato às vezes. Acontece, mas o máximo que pudermos evitar é o ideal.

Então nós temos o conceito de rolling upgrade, que é justamente a ideia de ter uma atualização sem nenhum downtime, sem nenhum instante em que a aplicação esteja inacessível.

Existe o conceito de blue-green deployment. O que significa? Você tem o tráfego mandando para um local, para um cluster com vários servidores que recebem essa API e tem um load balancer recebendo para cá.

Você pode passar a transferir, você sobe um outro cluster, um outro conjunto de servidores com a nova versão e você redireciona o tráfego para esse novo cluster, mas o antigo continua lá, válido, só que ele não está acessível.

Você vai monitorando esse novo cluster, garantindo que esteja tudo certo. Se não tem nenhum problema e você está monitorando, tudo estará certo. Você pode jogar essa versão antiga fora,

Uma outra opção de fazer deploys não especificamente de uma aplicação como um todo, é você ter
feature toggles.
Imagine que você implementou uma nova funcionalidade em seus microsserviços, ou até em uma aplicação monolítica.
Você pode permitir que somente determinados clientes acessem essa funcionalidade. Com esse pequeno número de clientes você vai testando e verificando se está tudo dando certo e você vai aumentando o número de clientes que vão acessar.

Você vai monitorando o uso e depois você libera o uso dessa feature para todos os clientes. Essa é a ideia de uma feature toggle. Você ativa ou desativa o acesso dessa feature para cada um dos clientes.