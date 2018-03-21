# Concepto de vector 

Un vector es la estructura de datos m�s b�sica: un contenedor que almacena $n$ elementos del mismo tipo en $n$ posiciones consecutivas de memoria. Si el vector se llama v, los elementos se denominan v&#91;0&#93;, v&#91;1&#93;, ... , v&#91;n-1&#93;. Para que tu programa use vectores, es necesario a�adir #include &lt;vector&gt; y using namespace std; (este �ltimo para no tener que poner $stl::$ cada vez que usemos los vectores) al principio de tu c�digo.

Todos los elementos de un vector son del mismo tipo, y �ste se debe especificar en el momento de crearlo: $vector < T > N$ es un vector cuyos elementos son de tipo $T$ y su nombre es $N$. El tama�o del vector (es decir, el n�mero de elementos de tipo $T$ que contiene) tambi�n se puede especificar en el momento de su creaci�n; de otro modo, el vector empieza vac�o. Por ejemplo:

<pre>
vector &lt; int &gt; v(5); // vector de 5 enteros
vector &lt; bool &gt; w; // vector de booleanos, vac�o
vector &lt; int &gt; d(4, 100);  // vector con 4 enteros, todos iguales a 100
vector &lt; int &gt; e(d); // copia del vector d
</pre>

A diferencia de los arreglos, los vectores pueden cambiar de tama�o durante la ejecuci�n.

# Operaciones
 
Al tener el vector v declarado, las operaciones m�s usadas son:

<center>
<table>
  <thead>
    <tr>
      <th width=300>Funci�n</th>
      <th>Descripci�n</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>v[i]</td>
      <td>Acceso por �ndice, tambi�n puede asignarse.</td>
    </tr>
    <tr>
      <td>v&#46;front()</td>
      <td>Devuelve el primer valor del vector.</td>
    </tr>
    <tr>
      <td>v&#46;back()</td>
      <td>Devuelve el �ltimo valor del vector.</td>
    </tr>
      <td>v&#46;push&#95;back(x)</td>
      <td>A�ade el elemento x al final del vector.</td>
    </tr>
    <tr>
      <td>v&#46;pop&#95;back()</td>
      <td>Borra el �ltimo elemento del vector.</td>
    </tr>
    <tr>
      <td>v&#46;size()</td>
      <td>Devuelve el tama�o del vector.</td>
    </tr>
    <tr>
      <td>v&#46;resize(n, x)</td>
      <td>Cambia el tama�o del vector a n, rellenando con un valor x. Es lineal respecto al n�mero de elementos borrados e insertados.</td>
    </tr>
    <tr>
      <td>v&#46;empty()</td>
      <td>Devuelve true si el vector est� vac�o.</td>
    </tr>
   <tr>
      <td>v&#46;clear()</td>
      <td>Vac�a el vector. Es lineal respecto a la cantidad de elementos a eliminar.</td>
    </tr>
     <tr>
      <td>vector &lt; T &gt;  :: iterator N</td>
      <td>Declaraci�n de un iterador con nombre N para un vector con datos de tipo T.</td>
    </tr>
    <tr>
      <td>v.begin()</td>
      <td>Iterador que referencia al primer elemento del vector, es decir, a v[0].</td>
    </tr>
    <tr>
      <td>v.end()</td>
      <td>Iterador que referencia al lugar de memoria despu�s del �ltimo elemento del vector. No apunta a ning�n elemento del vector.</td>
    </tr>
  </tbody>
</table>
</center>

Al a�adir #include&lt;algorithm&gt;, la operaciones mayormente usadas son:

