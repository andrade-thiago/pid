# Descrição Geral

# Descrição das Classes

## projeto

A produção deve ser organizada em projetos. O projeto possui o atributo _nome_.

## fase

Um projeto é composto de uma ou mais fases de produção. As fases são de um determinado _tipo fase_. As fases são ordenadas dentro de um projeto.

## tipo_fase

Os _tipo_fase_ são as fases padrão da produção cartográfica da Diretoria de Serviço Geográfico, por exemplo, _Digitalização_, _Reambulação_, _Validação_, _Edição_, etc.

## subfase

As subfases são os processos que os Centros de Geoinformação realizam de fato, estando em uma granularidade maior que a fase. Exemplos de subfase são: _Digitalização de Transportes_, _Digitalização de Edificações_, etc.
Uma subfase pertence a fase. As subfases podem ocorrer em paralelo dentro de uma fase.

## etapa

As subfases são executadas através de uma ou mais etapas. Etapas são as operações básicas a serem realizadas pelos usuários, como revisão, correção, execução. As etapas são de um determinado _tipo etapa_. As etapas são ordenadas dentro de uma subfase.

## tipo_etapa

Exemplos de tipo_etapa são: _Execução_, _Revisão 1_, _Correção 1_, _Revisão 2_, etc. Tipo_etapas são de um determinado _tipo processo_.

## tipo_processo

Os tipos de processo em uma produção cartográfica, sendo eles _Execução_, _Revisão_ ou _Correção_.

## restricao_etapa

Etapas podem ter restrição de distribuição baseado em quem executou uma etapa anterior. Um padrão comum na DSG é que que executou uma etapa não pode revisá-la, ou quem deve corrigir os apontamentos de uma revisão é o mesmo operador que executou a determinada subfase. Esse tipo de lógica pode ser inserida no sistema com restricao_etapa.

## tipo_restricao

Os tipos de restrição implementados no sistema, sendo eles _Operadores distintos_, _Operadores iguais_, _Operadores no mesmo turno_.

## unidade_trabalho

Camada espacial
Geográfico
etapas de uma subfase são realizadas
lote
banco de dados

## lote

## banco_dados

## insumo

Camada espacial para cadastramento dos insumos utilizados na produção. Contém os atributos _nome_, _caminho_ (onde a localização é armazenada), _epsg_ (sistema de coordenadas do insumo). Insumos são de um determinado _tipo insumo_.

## tipo_insumo

Classe utilizada para categorizar insumos, de modo a facilitar a associação pelo gerente de produção.

## insumo_unidade_trabalho

Associação entre unidades de trabalho e insumos. Quando um insumo é associado a unidade de trabalho ele passa a ser distribuído para o operador.

## execucao_etapa

Classe onde é armazenada as informações de execução de uma etapa. Contém informações de _data de ínicio_, _data fim_ e _operador_ (classe _usuario_). Uma execucao_etapa é associada a uma única unidade de trabalho, e a uma única etapa.  As execucao_etapa possuem um determinado _tipo situacao_.

## tipo_situacao

Os tipos possíveis de situação de uma execucao_etapa, sendo eles _Não iniciada_, _Em execução_, _Pausada_, _Finalizada_, _Não será executada_.

## usuario

## tipo_perfil_sistema

## tipo-posto_grad

## tipo_turno

## perfil producao

## perfil_producao_etapa

## perfil_producao_operador

## fila_prioritaria

## fila_prioritaria_grupo

## requisito_finalizacao

## perfil_estilo

## perfil_regras

## perfil_menu

## perfil_propriedades_camada

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

## Casos especiais