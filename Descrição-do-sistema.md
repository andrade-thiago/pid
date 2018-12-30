# Descrição Geral

O SAP é composto por três partes, um serviço HTTP (este repositório) desenvolvido em Node.Js, um plugin QGIS utilizado como cliente ([Ferramentas de Produção](https://github.com/1cgeo/Ferramentas_Producao)), e um projeto do QGIS utilizado para configurar o SAP.

# Descrição das Classes

## projeto

A produção deve ser organizada em projetos. O projeto possui o atributo _nome_.

## fase

Um projeto é composto de uma ou mais fases de produção. As fases são de um determinado _tipo_fase_. As fases são ordenadas dentro de um projeto.

## tipo_fase

Os _tipo_fase_ são as fases padrão da produção cartográfica da Diretoria de Serviço Geográfico, por exemplo, _Digitalização_, _Reambulação_, _Validação_, _Edição_, etc.

## subfase

As subfases são os processos que os Centros de Geoinformação realizam de fato, estando em uma granularidade maior que a fase. Exemplos de subfase são: _Digitalização_de_Transportes_, _Digitalização_de_Edificações_, etc.
Uma subfase pertence a fase. As subfases podem ocorrer em paralelo dentro de uma fase.

## etapa

As subfases são executadas através de uma ou mais etapas. Etapas são as operações básicas a serem realizadas pelos usuários, como revisão, correção, execução. As etapas são de um determinado _tipo_etapa_. As etapas são ordenadas dentro de uma subfase.

## tipo_etapa

Exemplos de tipo_etapa são: _Execução_, _Revisão 1_, _Correção 1_, _Revisão 2_, etc. Tipo_etapas são de um determinado _tipo_processo_.

## tipo_processo

Os tipos de processo em uma produção cartográfica, sendo eles _Execução_, _Revisão_ ou _Correção_.

## restricao_etapa

Etapas podem ter restrição de distribuição baseado em quem executou uma etapa anterior. Um padrão comum na DSG é que que executou uma etapa não pode revisá-la, ou quem deve corrigir os apontamentos de uma revisão é o mesmo operador que executou a determinada subfase. Esse tipo de lógica pode ser inserida no sistema com restricao_etapa.

## tipo_restricao

Os tipos de restrição implementados no sistema, sendo eles _Operadores distintos_, _Operadores iguais_, _Operadores no mesmo turno_.

## unidade_trabalho

Camada espacial que define onde um usuário irá executar sua atividade. Tal camada permite que o projeto seja subdividido geograficamente em polígonos arbitrários (não necessariamente MI). Unidades de trabalho possuem _nome_, _epsg_. Unidades de trabalho podem estar disponíveis ou não (atributo _disponivel), no sentido que unidades de trabalho não disponíveis não são distribuídas pelo sistema. Unidades de trabalho são vinculadas a um banco de dados de produção e a uma única subfase. Elas também pertencem obrigatoriamente a um lote. Unidades de trabalho possuem uma prioridade dentro de uma subfase (e um lote)

## lote

Lotes organizam a prioridade em que unidades de trabalho são executadas. Eles possuem atributo _nome_ e _prioridade_.

## banco_dados

Definição do banco de dados de produção (onde a manipulação de geometria será feita). Possui atributo _nome_, _servidor_, _porta_.

## insumo

Camada espacial para cadastramento dos insumos utilizados na produção. Contém os atributos _nome_, _caminho_ (onde a localização é armazenada), _epsg_ (sistema de coordenadas do insumo). Insumos são de um determinado _tipo insumo_.

## tipo_insumo

Classe utilizada para categorizar insumos, de modo a facilitar a associação pelo gerente de produção.

## insumo_unidade_trabalho

Associação entre unidades de trabalho e insumos. Quando um insumo é associado a unidade de trabalho ele passa a ser distribuído para o operador.

## execucao_etapa

Classe onde é armazenada as informações de execução de uma etapa. Contém informações de _data de ínicio_, _data fim_ e _operador_ (classe _usuario_). Uma execucao_etapa é associada a uma única unidade de trabalho, e a uma única etapa.  As execucao_etapa possuem um determinado _tipo situacao_.

As execucao_etapa que são distribuídas aos operadores, baseado nas propriedades dos operadores, unidade de trabalho e das etapas. Sendo assim elas devem ser criadas para que o sistema as distribua.

## tipo_situacao

Os tipos possíveis de situação de uma execucao_etapa, sendo eles _Não iniciada_, _Em execução_, _Pausada_, _Finalizada_, _Não será executada_.

## usuario

Usuario que executa as atividades do SAP. Possui atributos _nome_, _nome_guerra_, _login_. Possui um turno de trabalho (_tipo_turno_id_) e um posto ou graduação (_tipo_posto_grad_id_).

O usuário deve existir com o mesmo login no PostgreSQL do SAP (e do banco de produção, caso seja distinto).

O usuário deve ter permissão no banco de dados da atividade que irá receber.

## tipo-posto_grad

Posto ou graduação do usuário. Utilizado somente para facilitar a identificação.

## tipo_turno

Turno que o usuário trabalha (_manhã_, _tarde_, ou _integral_). Utilizado como informação para o gerente de produção, e no sistema no caso da restrição _Operadores no mesmo turno_.

## tipo_perfil_sistema

Perfil do usuário no sistema. Atualmente utilizado apenas para habilitar certos usuários a configurar o menu de classificação (necessitando perfil superior a _operador_).

## perfil producao

Cria um perfil de produção. Possui o atributo _nome_.

## perfil_producao_etapa

Define a prioridade de etapas de um perfil de produção.  Deve ser definida uma etapa (_etapa_id_) e a prioridade correspondente a esta etapa. É associado a um _perfil_producao_ (_perfil_producao_id).

Para um perfil de produção deve-se criar quantos perfil_producao_etapa quanto necessário para definir as possíveis etapas que o perfil de produção pode executar. O ordenamento dessas etapas influencia na fila de produção.

## perfil_producao_operador

Associa um perfil_producao a um operador (_usuario_).

## fila_prioritaria

Classe utilizada para casos especiais de distribuição de atividades. Ela associa um operador (_usuario_) a uma _execucao_etapa_ com uma certa prioridade. Sempre que existir uma atividade na fila prioritária de um operador esta será distribuída em detrimento da fila padrão.

A prioridade permite ordenar multiplas _execucao_etapa_ a um operador.

Em geral deve-se utilizar a fila padrão, somente utilizar fila_prioritaria quando por algum motivo se exigir que uma determinada pessoa execute uma determinada tarefa (de forma pontual).

Não respeita restricao_etapa, perfil_producao e ordenamento de etapas.

## fila_prioritaria_grupo

Classe utilizada para casos especiais de distribuição de atividades. Ela associa um _perfil_producao_ a uma _execucao_etapa_ com uma certa prioridade. Sempre que existir uma atividade na fila prioritária de perfil de produção esta será distribuída para qualquer usuário daquele perfil em detrimento da fila padrão.

A prioridade permite ordenar multiplas _execucao_etapa_ a um perfil de produção.

Em geral deve-se utilizar a fila padrão, somente utilizar fila_prioritaria_grupo quando por algum motivo existirem atividades que não podem ser executadas pelo operador original (por estar de férias por exemplo) e qualquer operador de um determinado perfil puder executar aquela tarefa.

Não respeita restricao_etapa, perfil_producao e ordenamento de etapas.

## requisito_finalizacao

Utilizados para criar um checklist de ações a serem realizadas durante uma etapa. Tal checklist é exibido no plugin Ferramentas de Produção, e somente permite a finalização da atividade se todo o checklist for marcado.

## perfil_estilo

Permite a configuração dos estilos disponíveis para uma etapa. Possui o atributo _nome_, onde é informado o nome do estilo, e deve ser associado a uma etapa.

O estilo deve estar cadastrado no banco de dados (tabela _layer_styles_) e deve seguir o padrão de nomenclatura {{Nome do estilo}} | {{Nome da classe}}, por exemplo reambulacao|constr_edificacao_a

Múltiplos estilos podem estar associado a uma etapa.

## perfil_regras

Permite a configuração de regras de atributação para uma etapa. Possui o atributo _nome_, onde é informado o nome do grupo de regras, e deve ser associado a uma etapa.

As regras devem estar cadastradas no banco de dados (tabela _layer_rules_).

Múltiplos grupos de regras podem estar associado a uma etapa.

## perfil_menu

Permite a configuração de menus de atributação para uma etapa. Possui o atributo _nome_, onde é informado o nome do menu, e deve ser associado a uma etapa.

Os menus devem estar cadastradas no banco de dados (tabela _menu_profile_).

Múltiplos menus podem estar associado a uma etapa.

## perfil_propriedades_camada

Associa uma camada do banco de dados de produção a uma etapa. É utilizado para definir que camadas um usuário tem acesso durante a execução de uma etapa.

## camada

Classe que guarda o nome das camadas do banco de dados geográficos de trabalho, por exemplo _constr_edificacao_a_. Não é necessário informar o schema.

Não é fixado os nomes das camadas da ET-EDGV de modo a dar flexibilidade ao uso de outras modelagens, como a EDGV Pro.

## perfil_rotina

Classe utilizada para disponibilizar rotinas python para uma determinada etapa. Deve ser informado o tipo de rotina (_tipo_rotina_), a camada em que a rotina será executada (_camada_id_), a camada que os erros serão armazenados (_camada_apontamento_id_), e os parâmetros no formato JSON caso necessário (_parametros_).

**Esta classe será remodelada de forma a se integrar com o DSGTools 4**

## tipo_rotina

Lista de rotinas que atualmente podem ser disponibilizadas. Atualmente são as seguintes rotinas _outOfBoundsAngles_, _invalidGeometry_ e _notSimpleGeometry_.

## perfil_fme

Classe utilizada para integrar o FME Manager com o SAP. Deve ser cadastrado para a etapa desejada o servidor do FME Manager (com porta) e qual categoria deve ser disponibilizada naquela etapa.

**Esta classe será remodelada de forma a se integrar com perfil_rotina**

# Funcionamento da Fila

A distribuição automática de atividades é baseada em uma fila dinamica que é calculada no momento que o usuário requisita uma nova atividade. Seguindo a ordem de prioridade dos lotes, para cada etapa do perfil de produção do operador é verificado se existe alguma execucao_etapa disponível (não inicada) para aquela etapa e lote. Caso tenha é distribuída a execucao_etapa com a unidade de trabalho de maior prioridade para o operador, caso contrário é verificado a próxima etapa do perfil de produção.

O procedimento se repete em todo o perfil de produção e todos os lotes caso não seja encontrado execucao_etapas disponíveis. Caso não tenha nenhuma disponível o plugin Ferramentas_Producao avisará o usuário para entrar em contato com Gerente de Produção.

A fila respeita a ordem das etapas em uma subfase, e a restricao_etapa.

## Casos especiais

Utilizando as classes _fila_prioritaria_ e fila_prioritaria_grupo_ pode-se distribuir atividades foram da fila padrão de distribuição, inclusive ignorando a ordem das etapas em uma subfase e a restricao_etapa.

Em geral _fila_prioritaria_ é utilizada para distribuir uma execucao_etapa específica para um operador específico, que normalmente ocorre quando uma região é complicada e se deseja que um operador mais experiente a execute.

Em geral _fila_prioritaria_grupo_ é utilizada para distribuir execucao_etapa de operadores de férias, normalmente correção, que não seriam distribuídas pelo sistema devido a restricao_etapa.