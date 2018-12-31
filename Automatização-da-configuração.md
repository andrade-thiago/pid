# Automatização da configuração via FME

Esta seção dá exemplos de como utilizar o software FME Workbench 2018 ([SAFE Software](https://www.safe.com/)) para automatização partes da configuração do SAP.

## Criação de Unidades de Trabalho

A criação de unidade de trabalho pode ser executada em lote. A figura abaixo demonstra uma rotina do FME que lê um conjunto de imagens no formato ECW, transforma as imagens em polígonos utilizando seu _bounding box_, corta cada polígono em 4 partes, cria uma sobreposição entre os polígonos e insere no banco SAP.

[[/images/fme_unidade_trabalho.PNG|FME Unidade de Trabalho]]

Deve-se atentar que o sistema de coordenadas do SAP é EPSG:4674, necessitando que os polígonos sejam reprojetados antes de serem inseridos. Na rotina do FME também foi utilizado o transformer _counter_ para criar artificialmente uma prioridade entre as unidades de trabalho.

O corte em 4 e a sobreposição é opcional, e depende da necessidade de cada subfase. 

A rotina pode ser acessada em [unidade_trabalho.fmw](https://github.com/1cgeo/sap/wiki/fme/unidade_trabalho.fmw):

## Criação de Execução Etapa

Para um conjunto de unidades_trabalho de uma determinada subfase pode-se criar em lote todas as execucao_etapa associadas a elas. O gerente deve saber os ids de todas as etapas que deseja associar as unidade de trabalho, bem com o id da subfase.

Foi inserida uma restrição (utilizando _FeatureMerger_) de forma a não criar uma execucao_etapa mais de uma vez a unidade de trabalho acidentalmente.

A rotina pode ser acessada em [etapa.fmw](https://github.com/1cgeo/sap/wiki/fme/etapa.fmw).

## Criação de Insumos

A criação de insumos em lote pode ser feita de forma simples no FME. Primeiro passo é criar tipo_insumo que será utilizado e verificar o _id_.  A figura abaixo demonstra uma rotina do FME que lê um conjunto de imagens no formato ECW, transforma as imagens em polígonos utilizando seu _bounding box_ e insere no banco do SAP.

[[/images/fme_insumo.PNG|FME Insumo]]

A rotina pode ser acessada em [insumo.fmw](https://github.com/1cgeo/sap/wiki/fme/insumo.fmw).

## Associação de Insumos e Unidades de Trabalho

Pode ser implementada uma rotina do FME que realiza a associação entre insumos e unidade de trabalhos (tabela insumo_unidade_trabalho). A associação normalmente é feita baseada na padronização do nome tanto dos insumos quando da unidade de trabalho, porém tal associação também pode ser feita espacialmente.

Pode ser adicionada uma restrição de forma a não associar o mesmo insumo mais de uma vez a unidade de trabalho acidentalmente conforme foi feito com _execucao_etapa_.

Exemplos de rotina pode ser acessados em:
* [Insumo_unidade_trabalho_1.fmw](https://github.com/1cgeo/sap/wiki/fme/Insumo_unidade_trabalho_1.fmw): Associando utilizando o padrão de nomenclatura.
* [Insumo_unidade_trabalho_2.fmw](https://github.com/1cgeo/sap/wiki/fme/Insumo_unidade_trabalho_2.fmw): Utilizando somente o insumo que intersecta o centroide da unidade de trabalho.
* [Insumo_unidade_trabalho_3.fmw](https://github.com/1cgeo/sap/wiki/fme/Insumo_unidade_trabalho_3.fmw): Utilizando filtro espacial