<center>
<table>
  <thead>
    <tr>
      <th width=350>Funci�n</th>
      <th>Descripci�n</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>fill(iterador inicial, interador final, valor)</td>
      <td>Asigna valor a los elementos desde el iterador inicial hasta antes del iterador final. Es lineal respecto a la cantidad de elementos a modificar.</td>
    </tr>
    <tr>
      <td>reverse(iterador inicial, interador final)</td>
      <td>Invierte el orden de los elementos desde el iterador inicial hasta antes del iterador final. Si n es la cantidad de elementos a modificar, dura n/2 operaciones en realizarse la funci�n.</td>
    </tr>
    <tr>
      <td>sort(iterador inicial, iterador final)</td>
      <td>Coloca en orden ascendente los elementos desde el iterador inicial hasta antes del iterador final. Si n es la cantidad de elementos a ordenar, la funci�n dura nlog2(n) en ejecutarse.</td>
    </tr>
    <tr>
      <td>binary_search(iterador inicial, iterador final, valor)</td>
      <td>Devuelve true si existe valor desde el iterador inicial hasta antes del iterador final. Para usar esta funci�n correctamente, la parte del vector donde se buscar� debe de estar ordenada ascendentemente. Si n es la cantidad de elementos en donde se buscar�, la funci�n dura log2(n) en ejecutarse.</td>
    </tr>
    <tr>
      <td>lower_bound(iterador inicial, iterador final, valor)</td>
      <td>Devuelve el iterador del primer elemento mayor o igual a valor. Para usar esta funci�n correctamente, la parte del vector donde se buscar� debe de estar ordenada ascendentemente. Si n es la cantidad de elementos en donde se buscar�, la funci�n dura log2(n) en ejecutarse. Si el elemento no existe, devuelve el iterador final.</td>
    </tr>
    <tr>
      <td>upper_bound(iterador inicial, iterador final, valor)</td>
      <td>Devuelve el iterador del primer elemento mayor a valor. Para usar esta funci�n correctamente, la parte del vector donde se buscar� debe de estar ordenada ascendentemente. Si n es la cantidad de elementos en donde se buscar�, la funci�n dura log2(n) en ejecutarse. Si el elemento no existe, devuelve el iterador final.</td>
    </tr>
  </tbody>
</table>
</center>

Observemos que como el vector guarda en posiciones consecutivas de memoria, entonces v.begin()+x es el iterador del elemento v[x] y que si tenemos un iterador n, entonces su posici�n en el vector es n-v.begin().

Para recorrer un vector v que almacena datos de tipo T con iteradores se usa lo siguiente:

<pre>
for (vector&lt;T&gt;::iterator it = v.begin(); it!=v.end(); ++it)
{
        //operaciones a realizar durante el recorrido
}
</pre>

Pero con vectores mayormente no se usan iteradores para recorrer o realizar operaciones en ella, ya que esta estructura de datos nos permite acceder f�cilmente a cada elemento que se encuentra en ella y guarda en posiciones consecutivas de la memoria:

<pre>
for (int i=0; i&lt;v.size(); i++)
{
        //operaciones a realizar durante el recorrido
}
</pre>

Tambi�n puedes comparar los contenidos de dos vectores elemento por elemento utilizando los operadores ==, !=, &lt;, &lt;=, &gt; y &gt;=, siempre y cuando el tipo de dato T sea comparable, (casi todos los datos en C++ son comparables, al menos que sea un struct definido por nosotros mismos sin un operador de comparaci�n). Dos vectores son iguales si ambos tienen la misma cantidad de elementos y los elementos son correspondientemente iguales. Dos vectores se comparan por el orden lexicogr�fico de sus elementos. La comparaci�n es lineal respecto a la cantidad de elementos de los vectores (primero checa si tienen la misma cantidad de elementos y despu�s realiza comparaci�n elemento por elemento). Incluso puedes igualar un vector con otro usando el operador =, que tambi�n es lineal respecto a la cantidad de elementos.

Para consultar m�s funciones de la STL, consulta las referencias oficiales de la olimpiada:

* http://www.cplusplus.com/reference/

* http://en.cppreference.com/w/

#Problema de ejemplo

# [ULAM ordenado][1]

Podemos simular la secuencia, aplicando las reglas de la conjetura de ULAM y guardando los valores generados en un vector y al final los ordenamos con $sort()$.

* C�digo:

<pre>
#include&lt;stdio.h&gt;
#include&lt;vector&gt;
#include&lt;algorithm&gt;
using namespace std;
vector &lt; int &gt; ULAM;
int N;
int main()
{
    scanf("%d",&N);
    while(N!=1)
    {
        ULAM.push_back(N);
        if(N%2==0)
            N=N/2;
        else
            N=3*N+1;
    }
    ULAM.push_back(1);
    sort(ULAM.begin(), ULAM.end());
    for(int i=0; i&lt;ULAM.size(); i++)
        printf("%d ", ULAM[i]);
    return 0;
}
</pre>

# Tarea

* Escribiendo canciones

* Tomando asiento

[1]: https://omegaup.com/arena/problem/ULAM-ordenado#problems
