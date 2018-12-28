# FME Manager

O [FME Manager](https://github.com/1cgeo/fme_manager) é utilizado para gerenciamento do FME Workbench 2018 ([SAFE Software](https://www.safe.com/)).

O FME Manager pode ser integrado ao SAP, permitindo que o operador execute rotinas do FME a partir do QGIS, com o preenchimento automático de parâmetros de acordo com sua atividade.

# Configuração do FME Manager

Verifique a [Wiki](https://github.com/1cgeo/fme_manager/wiki/Integração-SAP) do FME Manager.

# Configuração SAP

De modo a habilitar um conjunto de rotinas do FME Manager em uma etapa de produção deve-se preencher a tabela _perfil fme_ no SAP.

Deve ser preenchido o servidor do serviço do FME Manager (com porta), o ID da categoria a ser disponibilizada, e a etapa de produção no qual a rotina será disponibilizada.

Em caso de necessidade de disponibilização de mais de uma categoria ela pode ser separada por vírgula.

[[/images/perfil_fme.PNG|Perfil_FME]]
