## PROJETO UC10

## - INSTALAÇÃO DO LINUX UBUNTU

## Primeiro começaremos a instalar o VM do UBUNTU no VirtualBox. Quando eu terminei de instalar, eu instalei o cockpit pelo terminal do UBUNTU, apontei as portas dentro da VirtualBox para acessar o cockpit em um navegador colocando o seguinte endereço: http://127.0.0.1:9090. IP automático do Linux é: “127.0.0.1”. A PORTA pode ser qualquer uma, mas para uma questão de organização coloquei “9090” e no IP do convidado SEMPRE coloque “10.0.2.15”.

## - INSTALAÇÃO DO DOCKER, DOCKER-COMPOSE, ADMINER E WORDPRESS

## Depois de instalar o DOCKER dentro do cockpit usando o seguinte código: sudo apt install docker.
## Instalei o DOCKER-COMPOSE com o código: sudo apt install docker-compose.
## Agora para instalar o ADMINER e o WORDPRESS criei um editor de texto usando a ferramenta VIM com o seguinte código: vim docker-compose.yml.
## Dentro desse editor de texto coloquei o seguinte código para instalação do ADMINER e o WORDPRESS:

version: '3.1'

services: 
    
    db:
        image: mysql:latest
        restart: always
        environment:
            MYSQL_ROOT_PASSWORD: senac@123
            MYSQL_DATABASE: site
        ports:
            - '6556-3306'
        volumes:
            - ~/site-db:/var/lib/mysql
        expose: 
            - '3306'
            
    wordpress:
        image: wordpress
        restart: always
        environment:
            WORDPRESS_DB_HOST: db
            WORDPRESS_DB_USER: root
            WORDPRESS_DB_PASSWORD: senac@123
            WORDPRESS_DB_NAME: site
            WORDPRESS_TABLE_PREFIX: ps
        ports:
            - '8084:80'
        volumes:
            - ~/site-wordpress:/var/www/html
    adminer:
        image: adminer
        restart: always
        ports:
            - '8085:8080'

## Depois saia com ESC, e na caixa de texto logo a baixo, eu digitei: “:wq” para sair e salvar.
## E para executar o código use: docker-compose up

## ATENÇÃO
## Muito cuidado com a tabulação no caso o TAB, sempre reveja o código para não dar erro, pois a construção do código é bem detalhada e correta, de modo que quando abrir as chaves, diretórios e etc, terá que ficar perfeitamente alinhado, caso contrário começara a dar erro.


## - CONFIGURAÇÃO DO ADMINER E O WORDPRESS

## Depois da instalação do ADMINER e o WORDPRESS, eu apontei os IPS e as PORTAS dentro do VirtualBox.


## Ubuntu: 127.0.0.1:9090 || 10.0.2.15:9090
## MYSQL_Docker: 127.0.0.1:6556 || 10.0.2.15:6556
## Adminer: 127.0.0.1: 8085 || 10.0.2.15:8085
## Wordpress	IpDaSuaMáquina ou IpAutomáticoDoLinux	8084	10.0.2.15	8084

## Para acessar o ADMINER em qualquer navegador: http://127.0.0.1:8085.

## Para acessar o WORDPRESS em qualquer navegador: http://10.26.44.26:8084.
## PS: Esse IP é da minha máquina REAL mas você pode usar o IP automático do Linux.


## O MYSQL é usado para criar um Banco de Dados para armazenamento e manipulação de dados.

## O ADMINER é uma ferramenta de gerenciamento de Banco de Dados baseados em PHP.

## E o WORDPRESS é uma das ferramentas mais simples para criar e desenvolver um site.

