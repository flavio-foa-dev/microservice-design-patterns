Service Discovery

A partir de um  IP e porta, outros microsserviços podem se comunicar utilizando o protocolo acordado, HTTP, gRPC, Só que, o que acontece? Lidar diretamente com IP pode trazer muitos problemas.

Então nós precisamos ter algum serviço que dê nomes para cada um dos nossos serviços. dns
mas Nem sempre nós vamos querer expor os nossos microsserviços na internet.

Então nós precisamos ter isso de forma interna para que nossa aplicação consiga encontrar todos os microsserviços. O mundo externo não precisa encontrar. Só que ainda assim, eu posso utilizar o DNS, mesmo não sendo DNS públicos. Eu posso ter um DNS específico na minha rede.

É importante nós entendermos o por trás do DNS - que é basicamente um registro de nomes.  serviço que te dá nome de domínio. Você vai informar que o IP 8.8.8.8 vai ter agora o nome ‘google.com’. Esse é nome. Sempre que alguém acessar ‘google.com’, vai cair nesse servidor. Essa é a ideia por trás do DNS.

O kubernetes, por exemplo, ou qualquer outro container em si. O próprio Docker, quando utilizamos o Docker Compose que tem vários containers, nós conseguimos fazer referência a outro container a partir do nome dele. Isso é DNS. Fora da minha máquina esse nome não quer dizer nada, não significa nada, mas aqui dentro nós temos um DNS interno.

estudar microsserviços é muito mais do que escrever código!
microsserviços depende muito de infraestrutura e redes. Talvez até mais do que de programação em si.

O conceito de Service Discovery, por exemplo, via de regra não exige nenhum desenvolvimento. Precisamos apenas configurar servidores de DNS.





