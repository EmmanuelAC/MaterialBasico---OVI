# Introducci�n

La **b�squeda en profundidad** es una de las t�cnicas fundamentales dentro de las ciencias computacionales. Tambi�n conocida como *Depth First Search (DFS)* es un tipo de b�squeda recursiva, cuyo funcionamiento se basa en el ***backtracking***.

A grandes rasgos, la finalidad de una DFS es que, dado un espacio de b�squeda, explore todas las posibilidades que se puedan generar dentro de �ste. Lo anterior permite encontrar un *estado �ptimo* con respecto a cierto criterio, o llegar a un estado en particular, registrando informaci�n en el proceso, como la cantidad de estados para llegar al objetivo desde el estado inicial.

# Funcionamiento de la B�squeda en Profundidad 

Para comprender el funcionamiento del *backtracking*, se necesitan comprender tres conceptos. Dos de �stos son *estado padre* y *estado hijo*. Un *estado padre* es aquel a partir del cual se pueden llegar a otros estados, derivados de �ste; aquellos "nuevos" estados se conocen como *estados hijos*. De lo anterior, se puede extraer que dos estados son *hermanos* si ambos son hijos del mismo estado padre, es decir, se encuentran en el mismo "nivel" en la b�squeda.

Para ejemplificar de mejor manera lo anterior, utilicemos el siguiente esquema que representa el espacio de b�squeda, el cual, a su vez, puede ser visto como un �rbol, d�nde los estados se muestran como nodos:

![relationship](relationship.png)

En �ste caso, el estado A es *padre* de los estados B, C y D, por lo que se puede decir que B, C y D son *hijos* de A; a su vez, dichos tres estados son *hermanos* entre s�.

Una vez comprendidos los conceptos anteriores, se define como *backtracking* a la t�cnica, donde, desde un estado inicial, se avanza hacia yendo a todos los estados hijos, posteriormente a los hijos de �stos, y as� consecutivamente. Se contin�a yendo por cada estado hacia su hijo, uno a la vez, de modo que cada estado solo se visite en una �nica ocasi�n dentro de la ruta que se sigue.

Al momento de avanzar en el espacio de b�squeda, se exploran todos los hijos de un estado en concreto antes de explorar los estados del mismo nivel. De �sta forma, se sigue un camino en concreto, que, una vez explorado, se modifica para que explore otros estados dentro del mismo espacio de b�squeda.

![DFS](DFS.gif)

# Diferencia entre Amplitud y Profundidad

Es de ah� donde surge la naturaleza ***recursiva*** de la DFS: al momento de explorar el espacio de b�squeda por medio de profundidad, se explora un estado y los hijos de �ste, antes de explorar los estados hermanos y sus subsecuentes hijos; tomar estados hermanos en lugar del que se explora actualmente y visitar sus hijos queda pendiente mediante la **recursi�n**, la cual es llevada a cabo mediante diferentes instancias de una misma funci�n, o mediante una estructura ***Stack*** de la STL. La recursi�n se encargar� de que, una vez que se termine un camino y el estado actual no puede generar hijos y/o los que genera fueron visitados con anterioridad, aquellos estados hermanos y los caminos que nazcan de �stos sean visitados y se sigan nuevas v�as. �sto se traduce como *visitar todas las posibilidades en el espacio de b�squeda*. 

A diferencia de una *b�squeda en amplitud (Breadth First Search � BFS)*, donde se exploran todos los estados hermanos derivados de un mismo padre y, posteriormente, los hijos y descendencia de dichos estados, en una b�squeda en profundidad se visitan todos los hijos del estado actual y despu�s los estados hermanos y su diferencia.

A continuaci�n, se puede apreciar la comparaci�n entre el funcionamiento de una BFS contra una DFS.

![BFSvsDFS](BFSvsDFS.gif)
 


