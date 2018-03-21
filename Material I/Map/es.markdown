# Concepto de map

Un diccionario es una estructura donde podemos guardar datos ordenados seg�n una clave, de tal modo que resulte muy eficiente buscar el dato conociendo su clave correspondiente. Por ejemplo, en un diccionario real, la clave es una palabra, mientras que el dato guardado es la definici�n de la misma. La STL ofrece diversas estructuras de datos que pueden ejercer funciones parecidas a las de un diccionario. La m�s importante es el map &lt; K , T &gt;, donde K es el tipo de la clave y T es el tipo de los datos. Se requiere, adem�s, que los elementos de tipo K sean ordenables.

La principal caracter�stica que se espera de un diccionario es que las operaciones de insertar un nuevo dato con su clave, buscar si una clave existe, y recuperar el dato asociado, sean veloces. En concreto, se espera que tarden tiempo proporcional al logaritmo base 2 del n�mero de elementos almacenados en el diccionario. Esto se corresponde, intuitivamente, con el tiempo que tardar�amos a encontrar una palabra en un diccionario real siguiendo el algoritmo de b�squeda binario: abrimos el diccionario por la mitad, vemos en qu� mitad del diccionario est� la palabra buscada, volvemos a abrir por la mitad de la parte donde est� la palabra, etc. Como a cada paso descartamos la mitad del trozo de diccionario que nos interesaba, tardamos tantos pasos como veces podamos dividir por la mitad el n�mero de palabras del diccionario, es decir, el logaritmo base 2 de este n�mero. La implementaci�n usual de los tipos map  es usando �rboles binarios de b�squeda.

# Uso de stl::map

Para que tu programa use maps, es necesario a�adir #include&lt;map&gt; y using namespace std; (este �ltimo para no tener que poner $stl::$ cada vez que usemos los maps) al principio de tu c�digo. Todos los elementos de un map son del mismo tipo.

En un map, podemos insertar y recuperar datos de modo muy parecido a como usar�amos un vector, escribiendo m[c]=d; insertamos un dato d con clave c (o modificamos el dato antiguo, si la clave c ya estuviera en el diccionario), y escribiendo m[c] recuperamos el dato con clave c. Por ejemplo, un map &lt; int , T &gt; funciona de un modo parecido a un vector &lt; T &gt;, con la ventaja de que no necesitamos preocuparnos de su tama�o, o de si accededemos fuera de rango, porque cualquier entero puede actuar como clave. 

Escribir m[c] siempre sirve para recuperar un dato con clave c. �Qu� ocurre cuando no hay ning�n dato con clave c? En otros lenguajes de programaci�n, esto provocar�a un error en tiempo de ejecuci�n. La STL, sin embargo, hace lo siguiente: toma las medidas necesarias para que este intento de recuperaci�n no provoque ning�n error. Para ello, el map m inserta un dato con clave c y dato vac�o (0 si el dato es de tipo int, double o bool, "" si el dato es de tipo string, etc.), y retorna ese dato vac�o. Por lo tanto: nunca hay que escribir m[c] a menos que estemos seguros de que exista la clave c, o que queramos insertar en el map la clave no existente.

Para saber si una clave est� o no en el map sin insertarla debemos usar el m�todo **find**: este m�todo nos devuelve un iterador que nos indica si ha encontrado o no la clave, y qu� dato asociado tiene la misma. M�s adelante veremos los iteradores de un map; por ahora, lo �nico que necesitamos saber es que para saber si la clave existe o no existe en el map m s�lo necesitamos hacer m.find(c) y comparar el valor que retorna con m.end(): si son iguales, es que la clave no existe; de otro modo, sabemos que escribir m[c] es seguro, y que devolver� el dato asociado. Haciendo lo descrito anteriormente estar�amos realizando dos b�squedas, una primera m.find(c) para saber si el dato existe, y una segunda m[c] para encontrar el dato asociado. En realidad, el iterador que devuelve el find ya contiene el dato asociado, sin que necesitemos buscarlo de nuevo en el diccionario: habr�a que guardar la respuesta en una variable de tipo iterador, compararlo con m.end(), y si son distintos, usar este mismo iterador para acceder al dato. Para eliminar el elemento con clave c de un map basta con hacer **m.erase(c)**. El erase tambi�n funciona si recibe un iterador (como los devueltos por el find) en vez de una clave. Al igual que con otras estructuras de la STL, tambi�n podemos hacer **m.size()** para conocer el n�mero de elementos almacenados, **m.empty()** para saber si est� o no est� vac�o, y **m.clear()** para borrar todos los elementos del map.

