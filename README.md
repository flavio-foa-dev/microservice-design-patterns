# Microservice Design-Patterns

- Como funciona a web
- conceito de aplicação monolítica
- microsserviços
- vantagens e desvantagens
- abordagens implementar e nao implementar
- tipos de microsserviços

- serviços de domínio
- DDD pode nos ajudar com essa abordagem
- serviços de negócio
- Strangler pattern
- Sidecar pattern

- ponto único de entrada na aplicação com API Gateway
- agregar processos distintos em uma operação
- ideia de Gateway por cliente
- Edge Pattern

- ideal é que cada serviço tenha seu banco
- CQRS e como podem nos ajudar
- eventos de forma assíncrona
- a importância dos logs
- stack trace de chamadas de microsserviços
- métricas são necessárias

- separar sua aplicação em microsserviços
- padrões de integração de microsserviços
- lidar com dados usando microsserviços
- realizar a operação e monitoramento de microsserviços
- componentes de um microsserviço;
- importância de uma API (interface pública) de um microsserviço;
- separações entre serviços diferentes.

Tipos de microservicos
- Data service
  data services. Um data service ou serviço de dado é um tipo de um serviço que simplesmente vai expor dados, como se fosse uma fina camada antes do seu banco de dados. Então o que ele vai fazer é receber dados e realizar o processamento necessário para manter aqueles dados consistentes.

- Business service
  usiness service, ou serviço de negócio, é um tipo de serviço que além de consumir dados de alguma forma, seja consumindo um data service ou tendo acesso direto ao banco de dados, ele fornece operações mais complexas.

- Translation service
  ranslation services, que são basicamente uma forma de você acessar algum recurso externo, mas mantendo certo controle. Então imagine que, por exemplo, eu queira consumir um serviço de log externo.

- Edge service
  edge services. Um edge service, como o nome já diz, serviço de ponta, é algo que é entregue diretamente para o cliente e pode ter necessidades específicas.

- diversas formas de prover hosts de aplicações;
- etapas de criação de um novo serviço;
- necessidade de um padrão entre serviços.
- necessidade de comunicação entre serviços;
- técnicas de comunicação síncrona e assíncrona;
- falhas de comunicação
- Possiveis soluções para elas;
- conceito de Service Discovery e DNS.
- detalhes de segurança além dos microsserviços;
- autenticação
-  autorização;
- técnicas de segurança em rede, como listas de IP, redes virtuais e firewall;
- Defense in Depth.
- automatizar pipelines;
- importância de criar diferentes ambientes de deploy;
- estratégias de deploy como blue-green e feature toggles.

