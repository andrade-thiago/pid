# Criação da Estrutura do Projeto

O primeiro passo é a criação da estrutura do projeto seguindo os seguintes passos:
1. Adicionar um novo projeto na camada _projeto_.
2. Associar fases de forma ordenada ao projeto criado utilizando a camada _fase_.
3. Adicionar subfases a cada fase associada ao projeto utilizando a camada _subfase_. Subfases devem ser ordenadas dentro de uma fase.
4. Associar etapas as subfases criadas utilizando a camada _etapa_. Etapas devem ser ordenadas dentro de uma subfase.
5. Definir restrições entre as etapas criadas. As restrições devem ser entre etapas de uma mesma subfase. Atentar para cadastrar etapas que ocorrem primeiro em _etapa id anterior_.

# Criação das Atividades de Trabalho

Devem ser criadas as unidades de trabalho e suas execucao_etapa seguindo os seguintes passos:
1. Definir banco de dados de produção na camada _banco_dados_.
2. Definir os lotes de produção na camada _lote_.
3. Criação das unidades de trabalho na cada _unidade_trabalho_.
4. Para cada unidade de trabalho devem ser definidas quais etapas serão executadas utilizando a camada execucao_etapa.

O passo 3 e 4 podem ser feitos em lote conforme é descrito em [[Automatização da configuração|Automatização da configuração]].

# Associação de Insumos

Insumos podem ser associados a unidades de trabalho seguindo os seguintes passos:
1. Criar os tipos de insumo que podem existir utilizando a camada _tipo_insumo_.
2. Criar os insumos utilizando a camada _insumo_.
3. Associar os insumos as unidades de trabalho utilizando a camada _insumo_unidade_trabalho_.

Os passos 2 e 3 podem ser feitos em lote conforme é descrito em [[Automatização da configuração|Automatização da configuração]].

# Criação dos Usuários

Os usuários que irão participar da produção podem ser cadastrados seguindo os seguintes passos:
1. Criar o usuário na camada _usuario_. É necessário que os usuários tenham login já criado no banco de dados PostgreSQL.
2. Associar um perfil do sistema ao usuário caso necessário utilizando a camada _usuario_perfil_sistema_.

# Definição da Sequência de Execução

A fila de execução pode ser definida utilizando os seguintes passos:
1. Criação de um perfil de produção na camada _perfil_producao_.
2. Associar as etapas de forma ordenada que farão parte do perfil de produção criado na camada _perfil_producao_etapa. 
3. Associar um perfil de produção a um usuário utilizando a camada _perfil_producao_operador_.

Utilizar as camadas _fila_prioritaria_grupo_ e _fila_prioritaria_ para distribuição em casos especiais.

# Configurações das Atividades

Cada atividade a ser distribuída pode ser configurada da seguinte forma:
1. Cadastrar camadas espaciais que existem no banco de dados de produção na camada _camada_.
2. Utilizar a camada _perfil_propriedades_camada_ para definir quais camadas o usuário terá acesso durante a execução de uma determinada etapa.
3. Utilizar a camada _perfil_estilo_ para definir quais estilos o o usuário terá acesso durante a execução de uma determinada etapa.
4. Utilizar a camada _perfil_menu_ para definir quais menus de classificação o o usuário terá acesso durante a execução de uma determinada etapa.
5. Utilizar a camada _perfil_rotina_ para definir quais rotinas de validação o o usuário terá acesso durante a execução de uma determinada etapa.
6. Utilizar a camada _perfil_regras_ para definir quais regras de atributação o o usuário terá acesso durante a execução de uma determinada etapa.
7. Utilizar a camada _perfil_fme_ para definir quais rotinas do FME Manager o o usuário terá acesso durante a execução de uma determinada etapa.
8. Utilizar a camada _requisito_finalizacao_ para definir o checklist de finalização de uma determinada etapa.

# Camadas de Acompanhamento

Carregar as camadas de acompanhamento criadas dinamicamente no schema _acompanhamento_. Mais informações sobre camadas de acompanhamento e outras configurações do projeto em [[Personalização do Projeto QGIS|Personalização do Projeto QGIS]].