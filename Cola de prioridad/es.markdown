Antes de ver la estructura de datos llamada *cola de prioridad*, vamos a ver algunos conceptos para la adecuada del funcionamiento de la misma:

# Concepto de �rbol

Un �rbol es una estructura de datos compuesta de nodos y aristas que es ac�clica. Un �rbol que no tiene ning�n nodo se llama �rbol vac�o o nulo. Un �rbol que no est� vac�o consta de un nodo ra�z y potencialmente muchos niveles de nodos adicionales que forman una jerarqu�a. Las caracter�sticas principales de un �rbol es que si tiene $N$ nodos, entonces tendr� $N-1$ aristas y que hay al menos un camino entre cada par de nodos.

![�rbol](arbol.png)

# Terminolog�a utilizada en �rboles

* Nodo: Es una estructura que puede contener un valor o condici�n, es la unidad fundamental de la que est�n formados los grafos.

* Aristas: Es una relaci�n entre nodos

* Ra�z: El nodo superior de un �rbol.

* Hijo: Un nodo conectado directamente con otro cuando se aleja de la ra�z.

* Padre: Un nodo conectado directamente con otro cuando se acerca a la ra�z.

* Hoja: Un nodo sin hijos.

* Grado de un nodo: Es el n�mero de hijos que tiene

* Profundidad: La profundidad de un nodo es el n�mero de aristas desde la ra�z del �rbol hasta un nodo.

* Altura de un �rbol: Es la profundidad del nodo m�s profundo.

* �rbol binario: Tipo de �rbol en donde cada nodo puede tener a lo m�s dos nodos hijos.

# Concepto de mont�culo

Un mont�culo o heap es una estructura de datos del tipo �rbol con informaci�n perteneciente a un conjunto ordenado. Los mont�culos m�ximos tienen la caracter�stica de que cada nodo padre tiene un valor mayor que el de cualquiera de sus nodos hijos, mientras que en los mont�culos m�nimos, el valor del nodo padre es siempre menor al de sus nodos hijos. En un mont�culo de prioridad, el mayor elemento (o el menor, dependiendo de la relaci�n de orden escogida) est� siempre en el nodo ra�z. Por ejemplo:

En la STL existe una estructura de datos llamada cola de prioridad o priority_queue ya implementada, que en realidad es un heap binario de m�ximos, es decir, que permite extraer los valores insertados en orden decreciente. Una cola de prioridad es una estructura donde se guardan datos de modo que el mayor de ellos pueda ser consultado o eliminado. En cierto modo, es como una cola o una pila donde los elementos no se ordenan seg�n el orden en el que se han insertado, sino seg�n su valor.

# Funcionamiento de un heap binario de m�ximos

Una cola de prioridad se implementa mediante un heap binario de m�ximos el cual sus funciones b�sicas en el �rbol son:

* A�adir un elemento al heap

* Devolver cual es el elemento m�ximo

* Eliminar el elemento m�ximo

Si el heap tiene N elementos, entonces el heap tiene una altura de log2(N). En la ra�z del heap se debe encontrar el m�ximo elemento y se cumple que cada nodo padre tiene un valor mayor que el de cualquiera de sus nodos hijos. Al insertar un elemento se realiza el siguiente proceso: el valor se agrega como un nodo en el siguiente espacio disponible en el heap y subir� mientras �l sea mayor a su padre hasta el momento o si llega a ser la ra�z.

![Insertar1](insertar1.png)

![Insertar2](insertar2.png)

![Insertar3](insertar3.png)

![Insertar4](insertar4.png)

![Eliminar1](eliminar1.png)

![Eliminar2](eliminar2.png)

![Eliminar3](eliminar3.png)

![Eliminar4](eliminar4.png)

# Uso de stl::priority_queue

Para que tu programa use colas de prioridad, es necesario a�adir #include &lt;queue&gt; y using namespace std; (este �ltimo para no tener que poner $stl::$ cada vez que usemos las coas de prioridad) al principio de tu c�digo. Todos los elementos de una cola de prioridad son del mismo tipo, y �ste se debe especificar en el momento de crearlo: $priority_queue < T > N$ es una cola de prioridad cuyos elementos son de tipo $T$ y su nombre es $N$. 

#Problema de ejemplo

# [Buscando una estrella][1]

Podemos observar que si m�ltiplicamos por -1 cada elemento a insertar en la priority_queue ahora el heap es de m�nimos. 

* C�digo:

# Tarea

* List Game

* Adivina

* Lavando platos 

[1]: https://omegaup.com/arena/problem/Buscando-una-estrella#problems
