- strangler pattern
    que é um padrão de estrangulamento.
  pegamos o monolito, o estrangulamos até extrair pequenas partes.
  a ideia desse strangler pattern é ir quebrando ele, tirando pequenas funcionalidades.

  Podemos começar esse processo isolando os dados de um monolito ou podemos começar esse processo isolando o domínio de um monolito. imagina ama escola como um grande monolito e começar ama migração de um monolito para microsserviços.

  vamos separando domínio por domínio, processo por processo, vamos extraindo o monolito até que ele deixe de ser um monolito, até que ele mesmo só tenha alguns pequenos serviços e ele seja talvez um serviço um pouco maior ou até vire realmente um outro microsserviço muito específico.

- sidecar pattern
   por exemplo, realizar log. Isso é comum a todos os serviços, só que isso também vai crescer conforme o serviço cresce, então vamos precisar ter essa escalabilidade junto com o serviço. Se tivéssemos um serviço separado teríamos outros problemas.

   Então identificamos um processo comum e sabemos que o ideal é tê-lo junto com os serviços? Vamos construir um módulo compartilhável. Então por exemplo, se estamos trabalhando com um Node, vamos criar um pacote no NPM,
   vamos criar um pacote que pode ser compartilhado entre vários serviços de forma independente, só que o código em si, está em um lugar só, de forma que se eu atualizar esse código, essa atualização vai ser replicada em todos os serviços.
   Então a partir disso, aplicamos esse sidecar