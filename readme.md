# Informações
O projeto está configurado para conseguir o IP de forma automática mas caso não funcione você pode executar esse comando:

    hostname -I
 
no WSL2 (Ubuntu) e adicionar o IP gerado no arquivo ```xdebug.ini``` da seguinte forma:

    # Arquivo xdebug.ini

    # Para PHP nas versões 7.4.33 e 8.5.x
    xdebug.client_host=SEU_IP

ou

    # Arquivo xdebug.ini

    # Para PHP na versão 5.6.40
    xdebug.remote_host=SEU_IP