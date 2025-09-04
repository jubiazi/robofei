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

1. código instalação

sudo apt update
sudo apt install ros-humble-turtlesim

para checar se está instalado:
ros2 pkg executables turtlesim

2. código inicialização

ros2 run turtlesim turtlesim_node

abaixo do comando, haverá mensagens do nó. ali, pode-se ver o nome padrão da tartaruga e as coordenadas onde ela é gerada, a janela do simulador deve aparecer, com uma tartaruga no centro.

3. uso turtlesim

