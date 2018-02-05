Antes de ver la estructura de datos llamada *cola de prioridad*, vamos a ver algunos conceptos para la adecuada comprensi�n del funcionamiento de la misma:

# Concepto de �rbol

Un �rbol es una estructura de datos compuesta de nodos y aristas que es ac�clica. Un �rbol que no tiene ning�n nodo se llama �rbol vac�o o nulo. Un �rbol que no est� vac�o consta de un nodo ra�z y potencialmente muchos niveles de nodos adicionales que forman una jerarqu�a. Las caracter�sticas principales de un �rbol es que si tiene $N$ nodos, entonces tendr� $N-1$ aristas y que hay al menos un camino entre cada par de nodos.

<center>![�rbol](arbol.png)</center>

# Terminolog�a utilizada en �rboles

* Nodo: Es una estructura que puede contener un valor o condici�n, es la unidad fundamental de la que est�n formados los grafos.

* Aristas: Es una relaci�n entre nodos.

* Ra�z: El nodo superior de un �rbol.

* Hijo: Un nodo conectado directamente con otro cuando se aleja de la ra�z.

* Padre: Un nodo conectado directamente con otro cuando se acerca a la ra�z.

* Hoja: Un nodo sin hijos.

* Grado de un nodo: Es el n�mero de hijos que tiene

* Profundidad: La profundidad de un nodo es el n�mero de aristas desde la ra�z del �rbol hasta un nodo.

* Altura de un �rbol: Es la profundidad del nodo m�s profundo.

* �rbol binario: Tipo de �rbol en donde cada nodo puede tener a lo m�s dos nodos hijos.

# Concepto de mont�culo

Un mont�culo o heap es una estructura de datos del tipo �rbol con informaci�n perteneciente a un conjunto ordenado. Los mont�culos m�ximos tienen la caracter�stica de que cada nodo padre tiene un valor mayor que el de cualquiera de sus nodos hijos, mientras que en los mont�culos m�nimos, el valor del nodo padre es siempre menor al de sus nodos hijos. En un mont�culo de prioridad, el mayor elemento (o el menor, dependiendo de la relaci�n de orden escogida) est� siempre en el nodo ra�z.

En la STL existe una estructura de datos llamada cola de prioridad o priority_queue ya implementada, que en realidad es un heap binario de m�ximos, es decir, que permite extraer los valores insertados en orden decreciente. Una cola de prioridad es una estructura donde se guardan datos de modo que el mayor de ellos pueda ser consultado o eliminado. En cierto modo, es como una cola o una pila donde los elementos no se ordenan seg�n el orden en el que se han insertado, sino seg�n su valor.

# Funcionamiento de un heap binario de m�ximos

Una cola de prioridad se implementa mediante un heap binario de m�ximos el cual sus funciones b�sicas en el �rbol son:

* A�adir un elemento al heap

* Devolver cu�l es el elemento m�ximo

* Eliminar el elemento m�ximo

Si el heap tiene N elementos, entonces el heap tiene una altura de log2(N). En la ra�z del heap se debe encontrar el m�ximo elemento y se cumple que cada nodo padre tiene un valor mayor que el de cualquiera de sus nodos hijos. Al insertar un elemento se realiza el siguiente proceso: el valor se agrega como un nodo en el siguiente espacio disponible en el heap y subir� mientras �l sea mayor a su padre hasta el momento o si llega a ser la ra�z. Esta operaci�n dura log2(N) por recorrer a lo m�s la altura del heap. Por ejemplo:

Heap inicial:

<center>![Insertar1](insertar1.png)</center>

Inserci�n del 34:

<center>![Insertar2](insertar2.png)</center>

<center>![Insertar3](insertar3.png)</center>

<center>![Insertar4](insertar4.png)</center>

Para eliminar el elemento m�ximo, es decir la ra�z del heap, y mantener el orden de los nodos se sigue el siguiente proceso: reemplace el valor en la ra�z con el valor del �ltimo nodo del heap, quita esa hoja del heap y ahora navegue por el heap, intercambiando valores para restaurar la propiedad de la orden: cada vez, si el valor en el nodo actual es menor que uno de sus hijos, cambie su valor con el hijo m�s grande (eso asegura que el nuevo valor padre es m�s grande que sus dos hijos). Esta operaci�n dura log2(N) por recorrer a lo m�s la altura del heap. Por ejemplo:

