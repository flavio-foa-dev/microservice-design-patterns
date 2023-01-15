Agregacao de Logs

operações de microsserviços. logs

E logs de monolitos são agregados por padrão, você gera um log e todos os logs são gerados para algum lugar que o monolito salva.

Já quando falamos de microsserviços, um serviço gera log em um lugar, outro microsserviço gera log para outro lugar, então precisamos cuidar da agregação.

twelve factory application,
uma metodologia de desenvolvimento e essa metodologia diz que os logs devem ser um string de dados.

Então por exemplo, a partir de um processo que é a nossa aplicação, mandamos os logs para saída padrão e a partir disso podemos ter um serviço realmente específico de logs, não nosso,
 um serviço externo, que coleta todos os logs de todos os nossos processos e agrega, faz o parsing desses logs, que é uma parte da tarefa de agregação, os categoriza, gera relatórios bonitos.

 Agregando Metricas.

 E também precisamos conhecer o status da nossa aplicação como um todo, um status mais geral. E para receber, para conseguirmos visualizar esse status, nós precisamos de métricas.

 Então eu posso utilizar métricas para manter meu sistema saudável.
  Assim como exames de sangue estão para a saúde de uma pessoa,
  métricas estão para a saúde de um sistema.
 Precisamos ter métricas para saber se nossos sistemas estão saudáveis ou estão quase morrendo,
 estão quase ficando offline.

 Então precisamos coletar e agregar métricas. Nos permitem saber o que está acontecendo em determinado momento e ter uma visão de alto nível.
  Eu posso saber que determinado microsserviço está recebendo muita requisição e outro quase não está recebendo.
  Então eu posso diminuir recurso de um e aumentar do outro para poupar dinheiro e garantir que os nossos serviços estejam sempre de pé.

   dashboard, ou seja, podemos utilizar, construir o nosso próprio, mas precisamos ter alguma forma de visualizar o status mais detalhado de cada microsserviço. Esse microsserviço está gerando esse tipo de log muito mais do que a média do ano passado, por exemplo.

  Então métricas não podem ser ignoradas, precisamos avaliar métricas.
