O plugin Ferramentas de Produção pode ser acessado em [Ferramentas de Produção](https://github.com/1cgeo/Ferramentas_Producao)

# Login

O plugin habilita um único botão no QGIS, que ao usuário clicar abre a tela do login. Basta o usuário preencher o endereço do serviço do SAP, seu usuário e senha do banco de dados PostgreSQL.

[[/images/login.PNG|Login]]

# Iniciando uma atividade

Após efetuar o login, o sistema verificará se já existe uma atividade em execução para o usuário. Caso não exista o sistema perguntará se o usuário deseja iniciar uma nova atividade.

[[/images/inicio_atividade.PNG|Inicio atividade]]

Após o inicio da atividade aparecerá a tela principal do sistema, onde aparece o nome da atividade a ser realizada.

[[/images/atividade_1.PNG|Finaliza atividade 1]]

Após finalizar uma atividade o sistema também perguntará se o usuário deseja iniciar uma nova atividade.

# Carregando camadas

Após logar (e com uma atividade) o operador terá acesso a uma série de abas. A primeira aba é _Carregar Camadas_ onde será exposto quais camadas o usuário está habilitado a carregar. Para carrega-las basta o usuário clicar no botão _Carregar_.

[[/images/carrega_camada.PNG|Carrega camadas]]

Caso tenham estilos definidos, o usuário também pode escolher o estilo que se deseja carregar as camadas no menu acima do _Carregar Camadas_.

As camadas são carregadas organizadas alfabeticamente e por geometria. Em todas as camadas é aplicado um filtro espacial conforme a unidade de trabalho correspondente. Também é criada uma camada virtual de moldura.

Caso o usuário deseje apenas trocar os estilos de uma conjunto de camadas já carregados não é necessário remover as camadas e carregar novamente. O sistema detectará que as camadas já estão carregadas e aplicará a troca de estilos.

# Carregando insumos

Os insumos associados a atividade serão apresentados na aba _Insumos_. Ao clicar sobre o nome do insumo o usuário deve escolher a pasta que o insumo será salvo. Caso o insumo tenha extensão _.tif_ ou _.ecw_ o sistema carregará automáticamente no QGIS. Caso contrário o usuário deve manualmente carregar o arquivo.

[[/images/insumo.PNG|Carrega insumos]]

O usuário deve atentar para utilizar pastas sem caracteres especiais ou espaços para salvar os insumos.

# Executando Rotinas

Na aba rotinas são acessadas as rotinas do FME e as rotinas do _perfil_rotina_, sendo opaco para usuário qual o tipo de rotina está sendo executada. Os parâmetros também são preenchidos automaticamente pelo plugin.

Após a execução da rotina aparecerá uma mensagem informando se ela foi realizada com sucesso.

# Regras de Atributação e Estatística de Regras

Caso tenha regras de atributação definidas, ao carregar as camadas podem ser carregadas um ou mais conjuntos de regras de atributação. Tais regras serão avaliadas na tabela de atributos e ao formulário de feições, atribuindo cores a atributos que falharam uma determinada regra.

A aba estatística de regras permite que o usuário veja um sumário de que camadas possuem feições que falharam algum grupo de regras de atributação.

Caso o usuário deseje remover as regras basta carregar novamente as camadas sem selecionar as regras disponíveis (não é necessário remover as camadas)

# Atalhos

Na aba _Atalhos_ o usuário pode verificar os atalhos que o Ferramentas de Produção define como padrão no QGIS.

[[/images/atalhos.PNG|Atalhos]]

# Menu de classificação

Caso tenham menus de classificação definidos eles podem ser acessados a partir dos botões abaixo dos estilos. O botão abrirá o menu com a configuração disponível.

Na aba Configuração do menu, usuários com permissão (perfil sistema superior a operador) podem alterar e criar novos menus.

# Finalizando uma atividade

Uma vez que o usuário completou a atividade ele pode finalizar na tela principal do sistema clicando no botão _Finalizar Atividade_

[[/images/atividade_1.PNG|Finaliza atividade 1]]

Caso a atividade tenha requisitos cadastrados estes aparecerão como um checklist que o usuário deve marcar antes de finalizar a atividade.

[[/images/atividade_1.PNG|Finaliza atividade 1]]

Ao clicar em _Finalizar Atividade_ uma janela de confirmação aparecerá para o usuário. Nela o usuário deve digitar o login de forma a confirmar a finalização da atividade.

[[/images/finaliza_atividade.PNG|Confirmação de finalização]]

# Outras funcionalidades

## Filtro espacial

O usuário somente pode acessar geometrias que intersectem com sua área de trabalho.

## Bloqueio espacial

O usuário não consegue criar feições fora de sua área de trabalho.

## Aviso para salvar

A cada 5 minutos, caso alguma camada tenha feições não salvas aparecerá um aviso relembrando o usuário de salvar.