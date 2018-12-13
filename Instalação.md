# Instalação do NodeJS

O serviço do SAP foi testado no NodeJS versão 10.14. Instalar esta versão, ou versão LTS superior.
É necessário o NodeJS, e o NPM (https://www.npmjs.com/), normalmente instalados juntos.

## Windows

Basta realizar o download do instalador no site https://nodejs.org/en/

## Linux

Nas distribuições baseadas em Ubuntu, os repositórios das versões 16.04 e 18.04 não possuem a versão adequada para o sap. Sendo assim, é necessário adicionar repositórios adicionais por meio do recurso curl:

`sudo apt-get install curl`

`curl -sL https://deb.nodesource.com/setup_10.x | sudo bash -`

Em seguida, rodar o comando:

`sudo apt-get install nodejs`