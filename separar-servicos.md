Um serviço data service e como podemos decidir quando vamos separar um data service.
E normalmente fazemos isso utilizando o que é conhecido como serviços de domínio.

Então vamos pegar um pequeno domínio da nossa aplicação, não vamos pegar um contexto inteiro, não vamos pegar um módulo inteiro. Vamos pegar um pequeno domínio e separar isso em um serviço.

E muito importante  que para isso um conhecimento ou uma certa consciência do que é domain-driven design. DDD
Através das práticas de domain-driven design, seguimos os padrões dele, temos muito claro o que é um domínio bem definido no nosso sistema para separá-lo em um serviço, em um data service que vai ser um serviço de domínio.

Começamos modelando o domínio ESCOLA, não pensamos na persistência ainda. Por exemplo, no caso da escola, imagina que  queira ter um data service, que vai ser um serviço do domínio de aluno.
 Sempre que um aluno se matricular, ou sempre que um aluno alterar algum dado seu, vamos precisar consumir um domínio que lida especificamente com o aluno. Então esse serviço de domínio aluno vai ter suas regras, por exemplo: um aluno precisa ter um e-mail, um aluno precisa ter determinadas regras para esse serviço ser criado de forma que atenda ao negócio em si.

 Então precisamos, obviamente, conhecer o negócio e esse é um outro ponto onde DDD, domain-driven design pega muito, precisamos conhecer o domínio do que estamos desenvolvendo.

 E a partir do modelo já bem pensado, a partir do domínio modelado, vamos começar avaliar quais ações vão ser disponibilizadas. Então, por exemplo, eu vou matricular um aluno a partir desse domínio? Ou vou simplesmente inserir um aluno a partir desse domínio?
 Então esse tipo de detalhes do contrato, ou seja, de como vamos expor as ações, precisamos pensar e ter muito bem definido. Tendo isso definido, vamos liberar acesso a esse recurso, acesso a esse serviço.

Obviamente o acesso a esses dados possui lógica, possui alguma regra para que esse domínio seja consistente, mas às vezes precisamos de operações que demandam mais de um domínio.
 Então para esse caso nós temos o que é chamado de

 “serviço de negócio”.
 Então no serviço de negócio ou business service, é basicamente a junção de diversos data services ou serviços de domínio.
 se formos pensar na matrícula de um aluno, isso não envolve apenas inserir um aluno no serviço de alunos. Talvez precisemos ter um registro dele no serviço financeiro, talvez esse registro na gamificação precisamos de um registro também sendo inserido.

 às vezes temos detalhes muito mais complexos do que somente lidar com um domínio. Então o serviço de negócios serve para esses casos.

 Precisamos pensar muito bem sobre um processo do domínio do negócio. Existe um processo que vai ser executado. Quando pensamos com a visão de negócio, sem pensar em código, sem pensar em implementação, existe um processo. Por exemplo, de novo, matricular aluno.
 E esse processo vai ser representado através desse serviço específico. Eles vão prover uma funcionalidade de negócio de mais alto nível. Então não é inserir um aluno, inserir uma matrícula financeira, inserir um jogador, ele vai ser um processo de alto nível: matricular. E a partir disso as operações mais granulares vão ser orquestradas.
 E através de um processo de matricular aluno, usando um serviço de domínio, conseguimos encapsular isso sem que o cliente, por exemplo, que a nossa API precise expor que o cliente precise chamar um inserir aluno e depois inserir uma matrícula financeira, inserir jogador, uma gamificação, então conseguimos encapsular isso tudo e simplificar o processo, o tornando mais real, mais próximo do que falamos no domínio.

 Agora receber matrícula, realizar matrícula, isso é um processo que acontece no nosso negócio. E a partir disso vamos identificar quais os domínios necessários. Precisamos do aluno, da matrícula financeira e do jogador. São os domínios que estão em serviços diferentes, que estão em data services diferentes.

 Então com isso determinamos, identificamos os domínios e a partir disso vamos definir a API que vamos utilizar. Focando de novo no domínio e não nos dados em si. Eu não preciso ter detalhes de como o banco de dados está organizado. Não. É um aluno? Então eu não vou passar um UUID desse aluno, um ID desse aluno, eu vou ter uma matrícula ou um CPF, alguma coisa do tipo, focando sempre no domínio.


