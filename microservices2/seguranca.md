Seguranca

segurança no geral.
  Nós temos duas principais formas de segurança quando estamos trabalhando com redes. safety at transport e safety at rest. Traduzindo é segurança no transporte e segurança em repouso,

  Quando falamos de segurança em transporte, na web, a primeira coisa que vem à mente é HTTPS, é a criptografia dos dados que sai de um cliente e vai até um servidor. Então sai do seu navegador e vai até o seu API Gateway. Sai do seu API Gateway chega até um microsserviço. Sai de um microsserviço, bate no seu service registry e vai para outro.
  Tudo isso precisa estar criptografado. Todas essas mensagens e esses caminhos precisam estar blindados. HTTPS  certificados

  E nós temos a safety at rest (segurança em repouso/segurança no destino), que é basicamente termos criptografia, seja do nosso disco, sistema de arquivos - todos os arquivos que o usuário nos manda precisam estar criptografados e bem seguros.

  Os nossos bancos de dados, principalmente, precisamos criptografar. Você me diz: “eu preciso criptografar o meu banco de dados de catálogo? Só tem informação pública lá”. Ok, lá você não tem informação sensível, mas no microsserviço de pedidos onde você tem detalhes de pagamento e informações sobre o cliente, isso precisa ser criptografado. Não só criptografado, mas também anonimizado.
  Se por algum motivo alguém conseguir quebrar nossa criptografia, nós precisamos fazer o máximo para que esses dados não façam sentido para a pessoa que roubou as nossas informações.



segurança de microsserviços,

Mas quando trabalhamos com microsserviços nós precisamos ter um cuidado especial com isso, porque são vários microsserviços e nós temos vários pontos de ataque onde podem acontecer falhas de segurança. Então nós precisamos ter certeza de que sabemos com quem estamos lidando.

autenticação e a autorização lidam, com que nós saibamos com quem estamos lidando.

nunca devemos confiar em um usuário - e quando eu digo usuário, não é só uma pessoa que está se conectando, é qualquer cliente que faça alguma requisição para o nosso servidor. Nós não podemos confiar.
Pode ser um cliente malicioso, ou seja, um ataque acontecendo. Pode ser um cliente descuidado, uma pessoa que não tem más intenções, mas que pode ser prejudicial para o nosso sistema.
Várias falhas de segurança acontecem por causa de usuários não mal-intencionados, mas talvez mal informados

A autenticação permite que nós saibamos quem está fazendo uma chamada.
A autorização diz se essa pessoa, que já está autenticada, pode ou não fazer essa ação, pode realizar a ação que ela está querendo.

 é muito importante lidarmos com a parte de rede. É crucial entender essa parte de infraestrutura para que possamos gerenciar bem a segurança dos nossos microsserviços.

 a parte de programação é uma pequena parte da arquitetura de microsserviços. Muito é product design, como  vai arquitetar cada um dos microsserviços, que a decisão pode ser, tecnológica ou de negócio.


Vamos lá! Imagine que eu tenha três microsserviços e eles precisem se comunicar. Eles não precisam receber requisições externas. Nenhum serviço externo precisa falar com eles. Então, o que podemos fazer?

 Nós colocamos eles dentro de uma rede virtual  VPN, permitindo somente conexões da mesma rede. Dessa forma, qualquer coisa que estiver fora dessa rede sera barrada.  Nunca é possível acabar, mas evitamos muito  a possibilidade de ataques a esses microsserviços.


 Só que se algum outro cliente precisar se comunicar,

 uasamos ferramentas de firewall.
 Ferramentas profissionais de firewall podem fazer muitas coisas. Nós podemos limitar acessos no geral, mas também podemos prevenir diretamente aqui no API Gateway, SQL injections, ou injeções de SQL, diretamente no firewall sem nem passar pelas proteções que a nossa aplicação também deve ter.

 Nós podemos prevenir ataques de negação de serviço, DoS, DDoS aumentamos a segurança de rede para o nosso sistema.

conceito defense in depth
é um nome difícil para um conceito relativamente simples.

Ou seja, todo sistema está propenso a ataques. Quando falamos de segurança, nós não estamos evitando ou impedindo ataques, nós estamos dificultando ataques e nós estamos tornando eles menos prováveis, mas eles ainda podem acontecer. Então nós precisamos nos defender de várias formas. Nós precisamos utilizar vários pontos de defesa para termos uma segurança maior.

Quem trabalha com back-up tem aquela máxima: quem tem dois, tem um. Quem tem um, não tem nenhum. Então mecanismos de segurança é a mesma coisa. Se você tem um só, você não tem nada. Você precisa de redundância de mecanismos de segurança.

Por exemplo: você precisa deixar os seus microsserviços em uma rede virtual, liberar acesso apenas ao API Gateway do IP dele acessar, ter um firewall no seu API Gateway e ter autenticação e autorização na sua aplicação ter HTTPS para a segurança de transporte. Tudo isso junto vai tornar o seu sistema realmente um pouco mais seguro.

É sempre uma balança: quando mais seguro eu quiser o meu sistema, menos amigável e prático ele vai ser. Quanto mais prático eu quiser, menos seguro ele vai ser. Então nós sempre colocamos em uma balança e tentamos achar um ponto

O conceito de ter vários mecanismos de segurança às vezes até redundantes
é o que chamamos de defense in depth,
 que é defesa de profundidade.
 Você tem primeiro o seu firewall. Se alguém conseguiu passar dele, ele tem restrição que só vai chegar o microsserviço se for pelo IP do API Gateway, Se ele conseguir simular esse IP de alguma forma, ele só vai conseguir acessar a nossa aplicação se estiver autenticado. Se ele conseguir se autenticar, ele tem que utilizar um usuário que está autorizado para executar aquela ação.
  Então nós temos várias etapas que precisam ser quebradas nessa defesa em profundidade,
  em defense in depth.

