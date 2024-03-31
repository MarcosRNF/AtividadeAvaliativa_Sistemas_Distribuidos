# Instruções para Compilar e Executar o Aplicativo: #

### Compilação: ###
Certifique-se de ter o **JDK (Java Development Kit)** instalado em seu sistema.
Abra um terminal e navegue até o diretório onde os arquivos **ChatServer.java** e **ChatClient.java** estão localizados.

### Compile os arquivos Java utilizando o comando javac: ###
#### javac ChatServer.java ####
#### javac ChatClient.java ####

### Execução do Servidor: ###
Com os arquivos compilados, inicie o servidor primeiro:
##### java ChatServer #####

### Execução do Cliente: ###
Abra um novo terminal e navegue até o diretório onde os arquivos compilados estão localizados.

### Inicie o cliente utilizando o comando: ###
##### java ChatClient #####

## Arquitetura do Sistema: ##
O sistema de chat implementado utiliza uma arquitetura cliente-servidor. Nesse modelo, o servidor atua como um ponto central que coordena a comunicação entre vários clientes conectados. Cada cliente estabelece uma conexão com o servidor para enviar e receber mensagens.
O servidor é responsável por receber as mensagens de todos os clientes conectados e transmiti-las para os destinatários apropriados sem perder nenhuma informação.

### Funcionamento do Sistema: ###

##### Servidor (ChatServer): #####
Iniciando o Servidor:

O servidor é iniciado e começa a ouvir por conexões na porta especificada.
Quando um cliente se conecta, o servidor aceita a conexão e cria uma nova thread para lidar com as comunicações com esse cliente.

##### Tratamento de Clientes: #####

Para cada cliente conectado, o servidor cria uma instância de **ClientHandler** em uma nova *thread*.
O **ClientHandler** é responsável por receber as mensagens do cliente e encaminhá-las para todos os outros clientes conectados.

##### Recebendo e Encaminhando Mensagens: #####

Dentro do **ClientHandler**, o servidor aguarda continuamente por mensagens do cliente.
Quando uma mensagem é recebida, o servidor a encaminha para todos os clientes conectados, incluindo o remetente.

##### Cliente (ChatClient): #####
*Conexão com o Servidor:*

O cliente tenta se conectar ao servidor especificado pelo endereço IP e porta.
Uma vez conectado, o cliente exibe uma mensagem de confirmação.

##### Envio de Mensagens: #####

O servidor aguarda a entrada do usuário no console.
Quando o usuário digita uma mensagem, ela é enviada para o servidor através do socket de saída.

##### Recebimento de Mensagens: #####

O cliente também inicia uma thread (ServerListener) para ouvir mensagens recebidas do servidor.
Quando uma mensagem é recebida, ela é exibida no console do cliente.
