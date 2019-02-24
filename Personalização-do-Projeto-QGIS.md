# Geração do projeto padrão

Após configurado o SAP, ao executar o comando `npm run project` é criado na pasta do SAP o arquivo _sap_config.qgs_, que é um projeto para QGIS 3.4 utilizado como interface de configuração da SAP.

# Acompanhamento visual

A cada subfase configurada é criada uma camada de acompanhamento (view) automaticamente pelo SAP. Essas camadas podem ser acessadas no schema _acompanhamento_.

As camadas de acompanhamento  são uma compilação das informações das diversas etapas de uma subfase por unidade de trabalho, permitindo que o gerente possa analisar mais facilmente o andamento de uma subfase.

[[/images/tabela_acompanhamento.PNG|Tabela acompanhamento]]

Além da visão tabular é interessante configurar estilos para esta camada, permitindo um acompanhamento visual do andamento da subfase.

[[/images/estilo_acompanhamento.PNG|Estilo acompanhamento]]

O estilo deve ser configurado com gerente, e variará conforme a configuração da subfase. A forma mais simples de preparar o estilo no QGIS é utilizar a simbologia baseada em regra e realizar os testes conforme a figura a seguir.

[[/images/configuracao_estilo.PNG|Configuração estilo]]

É também interessante criar grupos no painel de navegação do QGIS, e separar as camadas de acompanhamento por projeto.

# Outras camadas de acompanhamento


# Verificando Unidades de Trabalho

É comum necessitar de verificar as unidades de trabalho de uma determinada subfase, de modo a conferir se todas foram criadas corretamente, ou para habilitá-las (tornar _disponivel = true_).

A forma mais simples de realizar essa tarefa é aplicar filtros a camada unidade_trabalho. O filtro será da forma `"subfase_id" = 14` onde o id da subfase (_14_ no exemplo) deve ser verificado na tabela subfase. 

# Verificando Atividades

A camada _atividade_ com o tempo conterá muitas linhas, o que dificultará sua pesquisa diretamente no QGIS. De forma a organizar a leitura dessa camada é interessante ter múltiplas cópias desta camada e aplicar filtros.

Para cada subfase criar uma cópia da camada execucao_etapa. Em cada uma aplicar um filtro utilizando o atributo _etapa_id_ e referenciado todos os ids das etapas que pertencem a aquela subfase, por exemplo, `"etapa_id" IN (28,29,30,31,32)`.

Também é interessante organizar as camadas de execucao_etapa por projeto.

# Utilização de camadas SQL

QGIS permite a criação da camadas que são o resultado de uma SQL. Essas camadas então podem ser configuradas com rótulos e auxiliar no acompanhamento da produção.

Em _Banco de Dados_ > _Gerenciador BD_ pode se utilizar _Janela SQL_ para executar uma Query SQL e carregar o resultado como uma nova camada. Após executar a SQL deve-se definir a coluna que contém valores únicos, e a coluna com a geometria e clicar no botão carregar.

[[/images/janela_sql.PNG|Janela SQL]]

