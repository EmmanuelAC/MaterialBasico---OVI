# Concepto de cola e implementaci�n

Las colas son estructuras din�micas de datos que siguen el principio del First In First Out (FIFO), es decir, el primer elemento que se insertar� en una cola es el primero que se eliminar� de ella. Por ejemplo, una fila de personas esperando un autob�s: la persona que est� al comienzo de la fila es la primera en ingresar al autob�s.

**Insertar y eliminar elementos**

Las colas tienen restricciones en la inserci�n y eliminaci�n de elementos. Los elementos se pueden insertar o eliminar solo desde un extremo de la cola, es decir, la parte final. El primer elemento de la cola se llama $front()$ y el �ltimo $back()$. Las operaciones de inserci�n y eliminaci�n de elementos se denominan $push()$ y $pop()$, respectivamente.

Cuando se elimina el primer elemento de una cola, si la cola permanece no vac�a, entonces el elemento justo despu�s del elemento eliminado se convierte en el primer elemento de la cola, es decir, el elemento $front()$. Por ejemplo, en la fila del autob�s, la primera persona al ingresar al autob�s, la segunda persona se convierte autom�ticamente en la primera persona ($front()$) de la fila.

Una cola se puede visualizar de la siguiente manera:

![Cola](cola.png)

**Operaciones**

Sea $cola[]$ un arreglo (de tama�o igual a la cantidad m�xima de elementos que puede tener la cola en cualquier momento de la ejecuci�n) que representa la cola, sea $tam$ la cantidad de elementos en la cola, sea $ini$ el �ndice del primer elemento en la cola y sea $fin$ el �ndice del �ltimo elemento en la cola. Inicialmente el arreglo est� vac�o, $tam$ es igual a 0, $ini$ es igual a 0, $fin$ es igual a -1 (ya que no hay ning�n elemento en la cola).

* $isempty()$: Checa si la cola est� vac�a

<pre>
bool isempty()
{
    if(tam==0)
        return true;
    return false;
}
</pre>

* $csize()$: Devuelve el tama�o de la cola.

<pre>
int csize()
{
    return tam;
}
</pre>

* $push(x)$: Inserta el elemento $x$ al final de la cola.

<pre>
void push(int x)
{
    fin++;
    cola[fin]=x;
    tam++;	
}
</pre>

**Nota: Esta funci�n se declara dependiendo el tipo de dato de la cola.**

* $pop( )$: Elimina el elemento que se encuentra al inicio de la cola.

<pre>
void pop()
{
      ini++;
      tam--;
}
</pre>

* $cfront( )$: Devuelve el primer elemento de la cola.

<pre>
int cfront()
{
    return cola[ini];
}
</pre>

* $cback( )$: Devuelve el �ltimo elemento de la cola.

<pre>
int cback()
{
    return cola[fin];
}
</pre>

**Nota: Para usar estas �ltimas 2 funciones se debe verificar primero si hay elementos en la cola y se declara dependiendo el tipo de dato de la cola.**

# Utilizar colas con struct 

Una estructura de datos es un grupo de elementos de datos y funciones agrupadas bajo un nombre. La ventaja de implementar una cola con struct es que puedes declarar varias colas que realizan las funciones dadas en la estructura y con la implementaci�n antes vista tendr�as que realizar las funciones para cada cola que desees ocupar.

El c�digo para implementar una cola que tenga las funciones antes vistas con struct es el siguiente:

<pre>
struct stcola
{
    int tam, ini, fin;
    int cola[1000005];
    stcola() //constructor = sirve para inicializar datos de la estructura
    {
	  tam=0;
	  ini=0;
	  fin=-1;
    }
    bool isempty()
    {
	  if(tam==0)
		  return true;
	  return false;
    }
    int csize()
    {
	  return tam;
    }
    void push(int x)
    {
          fin++;
          cola[fin]=x;
          tam++;	
    }
    void pop()
    {
          ini++;
          tam--;
    }
    int cfront()
    {
          return cola[ini];
    }
    int cback()
    {
          return cola[fin];
    }  
};
</pre>

Declaraci�n (nombre_de_tipo_de_estructura nombre_del_dato):

<pre>
pcola q;
</pre>

Ejemplo de uso de la cola con struct (nombre.funci�n):

<pre>
int t=q.front() //t es igual al primer elemento de la cola "q"
q.push(4); //agrega a la cola "q" el n�mero 4
q.pop(); //quita el primer elemento de la cola "q"
</pre>