Una de las operaciones m�s usuales de un map es la de recorrer todos los elementos que contiene. Internamente, el map guarda todos los elementos que hemos insertado ordenados seg�n su clave: podemos recorrer los datos guardados siguiendo este orden, usando iteradores. Un iterador es, en cierto modo, la posici�n que ocupa un par clave-dato dentro del diccionario. A trav�s de un iterador podemos acceder no s�lo a la clave y al dato, sino tambi�n al elemento siguiente y anterior del diccionario. De este modo podemos recorrerlo, elemento a elemento, de un modo id�ntico al que ya vimos con los vectores.

Si m es un map &lt; K ,T &gt; y it es un iterador que apunta a un elemento del diccionario, se tiene que it->first es la clave del elemento, de tipo const K, y que it->second es el dato correspondiente, de tipo T. Dado un iterador it, las operaciones ++it; y --it; hacen que el iterador apunte al siguiente o anterior elemento del diccionario. El m�todo **m.begin()** devuelve un iterador que apunta al primer elemento del map, mientras que **m.end()** devuelve un iterador que apunta una posici�n despu�s del �ltimo elemento del diccionario. (Este era el iterador que devolv�a el m.find(c) para indicar que no hab�a encontrado la clave c.) Para recorrer un map, por lo tanto, basta con empezar con el iterador m.begin() e irlo incrementando con ++it; hasta comprobar que es igual a m.end(), momento en el que habremos acabado de recorrer por orden todos los elementos del map.

Por �ltimo, s�lo nos falta decir c�mo crear una variable de tipo iterador: el tipo de un iterador a un map<K,T> se llama **map &lt; K,T &gt;::iterator**. Con esto, ya podemos recorrer todos los elementos de un map. Por ejemplo, completamos el programa que calculaba cu�ntas veces aparec�a cada palabra por la entrada, haciendo que escriba el n�mero de apariciones ordenadamente (seg�n el orden lexicogr�fico de las palabras que aparecen, que hacen de claves en este ejemplo).


Con lo que sabemos podemos recorrer los elementos del map uno por uno, empezando por el principio o por el final, hasta encontar el positivo m�s peque�o; esto, sin embargo, sigue siendo un m�todo lento. Lo que necesitamos es buscar una clave (por ejemplo, el n�mero 0) y, caso de no existir, obtener un iterador a un elemento cercano a la clave buscada, de modo que con unos pocos incrementos o decrementos adicionales podamos encontrar el iterador al elemento buscado. Un m�todo que hace lo que queremos es el **m.lower_bound(c)** que, dada una clave c, retorna un iterador a la entrada de clave c si esta existe (al igual que el find), pero que, si no existe ninguna entrada con clave c, devuelve un iterador a la primera entrada con clave mayor que la clave c dada , o m.end() si una tal entrada no existe (a comparaci�n de **m.upper_bound(c)** que devuelve un iterador a la primera entrada con clave mayor que la clave c dada o m.end() si una tal entrada no existe.

#Problema de ejemplo

# [Tecleando n�meros][1]

Podemos ir contando las repeticiones con un map (la clave es el n�mero y el dato son las repeticiones).

* C�digo:

<pre>
#include&lt;stdio.h&gt;
#include&lt;map&gt;
using namespace std;
int n;
long long a;
map&lt;long long,long long&gt; mapita;
map&lt;long long,long long&gt;:: iterator it;
char aux;
int main()
{
    scanf("%d",&n);
    for(int i=0; i&lt;n; i++)
    {
        scanf(" %c",&aux);
        scanf("%lld",&a);
        if(aux=='A')
        {
            mapita[a]++;
        }
        if(aux=='B')
        {
            it=mapita.find(a);
            if(it!=mapita.end())
                printf("%lld\n",mapita[a]);
            else
                printf("0\n");
        }
    }
    return 0;
}
</pre>

# Tarea

* Tablero multiplicador

* Triples

* Alfa buena maravilla onda dinamita escuadr�n lobo

[1]: https://omegaup.com/arena/problem/Tecleando-numeros/#problems
