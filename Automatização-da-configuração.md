# Automatização da configuração via FME

Esta seção dá exemplos de como utilizar o software FME Workbench 2018 ([SAFE Software](https://www.safe.com/)) para automatização partes da configuração do SAP.

## Criação de Unidades de Trabalho

A criação de unidade de trabalho pode ser executada em lote.

## Criação de Execução Etapa

Pode ser adicionada uma restrição de forma a não criar uma execucao_etapa mais de uma vez a unidade de trabalho acidentalmente.

## Criação de Insumos

A criação de insumos em lote pode ser feita de forma simples no FME. Primeiro passo é criar tipo_insumo que será utilizado e verificar o _id_.

## Associação de Insumos e Unidades de Trabalho

A rotina do FME abaixo exemplifica a associação entre insumos e unidade de trabalhos (tabela insumo_unidade_trabalho). A associação neste caso é feita baseada na padronização do nome tanto dos insumos quando da unidade de trabalho.

No exemplo abaixo a associação é feita espacialmente.

Pode ser adicionada uma restrição de forma a não associar o mesmo insumo mais de uma vez a unidade de trabalho acidentalmente.


