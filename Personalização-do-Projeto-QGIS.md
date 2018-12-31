# Acompanhamento visual

A cada subfase configurada é criada uma camada de acompanhamento (view) automaticamente pelo SAP. Essas camadas podem ser acessadas no schema _acompanhamento_.

As camadas de acompanhamento  são uma compilação das informações das diversas etapas de uma subfase por unidade de trabalho, permitindo que o gerente possa analisar mais facilmente o andamento de uma subfase.

[[/images/tabela_acompanhamento.PNG|Tabela acompanhamento]]

Além da visão tabular é interessante configurar estilos para esta camada, permitindo um acompanhamento visual do andamento da subfase.

[[/images/estilo_acompanhamento.PNG|Estilo acompanhamento]]

O estilo deve ser configurado com gerente, e variará conforme a configuração da subfase. A forma mais simples de preparar o estilo no QGIS é utilizar a simbologia baseada em regra e realizar os testes conforme a figura a seguir.

[[/images/configuracao_estilo.PNG|Configuração estilo]]

É também interessante criar grupos no painel de navegação do QGIS, e separar as camadas de acompanhamento por projeto.

# Verificando Unidades de Trabalho

É comum necessitar de verificar as unidades de trabalho de uma determinada subfase, de modo a conferir se todas foram criadas corretamente, ou para habilitá-las (tornar _disponivel = true_).

A forma mais simples de realizar essa tarefa é aplicar filtros a camada unidade_trabalho. O filtro será da forma `"subfase_id" = 14` onde o id da subfase (_14_ no exemplo) deve ser verificado na tabela subfase. 

# Verificando Execução Etapa

A camada execucao_etapa com o tempo conterá muitas linhas, o que dificultará sua pesquisa diretamente no QGIS. De forma a organizar a leitura dessa camada é interessante ter múltiplas cópias desta camada e aplicar filtros.

Para cada subfase criar uma cópia da camada execucao_etapa. Em cada uma aplicar um filtro utilizando o atributo _etapa_id_ e referenciado todos os ids das etapas que pertencem a aquela subfase, por exemplo, `"etapa_id" IN (28,29,30,31,32)`.

Também é interessante organizar as camadas de execucao_etapa por projeto.

# Utilização de camadas SQL

QGIS permite a criação da camadas que são o resultado de uma SQL. Essas camadas então podem ser configuradas com rótulos e auxiliar no acompanhamento da produção.

Em _Banco de Dados_ > _Gerenciador BD_ pode se utilizar _Janela SQL_ para executar uma Query SQL e carregar o resultado como uma nova camada. Após executar a SQL deve-se definir a coluna que contém valores únicos, e a coluna com a geometria e clicar no botão carregar.

[[/images/janela_sql.PNG|Janela SQL]]

A SQL abaixo retorna informações sobre as atividades em execução.

`SELECT ee.unidade_trabalho_id, ut.nome AS unidade_trabalho_nome, ee.operador_atual AS operador_atual_id,u.nome_guerra AS operador_atual_nome, ee.etapa_id, su.nome AS subfase_nome, et.nome AS etapa_nome, ee.situacao AS situacao_id, si.nome AS situacao, ee.data_inicio
FROM macrocontrole.execucao_etapa AS ee
INNER JOIN macrocontrole.unidade_trabalho AS ut ON ut.id = ee.unidade_trabalho_id
INNER JOIN sdt.usuario AS u ON u.id = ee.operador_atual
INNER JOIN macrocontrole.subfase_etapa AS se ON se.id = ee.subfase_etapa_id
INNER JOIN macrocontrole.subfase AS su ON su.id = se.subfase_id
INNER JOIN macrocontrole.etapa AS et ON et.id = se.etapa_id
INNER JOIN macrocontrole.situacao AS si ON si.code = ee.situacao
WHERE (ee.operador_atual is not null AND ee.data_inicio is not null AND ee.data_fim is null) OR ee.situacao in  (2,3)
ORDER BY ee.data_inicio ASC`

