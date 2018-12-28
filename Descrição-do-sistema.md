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

## lote

## banco_dados

## insumo

## tipo_insumo

## insumo_unidade_trabalho

## execucao_etapa

## tipo_situacao

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

## perfil_rotina

## tipo_rotina

## perfil_fme

# Funcionamento da Fila

## Casos especiais