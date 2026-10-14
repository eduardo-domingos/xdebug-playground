# Sobre
Esse projeto se trata de um mini laboratório para configurar e testar diverentes versões do php com xdebug
Tecnologias utilizadas:

- Windows 11 v26h2
- WSL 2 v3.0.3.0
- Docker Desktop v4.95.0
- VsCode v1.141.2
- PHP (5.6, 7.4 e 8.5)
- Xdebug v2 e v3
    

## Configurações

### IP
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

### Porta

No arquivo ```launch.json``` as portas que forem configuradas devem ser referenciadas no arquivo ``` xdebug.ini ```

    # Arquivo launch.json
    {
        "name": "PHP 5.6 - Xdebug 2",
        "type": "php",
        "request": "launch",
        "port": 9000,
        "pathMappings": {
            "/var/www/html": "${workspaceFolder}/src"
        },
        "log": true
    },


    # Arquivo xdebug.ini
    xdebug.remote_port=9000

e

    # Arquivo launch.json
    {
        "name": "PHP 7.4 - Xdebug 3",
        "type": "php",
        "request": "launch",
        "port": 9003,
        "pathMappings": {
            "/var/www/html": "${workspaceFolder}/src"
        },
        "log": true
    },

    # Arquivo xdebug.ini
    xdebug.client_port=9003

e

    # Arquivo launch.json
    {
        "name": "PHP 8.5 - Xdebug 3",
        "type": "php",
        "request": "launch",
        "port": 9005,
        "pathMappings": {
            "/var/www/html": "${workspaceFolder}/src"
        },
        "log": true
    }

    # Arquivo xdebug.ini
    xdebug.client_port=9005

Repara que no PHP 5.6 é ```xdebug.remote_port``` e no PHP 7.4 e 8.5 é ```xdebug.client_port```

### Outras versões do PHP
este projeto permite adicionar várias outras versões do php com xdebug basta seguir a estrutura de services do arquivo ```docker-compose.yml```, a estrutura de pastas/arquivos que está dentro da pasta ```docker```, e a configuração do nginx que está no arquivo ```default.conf```