# Uso de stl::queue

La STL ofrece una estructura de datos ya implementada llamada $queue$, que trabaja como una cola y tiene las 6 funciones antes vistas:

* Para usarla es necesario hacer #include &lt;queue&gt; y using namespace std; (este �ltimo para no tener que poner $stl::$ cada vez que usemos la cola). 

* Con $queue < T > N$ declaramos una cola que almacena datos de tipo $T$ y el nombre de la cola es $N$.
 
* $push(x)$ y $pop()$ son funciones que se llaman y se usan igual en $stl::queue$.

* $cfront()$ se llama $front()$ en $stl::queue$ y se usa igual.

* $cback()$ se llama $back()$ en $stl::queue$ y se usa igual.

* $csize()$ se llama $size()$ en $stl::queue$ y se usa igual.

* $isempty()$ se llama $empty()$ en $stl::queue$ y se usa igual.

#Problema de ejemplo

# [Canguros][1]

Observe que cada acci�n representa una operaci�n de una cola:

* $N$: $push(M_{i}+1)$ (el canguro grande y sus peque�os).

* $A$: Actualizar $C$ a $C$-$front()$ (atendieron a los canguros que est�n al inicio de la fila) y realizar la operaci�n $pop()$ (y salieron de la fila).

* $C$: Imprimir $size()$ (cu�ntos canguros grandes hay en la fila).

* $R$: Imprimir $C$ (cu�nta comida queda).

* C�digo sin STL y sin struct: 

<pre>
#include&lt;stdio.h&gt;
char accion;
int C, N, m;
int cola[1000005];
int ini, fin=-1, tam;
bool isempty()
{
    if(tam==0)
        return true;
    return false;
}
int csize()
{
    return tam;
}
void push(int x)
{
    fin++;
    cola[fin]=x;
    tam++;
}
void pop()
{
    ini++;
    tam--;
}
int cfront()
{
    return cola[ini];
}
int cback()
{
    return cola[fin];
}
int main()
{
    scanf("%d %d", &C, &N);
    for(int i=0; i&lt;N; i++)
    {
        scanf(" %c", &accion);
        if(accion=='N')
        {
            scanf("%d", &m);
            push(m+1);
        }
        else if(accion=='C')
            printf("%d\n", csize());
        else if(accion=='R')
            printf("%d\n", C);
        else if(accion=='A')
        {
            C-=cfront();
            pop();
        }
    }
    return 0;
}
</pre>

* C�digo con struct:

<pre>
#include&lt;stdio.h&gt;
char accion;
int C, N, m;
struct stcola
{
    int tam, ini, fin;
    int cola[1000005];
    stcola() 
    {
        tam=0;
        ini=0;
        fin=-1;
    }
    bool isempty()
    {
        if(tam==0)
            return true;
        return false;
    }
    int csize()
    {
        return tam;
    }
    void push(int x)
    {
        fin++;
        cola[fin]=x;
        tam++;
    }
    void pop()
    {
        ini++;
        tam--;
    }
    int cfront()
    {
        return cola[ini];
    }
    int cback()
    {
        return cola[fin];
    }
};
stcola q;
int main()
{
    scanf("%d %d", &C, &N);
    for(int i=0; i&lt;N; i++)
    {
        scanf(" %c", &accion);
	if(accion=='N')
        {
            scanf("%d", &m);
            q.push(m+1);
        }
        else if(accion=='C')
            printf("%d\n", q.csize());
        else if(accion=='R')
            printf("%d\n", C);
        else if(accion=='A')
        {
            C-=q.cfront();
            q.pop();
        }
    }
    return 0;
}
</pre>

* C�digo con STL:

<pre>
#include&lt;stdio.h&gt;
#include&lt;queue&gt;
using namespace std;
using namespace std;
char accion;
int C, N, m;
queue < int > q;
int main()
{
    scanf("%d %d", &C, &N);
    for(int i=0; i&lt;N; i++)
    {
        scanf(" %c", &accion);
        if(accion=='N')
        {
            scanf("%d", &m);
            q.push(m+1);
        }
        else if(accion=='C')
            printf("%d\n", q.size());
        else if(accion=='R')
            printf("%d\n", C);
        else if(accion=='A')
        {
            C-=q.front();
            q.pop();
        }
    }
    return 0;
}
</pre>

# Tarea

* L-OMI2010-Espias

* iOI 2009 Garage

[1]: https://omegaup.com/arena/problem/Canguros#problems