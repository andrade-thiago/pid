# Criação da Estrutura do Projeto

O primeiro passo é a criação da estrutura do projeto seguindo os seguintes passos:
1. Adicionar um novo projeto na camada _projeto_.
2. Para cada tipo de produto que será gerado no projeto deve ser criada uma _linha_producao_.
3. Criação dos produtos associados com a linha de produção na camada _produto_.
4. Associar fases de forma ordenada a linha de produção criado utilizando a camada _fase_.
5. Adicionar subfases a cada fase associada a linha de produção utilizando a camada _subfase_. Subfases devem ser ordenadas dentro de uma fase.
6. Associar etapas as subfases criadas utilizando a camada _etapa_. Etapas devem ser ordenadas dentro de uma subfase.
7. Definir restrições entre as etapas criadas. As restrições devem ser entre etapas de uma mesma subfase. Atentar para cadastrar etapas que ocorrem primeiro em _etapa id anterior_.

# Criação das Unidades de Trabalho

Devem ser criadas as unidades de trabalho e suas atividades seguindo os seguintes passos:
1. Definir banco de dados de produção na camada _banco_dados_.
2. Definir os lotes de produção na camada _lote_.
3. Criação das unidades de trabalho na cada _unidade_trabalho_.
4. Para cada unidade de trabalho devem ser definidas quais etapas serão executadas utilizando a camada atividade.

O passo 3 e 4 podem ser feitos em lote conforme é descrito em [[Automatização da configuração|Automatização da configuração]].

# Associação de Insumos

Insumos podem ser associados a unidades de trabalho seguindo os seguintes passos:
1. Criar os grupos de insumo que podem existir utilizando a camada _grupo_insumo_.
2. Criar os insumos utilizando a camada _insumo_ (deve ser associado _grupo_insumo_ e _tipo_insumo_).
3. Associar os insumos as unidades de trabalho utilizando a camada _insumo_unidade_trabalho_.

Os passos 2 e 3 podem ser feitos em lote conforme é descrito em [[Automatização da configuração|Automatização da configuração]].

# Criação dos Usuários

Os usuários que irão participar da produção podem ser cadastrados seguindo os seguintes passos:
1. Criar o usuário na camada _usuario_. É necessário que os usuários tenham login já criado no banco de dados PostgreSQL que será feita a aquisição da geoinformação.
2. Associar um perfil do sistema ao usuário caso necessário utilizando a camada _usuario_perfil_sistema_. **(opcional)**

# Definição da Sequência de Execução

A fila de execução pode ser definida utilizando os seguintes passos:
1. Criação de um perfil de produção na camada _perfil_producao_.
2. Associar as etapas de forma ordenada que farão parte do perfil de produção criado na camada _perfil_producao_etapa. 
3. Associar um perfil de produção a um usuário utilizando a camada _perfil_producao_operador_.

Utilizar as camadas _fila_prioritaria_grupo_ e _fila_prioritaria_ para distribuição em casos especiais.

# Configurações das Atividades

Cada atividade a ser distribuída pode ser configurada da seguinte forma:
1. Cadastrar camadas que serão editadas e que existem no banco de dados de produção na camada _camada_.
2. Utilizar a camada _perfil_propriedades_camada_ para definir quais camadas o usuário terá acesso durante a execução de uma determinada etapa.
3. Utilizar a camada _perfil_estilo_ para definir quais estilos o o usuário terá acesso durante a execução de uma determinada etapa.
4. Utilizar a camada _perfil_menu_ para definir quais menus de classificação o o usuário terá acesso durante a execução de uma determinada etapa.
5. Utilizar a camada _perfil_rotina_ para definir quais rotinas de validação o o usuário terá acesso durante a execução de uma determinada etapa.
6. Utilizar a camada _perfil_regras_ para definir quais regras de atributação o o usuário terá acesso durante a execução de uma determinada etapa.
7. Utilizar a camada _perfil_fme_ para definir quais rotinas do FME Manager o o usuário terá acesso durante a execução de uma determinada etapa.
8. Utilizar a camada _perfil_linhagem_ para definir em quais etapas os operadores terão acesso a linhagem daquela subfase. **(em desenvolvimento)**
9. Utilizar a camada _perfil_monitoramento_ para definir qual tipo de monitoramento será aplicado a determinada etapa. **(em desenvolvimento)**
10. Utilizar a camada _atributo_ para criar alias nos atributos desejados para exibição no QGIS.
11. Utilizar a camada _requisito_finalizacao_ para definir o checklist de finalização de uma determinada etapa.

# Camadas de Acompanhamento

Carregar as camadas de acompanhamento criadas dinamicamente no schema _acompanhamento_. Mais informações sobre camadas de acompanhamento e outras configurações do projeto em [[Personalização do Projeto QGIS|Personalização do Projeto QGIS]].

# Camadas adicionais para fins de geração de metadados

**(Em desenvolvimento)**

# Camadas adicionais para criação de questionários

**(Em desenvolvimento)**

# Camadas adicionais para fins de Relatório Técnico Mensal

**(Em desenvolvimento)**
1. Preenchimento da camada _meta_anual_ para cada fase de cada projeto para o ano atual.
2. Utilização da camada _perda_recurso_humano_ para informar perda de tempo de produção de certos operadores.