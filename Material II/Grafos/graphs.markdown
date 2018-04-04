Grafos
///conceptos: grafos,aristas, nodos, outdegree,indegree


Representación de un Grafo

Para representar y almacenar un grafo se puede realizar de varias maneras. A continuación, se presentan distintas maneras de realizarlo.

Matriz de Adyacencia

Una matriz de adyacencia es una forma de representar el grafo tal que, sobre la matriz en posición $[i,j]$, hay una marca, indicando que los nodos $i$ y $j$ están unidos por una arista.
La principal ventaja de ésta forma de almacenar el grafo es que las consultas sobre si un nodo $i$ está conectado a un nodo $j$ son *constantes*, es decir, tienen una complejidad $O(1)$ sobre el tiempo.
No obstante, su principal desventaja es el gran costo que implica almacenarlo, ya que tiene una complejidad en memoria de $O(N^{2})$.

Una matriz de adyacencia puede hacerse utilizando una matriz de booleanos. Para una arista que une los nodos $(i,j)$, la posición $[i,j]$ de la matriz estará marcada con true. 
Dependiendo del tipo de grafo en cuestión, esa misma arista puede ser bidireccional o no, es decir, que usando la misma arista se puede . Si se trabaja sobre un grafo no dirigido, la arista *es* bidireccional, por lo que se puede ir del nodo $i$ al nodo $j$ y viceversa; es decir, al registrar la arista, tanto $[i,j]$ como $[j,i]$ se marcarán.
Por otra parte, si el grafo es dirigido, la arista *no es* bidireccional. Al marcar la posición $[i,j]$ no se marca al mismo tiempo $[j,i]$, lo que representa que, a menos que una arista distinta lo permita, no es posible ir del nodo $i$ al nodo $j$.

En una matriz de adyacencia se pueden manejar aristas ponderadas, utilizando una matriz de enteros en lugar de una de booleanos, donde la posición $[i,j]$ tiene guardado el peso de la arista que conecta a los nodos $i$ y $j$. En caso de no existir dicha arista, se pueden poner valores como *-1* o 0, indicando que no hay camino de $i$ a $j$. Sin embargo, en caso de existir pesos negativos o pesos con 0, ésto no funcionaría, por lo que se deben buscar otras maneras de indicar la ausencia de aristas, tales como elegir otro valor que se sabe que no se ocupará, o utilizar una matriz de booleanos para consultar la existencia de la arista y una de enteros para conocer su peso.

A continuación, se muestran ejemplos de grafos dirigidos, no dirigidos y ponderados y su representación en una matriz de adyacencia. Nótese que los valores "true" son representados con un 1 y "false" con 0.

![adjacencyMatrix](adjacencyMatrix.png)

Mientras que consultar si los nodos $i$ y $j$ están conectados es constante, revisar todas las adyacencias de un nodo tiene una complejidad *lineal*, es decir, $O(N)$, por lo que hay que tener cuidado con éste aspecto. 

//////desventaja sobre que no puedes conectar los mismos nodos por diferentes aristas
