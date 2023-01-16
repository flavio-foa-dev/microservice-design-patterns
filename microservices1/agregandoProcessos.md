Agregando Processos

process aggregator pattern.

os serviços de domínio e os serviços de negócio.
 Um serviço de negócio agrega vários serviços de domínio para termos um processo completo.

Agregador de processos é algo que precisamos agregar diversos desses processos completo.
 agrega diversos serviços de negócio.

Então imagina que, por exemplo, na hora de renovar a matrícula de um aluno da Alura eu realize todo o processo de matrícula, o que uma matrícula faz? Garante que o aluno está cadastrado, então insere o aluno ou atualiza se for necessário, insere o jogador, garante que ele está com os pontos atualizados, realiza o pagamento desse aluno, faz a matrícula financeira.

Então imagina que, por exemplo, na hora de renovar a matrícula de um aluno na ESCOLA eu realize todo o processo de matrícula, o que uma matrícula faz? Garante que o aluno está cadastrado, então insere o aluno ou atualiza se for necessário, insere o jogador, garante que ele está com os pontos atualizados, realiza o pagamento desse aluno, faz a matrícula financeira.

Só que além de matricular um aluno, eu preciso também nessa renovação de matrícula executar um processo de business intelligence, de data analytics ou qualquer outro processo
seja, eu vou pegar dados de tudo que o aluno fez, gerar relatórios , gerar métricas, para informar para ele tudo que ele fez no ano letivo anterior por exemplo.

Então eu tenho mais de um processo complexo em um processo maior.
O process aggregator pattern. É um padrão onde temos um tipo de serviço ainda mais de alto nível.

 um serviço de negócio agrega serviços de domínio, um process aggregator, um agregador de processos agrega serviços de negócio. Então serviços de domínio, serviços de negócio, agregadores de processo. Então são similares no conceito, mas vamos agregar tipos diferentes.



