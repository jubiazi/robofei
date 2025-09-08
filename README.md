# robofei

## CLI tools

I. configuração de ambiente

1. para pegar um arquivo: source /opt/ros/humble/setup.bash
é necessário rodar esse comando em toda "new shell" que abrir para ter acesso aos comandos do ROS2

2. para não ter que procurar o arquivo toda vez que abrir uma "new shell", adicionar esse comando:
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc

3. checar variáveis do ambiente

executar o sourcing dos arquivos de configuração do ROS 2 definirá diversas variáveis de ambiente necessárias para operar o ROS 2. se houver problemas para encontrar ou usar seus pacotes do ROS 2, certificar se o ambiente esteja configurado corretamente usando o comando:
printenv | grep -i ROS 
(checar se as variavéis ROS_DISTRO e ROS_VERSION estão configuradas)

4. variavél ROS_DOMAIN_ID

depois de determinar um número inteiro único para o seu grupo de nós do ROS 2, a variável de ambiente pode ser definida com o seguinte comando:
export ROS_DOMAIN_ID=<your_domain_id>
e para manter essa configuração entre as sessões do shell, adicionar o comando: "~/.bashrc"
echo "export ROS_DOMAIN_ID=<your_domain_id>" >> ~/.bashrc

5. variavél ROS_LOCALHOST_ONLY

por padrão, a comunicação do ROS 2 não é limitada ao localhost. a variável de ambiente ROS_LOCALHOST_ONLY permite restringir a comunicação do ROS 2 apenas ao localhost. isso significa que o seu sistema ROS 2 não fica visível para outros computadores na rede local. o uso da ROS_LOCALHOST_ONLY é útil em certos contextos, como em salas de aula, onde vários robôs podem publicar no mesmo tópico, o que causaria comportamentos inesperados.a variável é definida com o comando:
export ROS_LOCALHOST_ONLY=1
e para manter essa configuração entre as sessões do shell, adicionar o comando: "~/.bashrc"
echo "export ROS_LOCALHOST_ONLY=1" >> ~/.bashrc

II. uso de turtlesim, ros2 e rqt

II.1 turtlesim

é um simulador simples para aprender os conceitos básicos do ROS 2, como nós, tópicos e serviços

1. código instalação

sudo apt update
sudo apt install ros-humble-turtlesim

para checar se está instalado:
ros2 pkg executables turtlesim

2. código inicialização

ros2 run turtlesim turtlesim_node

abaixo do comando, haverá mensagens do nó. ali, pode-se ver o nome padrão da tartaruga e as coordenadas onde ela é gerada, a janela do simulador deve aparecer, com uma tartaruga no centro.

3. uso

em um novo terminal (já com source executado):
ros2 run turtlesim turtle_teleop_key

II.2 ros2

permite gerenciar, inspecionar e interagir com o sistema ROS 2, como iniciar nós, ajustar parâmetros e escutar tópicos

II.3 rqt

é uma interface gráfica que facilita manipular componentes do ROS 2 de forma mais amigável, embora tudo isso também possa ser feito via terminal

1. código instalação

sudo apt update
sudo apt install '~nros-humble-rqt*'

para executar:
rqt

2. uso

quando rodar pela primeira vez, selecionar "Plugins > Services > Service Caller" para chamar os serviços

III. entendendo nós

cada nó no ROS deve ser responsável por uma única finalidade modular, por exemplo, controlar os motores das rodas. cada nó pode enviar e receber dados de outros nós por meio de tópicos, serviços, ações ou parâmetros. um sistema robótico completo é composto por vários nós trabalhando em conjunto. no ROS 2, um único executável (programa em C++, programa em Python, etc.) pode conter um ou mais nós.

IV. entendendo tópicos

o ROS 2 divide sistemas complexos em vários nós modulares, os tópicos são um elemento fundamental, atuando como um barramento para que os nós troquem mensagens.

V. entendendo serviços

os serviços são outro método de comunicação entre nós. os serviços são baseados em um modelo de chamada e resposta, em contraste com o modelo publisher-subscriber dos tópicos. enquanto os tópicos permitem que os nós "assinem" fluxos de dados e recebam atualizações contínuas, os serviços fornecem dados apenas quando são chamados especificamente por um cliente.

VI. entendendo parâmetros

um parâmetro é um valor de configuração de um nó, são como configurações do nó. um nó pode armazenar parâmetros como inteiros, números de ponto flutuante (floats), valores booleanos, strings e listas. no ROS 2, cada nó mantém seus próprios parâmetros. 

VII. entendendo ações 

as actions são um tipo de comunicação no ROS 2 projetado para tarefas de longa duração, são compostas por três partes: objetivo (goal), retorno (feedback) e resultado (result).

são baseadas em tópicos e serviços, semelhantes aos serviços, mas com duas diferenças principais: podem ser canceladas e fornecem feedback contínuo, em vez de apenas uma resposta única.

as actions seguem o modelo cliente-servidor: um nó cliente envia um objetivo a um nó servidor, que o reconhece e retorna tanto o fluxo de feedback quanto o resultado final.

##Client Libraries

I. Usando o colcon para compilar pacotes

1. código instalação

sudo apt install python3-colcon-common-extensions

2. workspace

depois de criar o workspace, verificar se os 4 diretórios estão lá:
(.
├── build
├── install
├── log
└── src

4 directories, 0 files)

3. código para testar

colcon test

4. procurando no ambiente

Antes de poder usar qualquer executável ou biblioteca instalada, você precisará adicioná-los aos seus paths e aos caminhos de bibliotecas. O colcon terá gerado arquivos bash/bat no diretório install para ajudar a configurar o ambiente. Esses arquivos adicionam todos os elementos necessários aos paths e caminhos de bibliotecas, além de fornecer quaisquer comandos de shell ou bash exportados pelos pacotes.

código: source install/setup.bash

II. Criando um workspace

III. Criando um pacote

IV. Escrevendo um publisher e subscriber simples (C++)
