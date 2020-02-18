# CENTOS 7 - TOTVS Protheus - MSSQL - Docker 64bits

## O que é Docker ?

Docker é um _runtime_ para execução de LinuX _Containers_ (LXC). Este repositório contém um conjunto de scripts para construir uma imagem do protheus com o mssql que poderá ser executada em qualquer host Linux que tenha o [Docker Engine](https://docs.docker.com/installation/) instalado.

## Como usar esta imagem ?

Instale o Docker Compose (https://docs.docker.com/compose/install/) e clone o repositório Git:

$ git clone https://github.com/fabinajm/docker-mssql-12125

Baixe os arquivos (appserver - https://www.dropbox.com/s/x080mw92n8dk5iv/appsrvlinux.tar.gz?dl=0
                   systemload - https://www.dropbox.com/s/574ejo15t9eunxn/systemload.tar.xz?dl=0 
                   license server - https://www.dropbox.com/s/h9ffzc6aqknh3oi/totvs.tar.xz?dl=0 
                   rpo - https://www.dropbox.com/s/547mv1tgt5yen4p/tttp120.tar.xz?dl=0 ) e copie para a pasta docker-mssql-12125 que o git criou. 
Abra o terminal e acesse a pasta do repositório (docker-mssql-12125), rode os comandos:

$ sudo docker-compose build 

$ sudo docker-compose up -d

Acesse o data azure studio (https://docs.microsoft.com/en-us/sql/azure-data-studio/download?view=sql-server-2017):

	Conecte como localhost, usuário: sa, senha: P@55w0rd
	Abra o arquivo que está dentro da pasta do git docker-mssql-12125/build/init.sql 
	Rode-o (F5)

O protheus estará pronto para ser acessado na porta: 1234, environment: local25, dbaccess: 7891 e webapp 8082.

## Como usar o container ?

Para listar os containers em execução:

$ sudo docker ps

Para parar a execução do container:

$ sudo docker stop docker-mssql-12125_dbaccess_1

Para iniciar a execução do container:

$ sudo docker start docker-mssql-12125_dbaccess_1

Para entrar dentro das pastas do container, rode o comando:

$ sudo docker exec -ti docker-mssql-12125_dbaccess_1 bash

Para copiar arquivos entre o computador e o container.

Computador para Container:

$ sudo docker cp foo.txt docker-mssql-12125_dbaccess_1:/foo.txt

Container para Computador:

$ sudo docker cp docker-mssql-12125_dbaccess_1:/foo.txt foo.txt

# Referência

* https://github.com/endersonmaia/totvs-protheus-docker
* https://cardano.github.io/blog/2017/11/15/mssql-docker-container
* https://registry.centos.org/microsoft/mssql-server-linux/latest
* https://medium.com/the-code-review/run-bash-or-any-command-in-a-docker-container-9a1e7f0ec204
* https://docs.microsoft.com/en-us/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-2017
* https://www.shellhacks.com/docker-cp-command-copy-file-to-from-container/
