Gataway especifico

Edge Pattern

entendemos um conceito de um API Gateway
gateways específicos para cada um do cliente.

E o nome disso, desses gateways específicos, é o edge pattern.
   um tipo de serviço um pouco mais próximo do cliente.  isso é basicamente um gateway específico para determinados clientes, que vai ter um foco nas necessidades reais daqueles clientes.

   E quando eu refiro sobre cliente, podemos interpretar como um cliente HTTP, alguém que vai chamar nossa API,
   por exemplo, ou cliente de negócio mesmo. Eu posso ter uma empresa que fornece criação de formulários e o cliente X precisa de formulário de uma forma, o cliente Y precisa de um formulário com uma pequena modificação.

   Então ao invés de modificar nossa lógica de negócios eu crio um novo edge, eu crio um novo serviço na frente, que vai receber a resposta desse formulário e modificar um pouco para esse cliente.

