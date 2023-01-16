Integrando Servecos

- integração entre diversos microsserviços,
  a integração vai além dessa comunicação entre serviços.
  A comunicação entre serviços é uma parte importante, mas integração vai além disso.

  Por exemplo, como eu posso garantir um ponto único de entrada? Porque imagina Escola  está em uma arquitetura de microsserviços, então o desenvolvedor mobile vai pegar para desenvolver e na hora de consultar os dados do aluno ele precisa consultar uma URL.
  Na hora de consultar os dados de curso é outro domínio, outra URL, com outro padrão, outro formato.
  Então em um ele usa JSON, em outro XML, e na parte de jogos, de gamificação é um formato binário. Então como unificamos isso e mantemos uma API consistente para o cliente conseguir acessar?

  por exemplo, através de api.escola.com.br/ ? /aluno /jogador /matrícula financeira . então a partir disso eu quero que esse ponto único de entrada me mande para os serviços corretos e realize o que tem que fazer.
  O nome disso, é API Gateway. Então é gateway, um portão, em tradução livre, então é um portão para a API, um ponto de entrada.

  pensando no problema, imagina que clientes acessem livremente cada um dos serviços, isso gera caos para o nosso back-end e para o cliente também.
  cliente pode muito facilmente acessar os serviços fora de ordem, acessar serviços que não deveria
  o cliente vai ter muito mais dificuldade de saber onde consultar para pegar determinados dados, para realizar determinados processos.

   Então um gateway, portão de entrada, ele fornece um proxy ou uma fachada, ponto de entrada, para que você acesse  de forma simplificada para as necessidades reais.

   padrão de projeto, Facade,
    que fornece exatamente isso, um ponto de entrada para um subsistema,
    para algo mais complexo,
    então ele simplifica a API.
    E um API Gateway é como se fosse uma facade, mas nesse nível mais alto, um nível mais arquitetural que de design mesmo.

    Mas existe uma desvantagem, esse portão pode acabar se tornando um ponto central de falha. Se o meu API Gateway cair, a minha aplicação toda cai.

    Então precisa ser muito bem escalado,
    podemos ter algo como demanda elástica,
     por exemplo, que conforme as requisições chegam,
      isso cresce automaticamente.
      isso na parte de infraestrutura, que precisamos conhecer nosso ambiente.
sempre vamos falar de trade-offs.
Ganhamos em um ponto, mas acabamos perdendo em outro. Então vamos colocar na balança e ver o que pesa mais.





