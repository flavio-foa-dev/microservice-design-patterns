Lidando com dados

microsserviços.
 Como pensar na hora de arquitetar esse tipo de projeto?
 lidar com os dados de microsserviços.

 por exemplo, eu vou ter um banco de dados só ou um banco de dados para cada serviço?
 Algum serviço vai compartilhar banco de dados?
 Então como fazemos isso?

 single service
 database ou single
 database ou single service, a ideia é que um serviço tenha um banco de dados, e um banco de dados é para apenas um serviço.

 imaginamos um cenário que no microsserviço no processo de matrícula de aluno nós recebemos 15 requisições por dia.
 Já no microsserviço da parte acadêmica de exibir um materia, nós recebemos 1000 requisições no dia.

 A ideia é que esse microsserviço de matrícula de alunos vai acessar um banco de dados e como ele recebe menos requisições, eu posso ter esse banco de dados em um servidor menos robusto.
 Já na parte acadêmica, que vai enviar as materias, até processar as materias, eu preciso além de ter uma máquina do microsserviço em si mais robusta, mais potente, o banco de dados que ele acessa precisa ser maior, precisa ser uma máquina mais robusta também para não termos gargalo.

 A escalabilidade de um serviço está diretamente relacionada com o banco de dados que ele acessa.
 Por isso um serviço precisa se conectar a somente um banco de dados e esse banco de dados precisa ser acessado somente por um microsserviço.
 Temos a ideia por trás de single service, single database



shared service database.
  cenários onde temos o shared service database.
    Às vezes até por motivos contratuais, determinados dados precisam estar centralizados.
    Por exemplo, o e-mail do aluno e o detalhe de quanto ele paga por ano precisam estar no mesmo banco de dados por algum contrato que a Ampresa tem com um serviço de pagamento, situação hipotética aqui.

    Nesse cenário vamos acabar tendo que utilizar o mesmo banco de dados no módulo de aluno e no módulo de financeiro. Isso é um problema porque esse nosso banco vai precisar escalar conforme a necessidade do maior microsserviço, do microsserviço que precise de mais recursos e acabamos desperdiçando um pouco de recurso. Então isso pode ser um problema.

    Só que para garantirmos que nossos microsserviços sejam independentes vamos tratar esse banco em cada serviço como se fossem bancos diferentes.Emboram nao sejam sacou?.
    A conexão vai ser independente, a forma como o acessamos é independente, nós vamos ignorar o fato de que fisicamente é o mesmo banco, vamos fingir que são bancos separados.


CQRS
padrão que é mais para o lado de codificação
padrão de código pode nos ajudar na parte de microsserviços.
  microsserviço padrão conhecido como CQRS,
   que significa
    command query responsibility segragation,
  que é segregação da responsabilidade entre um comando e uma busca. LEITURA E ESCRITA

 Então a ideia por trás do CQRS
   é ter um modelo de escrita e um modelo de leitura.
     E com os 2 separados podemos ter cada um realizando operações mais complexas.

     Por exemplo, na hora de cadastrar um aluno, eu posso ter informações sendo inseridas.
     buscar as informações de um aluno, eu posso ver as informacaoes sendo escritas.

      Então se eu tenho 2 dados separados, 2 processos separados,
      eu consigo agregar domínios, consigo inserir informações de forma um pouco mais tranquila.
      CQRS pode nos ajudar nisso, só que isso aumenta muito a complexidade de um sistema.


eventos assíncronos.
Então existem cenários onde algum problema não pode, sob hipótese nenhuma ser resolvido na hora, ser resolvido em tempo real. Existem alguns cenários para isso, por exemplo, compra existe um processo de validação antifraude para garantir que o seu cartão é válido, que seu cartão é seu e isso pode ser um processo muito demorado.

Então o que acontece? Inserimos os nossos dados, clicamos em comprar e recebemos uma resposta: “Seu pagamento está sendo processado”, “Sua compra esta sendo aprovada”

Então nesses cenários da compra tecnologias como filas de mensagerias, como RabbitMQ e ZeroMQ e serviços de stream de dados, como o Kafka, eles brilham, eles são ferramentas exatamente para isso, para esses cenários, para a distribuição de mensagens assíncronas, de eventos, de dados assíncronos.




