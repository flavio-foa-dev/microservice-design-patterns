Em uma arquitetura de microsserviços, o que nós temos é cada uma dessas partes, cada pedaço desse nosso sistema de exemplo loja vai ser uma aplicação diferente e essa aplicação diferente, essa pequena aplicação é o que chamamos de um serviço. E a ideia de microsserviços é ter vários microsserviços.

 Ou seja, vários desses serviços muito pequenos, que tenham uma responsabilidade muito bem definida, que saibamos exatamente o que cada um dos serviços vai fazer.

 exemplo da loja, ela vai ter um serviço de catálogo, que vai lidar com produtos, vai ter toda a lógica de cadastro, de exibição de produtos, como um produto é organizado, tudo isso vai ter o próprio banco de dados. Um banco de dados de catálogo que lida com produtos, categorias, taxonomia de produtos.

 Então toda a lógica de produtos está nessa aplicação separada. Já a parte de realizar um pedido, por exemplo, vamos ter um serviço específico de pedido. E os pedidos estarão armazenados em um banco de dados diferente do de produtos. Então os produtos estão nesse banco de dados e os pedidos estão em outro.

Se por algum motivo o sistema de pedidos sair do ar, eu ainda consigo ver o meu catálogo de produtos, navegar nas páginas e ver o que eu quero comprar. Eu não vou conseguir efetivar a compra, mas eu consigo ir navegando.


"Microsserviços são uma abordagem arquitetônica e organizacional do desenvolvimento de software na qual o software consiste em pequenos serviços independentes que se comunicam usando APIs bem definidas. Esses serviços pertencem a pequenas equipes autossuficientes". author:

uma duvida ne , como eu vou fazer um pedido e armazenar no banco de dados, se eu não sei os detalhes do produto que estão sendo comprados?” Então esse que é o ponto.
Os microsserviços, para gerarem uma aplicação completa, eles precisam se comunicar. Então o meu microsserviço pedido vai conhecer o de catálogo, o de produto.
Ele vai conhecer o banco de dados, ele vai saber como funciona a lógica, toda a taxonomia de produtos? Não. Mas ele vai conhecer o endpoint, por exemplo, vai saber como acessar os detalhes de um produto ou alguma coisa assim, pegar pelo menos uma identificação de um produto para conseguir armazenar e quando eu quiser buscar os dados desse pedido, eu pego ele e tenho os detalhes do produto para depois conseguir consultar no catálogo.
A comunicação entre microsserviços é algo muito importante
microsseviços trazem tanta flexibilidade para o nosso projeto.
 Microsserviços não devem ser utilizados no desenvolvimento de qualquer aplicação


Algumas vantagens:

Projetos independentes = tecnologias independentes
Falha em 1 serviço é isolada
Deploys menores e mais rápidos


Algumas desvantagens:

Maior complexidade de desenvolvimento e infra
Debug mais complexo
Comunicação entre os serviços deve ser bem pensada
Diversas tecnologias pode ser um problema
Monitoramento é crucial e mais complexo

Primeiro, temos muito maior complexidade, tanto de desenvolvimento, quanto de infraestrutura. Vou precisar de diversos servidores, de aplicação de banco de dados, servidores web mais robustos para balancear melhor a carga, saber como realizar esse balanceamento.
O debug de um código, de uma arquitetura em microsserviços é muito mais complexo. Porque em uma aplicação monolítica nós temos o que é conhecido como a stack trace.

Já em microsserviços eu posso ter: O cliente chamou a URL, um endpoint, isso cai em um ponto que chama um serviço, esse serviço chama outro, que chama outro e no 4º serviço dessa cadeia teve um erro. Para eu rastrear todas essas chamadas e entender o que causou o erro é bem mais complexo.


Nos estágios iniciais do desenvolvimento de um software, o domínio ainda não é completamente conhecido. Erros serão cometidos e deverão ser fáceis de corrigir. Quando já conhecemos bem o domínio, fica muito mais fácil dividir uma aplicação em vários serviços.

existe uma referência interessante,
link: https://martinfowler.com/bliki/MonolithFirst.html,
do Martin Fowler,

E ele traz essa ideia, esse padrão de monolito por padrão. Então a ideia é que, segundo ele, caso você vá direto desenvolvendo microsserviços, é muito arriscado. Vamos nos deparar com complexidade que não precisávamos naquele momento

Já para a abordagem monolítica primeiro, desenvolvemos o sistema. O sistema está todo acoplado, ele vai ser um pouco mais difícil de escalar, mas conseguimos entender o domínio, implementamos as regras de negócio em algum lugar.

E a partir disso entendemos se uma parte da aplicação está ficando muito complexa ou está recebendo muitas requisições. Então pegamos essa parte da aplicação e separamos e assim vamos quebrando em partes até ter uma arquitetura de microsserviços.






