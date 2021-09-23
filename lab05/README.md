# Aluno
* `169366`: `<Gustavo Mantellatto Elias>`

## Tarefa de Cypher sobre Marcadores e Taxonomia

## Tarefa 1

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, sem considerar as categorias subordinadas.

### Resolução
~~~cypher
MATCH (n:Marcador)-[:Pertence]->(m:Categoria{id: "Serviços"})
RETURN n
~~~

## Tarefa 2

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, considerando as categorias subordinadas.

### Resolução
~~~cypher
MATCH (m: Marcador)-[:Pertence]->(c: Categoria), (c1: Categoria {id: "Serviços"})
WHERE (c)-[:Superior *]->(c1) OR c.id = 'Serviços'
RETURN m
~~~