Heap inicial:

<center>![Eliminar1](eliminar1.png)</center>

Eliminar:

<center>![Eliminar2](eliminar2.png)</center>

<center>![Eliminar3](eliminar3.png)</center>

<center>![Eliminar4](eliminar4.png)</center>

# Uso de stl::priority_queue

Para que tu programa use colas de prioridad, es necesario a�adir #include &lt;queue&gt; y using namespace std; (este �ltimo para no tener que poner $stl::$ cada vez que usemos las colas de prioridad) al principio de tu c�digo. Todos los elementos de una cola de prioridad son del mismo tipo, y �ste se debe especificar en el momento de crearlo: priority&#95;queue < T > N es una cola de prioridad cuyos elementos son de tipo $T$ y su nombre es $N$. 

Las funciones de la priority_queue son:

* $empty()$ devuelve true si la cola de prioridad est� vac�a.

* $size()$ devuelve el n�mero de elementos en la cola de prioridad.

* $top()$ devuelve el m�ximo valor en la cola de prioridad.

* $push(x)$ inserta el valor $x$ en la cola de prioridad.

* $pop()$ elimina el m�ximo valor en la cola de prioridad. Primero hay que checar si hay elementos en la cola de prioridad para usar adecuadamente esta funci�n.

Es importante que los tipos de datos que usemos en la cola de prioridad sean comparables (casi todos los datos en C++ son comparables, al menos que sea un struct definido por nosotros mismos sin un operador de comparaci�n).

#Problema de ejemplo

# [Buscando una estrella][1]

Podemos observar que si m�ltiplicamos por -1 cada elemento a insertar en la priority_queue ahora el heap es de m�nimos. Ahora las operaciones se pueden ver de la siguiente manera

* $S$: Si hay al menos 3 datos, sacar tres datos de la cola de prioridad (ser�n las tres valores m�nimos insertados), multiplicar por -1 cada uno (valor original), imprimirlos, multiplicarlos por -1 para insertarlos nuevamente en la cola de prioridad. En caso de no tener al menos 3 elementos imprimir "NO HAY SUFICIENTES PUNTAJES".

* $R$: Leer $x$, multiplicarlo por -1 e insertarlo a la cola de prioridad.

* $B$: Si hay elementos en la cola de prioridad, eliminar con pop().

Al final, si la cola de prioridad est� vac�a, imprimir "NO HUBO GANADOR", en caso contrario sacar de la cola de prioridad todos los valores, quedarte con el �ltimo eliminado e imprimir "EL PUNTAJE MAS ALTO FUE "+ ese n�mero por -1 (valor original).

* C�digo:

<pre>
#include&lt;queue&gt;
#include&lt;stdio.h&gt;
#define ll long long int
using namespace std;
priority_queue &lt; ll &gt; pq;
ll N, x, y, z;
char ins;
int main()
{
    scanf("%lld", &N);
    while(N--)
    {
        scanf(" %c", &ins);
        if(ins=='S')
        {
            if(pq.size()<3)
            {
                printf("NO HAY SUFICIENTES PUNTAJES\n");
            }
            else
            {
                x=pq.top();
                pq.pop();
                y=pq.top();
                pq.pop();
                z=pq.top();
                pq.pop();
                x*=-1;
                y*=-1;
                z*=-1;
                printf("%lld %lld %lld\n", x, y, z);
                x*=-1;
                y*=-1;
                z*=-1;
                pq.push(x);
                pq.push(y);
                pq.push(z);
            }
        }
        else if(ins=='R')
        {
            scanf("%lld", &x);
            x*=-1;
            pq.push(x);
        }
        else
        {
            if(!pq.empty())
                pq.pop();
        }
    }
    if(pq.empty())
    {
        printf("NO HUBO GANADOR\n");
        return 0;
    }
    else
    {
        while(!pq.empty())
            x=pq.top(), pq.pop();
        printf("EL PUNTAJE MAS ALTO FUE %lld", x*-1);
        return 0;
    }
    return 0;
}
</pre>

# Tarea

* List Game

* Adivina

* Lavando platos 

[1]: https://omegaup.com/arena/problem/Buscando-una-estrella#problems
