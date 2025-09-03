# robofei

1. para pegar um arquivo: source /opt/ros/humble/setup.bash
é necessário rodar esse comando em toda "new shell" que abrir para ter acesso aos comandos do ROS2

2. para não ter que procurar o arquivo toda vez que abrir uma "new shell", adicionar esse comando:
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc

3. checar variáveis do ambiente

Sourcing ROS 2 setup files will set several environment variables necessary for operating ROS 2. If you ever have problems finding or using your ROS 2 packages, make sure that your environment is properly set up using the following command:
