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

# Instalação do Serviço do SAP

É necessário que exista um banco de dados PostgreSQL instalado. Não necessariamente precisa ser na mesma máquina que o serviço do SAP, porém deve ser possível ter o acesso via rede. O serviço foi testado nas versões 9.5, 9.6 e 10.6.

Realizar o download do repositório e extrair o conteúdo.

Navegar até a pasta executar o comando `npm install` para instalar as dependências. É necessário acesso a internet. Dependendo da rede pode ser necessário a configuração de proxy.

Executar o comando `npm run config` para configurar o serviço. Uma série de perguntas será feita e ao final o banco de dados PostgreSQL que persiste os dados do serviço e o arquivo de configuração _.env_ serão criados. As seguintes perguntas serão feitas:
1. Qual endereço de IP do banco de dados PostgreSQL?
2. Qual a porta do banco de dados PostgreSQL?
3. Qual o nome do usuário com permissão de criação de banco do PostgreSQL?
4. Qual a senha deste usuário?
5. Qual o nome do banco de dados para gerência do SAP?
6. Em qual porta será executado o serviço do SAP?
7. Deseja criar o banco de dados do SAP? (responder sim em caso de primeira instalação)

Caso já exista o arquivo .env essa configuração retornará um erro. Caso já exista o banco o usuário selecione que deseja criar um banco também retornará um erro.

Executar o comando `npm run dev` para iniciar o serviço. Caso deseje iniciar o serviço em background utilizar o comando `npm run production`, que executará o serviço com o nome _sap_ utilizando [PM2](http://pm2.keymetrics.io/).

# Plugin QGIS (Ferramentas de Produção)

Os operadores deverão utilizar o plugin [Ferramentas de Produção](https://github.com/1cgeo/Ferramentas_Producao) no QGIS para se comunicar com o SAP.

O plugin habilita um único botão no QGIS, que ao usuário clicar abre a tela do login. Basta o usuário preencher o endereço do serviço do SAP, seu usuário e senha do banco de dados PostgreSQL.

[[/images/login.PNG|Login]]