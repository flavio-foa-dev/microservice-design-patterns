http => request => response => html/css/javascript

 padrões de projeto para arquitetar microsserviços, ou seja, como nós vamos separar nossos microsserviços, etc.

  precisamos dar um passo atrás e entender como funciona a web. Se não fossem microsserviços, como tudo seria feito? Como as coisas são feitas com ou sem microsserviços.

 web. A internet funciona através de um protocolo conhecido como HTTP. através de algum cliente, por exemplo, seu navegador, um celular ou uma coisa que se conecte à internet, acessamos algum lugar.

 exemplo, eu vou no meu navegador e digito "loja.com.br". Quando pressiono “Enter”, o meu navegador, que é conhecido como cliente, envia um pedido para um servidor. Então o servidor da LOJA vai processar esse pedido, que também chamamos de "requisição".

 Então ele vai processar essa requisição e vai fazer o que ele tem que fazer. Vai ver se esse cliente está logado ou não, vai carregar os produtos, ver se tem alguma promoção, mostrar as novidades, etc.

 E baseado em toda essa lógica ele vai montar uma resposta, que normalmente, se estamos falando de web, isso pode estar em HTML, por exemplo. Então o servidor monta essa resposta em HTML e devolve. O cliente recebe essa resposta e o navegador, como ele sabe interpretar HTML, ele vai exibir essa resposta no formato de uma página da web. Então simplificando bastante o conceito, é assim que funciona a web.

E como nós construímos aplicações para a web, como programamos para a web? É muito comum que tenhamos diversos clientes, por exemplo, temos vários navegadores, podemos ter um sistema que também receba requisições de dispositivos móveis, etc. e essa requisição chega para nós em algum lugar.

 Muitas vezes chega até algo que é conhecido como load balancer. É um servidor web que vai receber essa requisição e carregar, mandar essas requisições para servidores diferentes, vai distribuir a carga, como o próprio nome diz.

 Por exemplo no caso da Loja, uma aplicação só, uma aplicação conhecida como "monolítica", o que ela faria? Ela teria os cadastros de produtos, de setores, teria o conceito de gamificação vendas, para armazenar os pontos da plataforma, teria a parte financeira para processar pagamentos, teria a parte de conteúdos de loja, enfim, tudo isso em uma única grande aplicação.

 Então nesse exemplo nós temos uma loja e nessa aplicação da loja nós temos, por exemplo, um módulo, um pedaço de código, uma classe, o que for, que cuida do catálogo e isso lida com produtos. Nós temos uma outra parte que lida com pedidos, então temos o pedido e tem um serviço, tem um módulo, tem uma classe, um pedaço de código que lida com pagamentos.

Então nós temos vários módulos, várias partes, vários pedaços de código que lidam com dados diferentes e tudo isso é armazenado em um banco de dados. Assim nós criamos aplicações monolíticas, assim programamos via de regra. Normalmente é assim que aprendemos a desenvolver aplicações.

 Só que essa abordagem tem alguns problemas. Para começar, o deploy disso tudo pode ser demorado. Imagina se o Facebook fosse toda uma aplicação só e eu preciso alterar a forma como as notificações são exibidas.
 Eu alterei e agora todo o deploy de construir o mural, de mostrar sugestões de amizades, tudo isso vai ter que ser reconstruído, passar por todo o processo de deploy, de build, de fazer testes, para só então conseguirmos ter a aplicação em produção. Então isso pode causar uma demora muito grande.

 E por causa de post, que é algo um pouco menos importante, vamos dizer assim, eu acabo não conseguindo cria ads um plano da marketing, acabo não conseguindo atrair clientes
 Uma aplicação monolítica tem um único deploy, então um erro em uma parte da aplicação pode quebrar uma outra que não tem nenhuma relação.

 Então nesse cenário monolítico, uma falha pode derrubar um sistema inteiro, inclusive partes do sistema que não têm nada a ver com essa parte onde a falha foi originada. Então isso é um outro grande problema dessa abordagem.
Um outro ponto é que normalmente, via de regra, se temos um sistema monolítico, temos um projeto, então temos uma tecnologia. Óbvio que existem formas de contornar isso, mas via de regra, em uma aplicação monolítica somos presos a uma tecnologia só. E nem sempre a mesma tecnologia vai resolver bem todos os problemas que nós temos.

 Se eu tenho na mesma aplicação em uma parte de consultar em tempo real os dados da bolsa de valores e eu tenho também a geração muito simples de uma HTML, eu vou ter que fazer essas duas tarefas completamente diferentes com a mesma tecnologia?
 Sabemos que acessar dados de mercado em tempo real é muito comum o uso de C++, por exemplo. Já gerar uma simples página da web, podemos ou fazer de forma estática ou usar javascript para buscar os dados dinâmicos, enfim, ou várias outras linguagens dinâmicas mais leves, mais simples.
 Então poderíamos nos dar ao luxo de escolher tecnologias específicas para cada problemas, mas se temos um projeto só, isso se torna muito mais difícil. De novo, claro que existem formas de contornar, mas via de regra somos presos a uma única tecnologia.

 Então a forma como normalmente criamos soluções para a web tem alguns problemas. E exatamente quando esses problemas aparecem é que vamos ver a solução da arquitetura de microsserviços.