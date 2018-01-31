Las pilas son estructuras din�micas de datos que siguen el principio del Last In First Out (LIFO), es decir, el �ltimo elemento que se insertar� en una pila es el primero que se eliminar� de ella. Por ejemplo, una pila de bandejas en una mesa: la bandeja en la parte superior de la pila es el primer elemento que se mover� si necesita una bandeja espec�fica de esa pila.

# Insertar y eliminar elementos

Las pilas tienen restricciones en la inserci�n y eliminaci�n de elementos. Los elementos se pueden insertar o eliminar solo desde un extremo de la pila, es decir, desde la parte superior. El elemento en la parte superior se llama $top()$. Las operaciones de inserci�n y eliminaci�n de elementos se denominan $push()$ y $pop()$, respectivamente.

Cuando se elimina el elemento superior de una pila, si la pila permanece no vac�a, entonces el elemento justo debajo del elemento superior anterior se convierte en el nuevo elemento superior de la pila, es decir, el elemento $top()$. Por ejemplo, en la pila de bandejas, si toma la bandeja en la parte superior y no la reemplaza, la segunda bandeja se convierte autom�ticamente en el elemento superior ($top()$) de esa pila.

Una pila se puede visualizar de la siguiente manera:

![Pila](pila.png)

# Operaciones

Sea $pila[]$ un arreglo (de tama�o igual a la cantidad m�xima de elementos que puede tener la pila en cualquier momento de la ejecuci�n) que representa la pila y sea $tam$ la cantidad de elementos en la pila. Inicialmente el arreglo est� vac�o y $tam$ es igual a 0 (ya que no hay ning�n elemento en la pila).

* $isempty()$: Checa si la pila est� vac�a

<pre>
bool isempty()
{
	if(tam==0)
		return true;
	return false;
}
</pre>

* $psize()$: Devuelve el tama�o de la pila.

<pre>
int psize()
{
	return tam;
}
</pre>

* $push(x)$: Inserta el elemento $x$ en la parte superior de la pila.

<pre>
void push(int x)
{
	pila[tam]=x;
	tam++;	
}
</pre>

**Nota: Esta funci�n se declara dependiendo el tipo de dato de la pila.**

* $pop( )$: Elimina el elemento que se encuentra en la parte superior de la pila, si hay alguno. 

<pre>
void pop()
{
	if(!isempty()) 
	{
		tam--;
	}
}
</pre>

* $top( )$: Devuelve el elemento que se encuentra en la parte superior de la pila.

<pre>
int top()
{
	return pila[tam-1];
}
</pre>

**Nota: Para usar esta �ltima funci�n, se debe verificar primero si hay elementos en la pila y se declara dependiendo el tipo de dato de la pila.**

#Problema de ejemplo

# [Par�ntesis][1]

Tienes una secuencia formada por par�ntesis de apertura '(' y cierre ')' y tu tarea es  verificar si esta secuencia de par�ntesis es correcta, es decir, que si existe un par�ntesis que abre, entonces debe existir otro que cierra con la correspondencia correcta. 

Es muy f�cil ver que la secuencia se puede representar como una pila de la siguiente forma: si encuentro un par�ntesis de apertura, lo inserto en la pila y si encuentro un par�ntesis de cierre, quiere decir que en la pila tiene que haber al menos un par�ntesis de apertura que es su correspondiente y quito ese par�ntesis de apertura de la pila, en caso contrario, quiere decir que la secuencia de par�ntesis es incorrecta al no tener correspondencia. Al final tengo que checar si hay elementos en la pila, ya que al haberlo, quiere decir que algunos par�ntesis de abertura no tiene su respectivo par�ntesis de cierre y la cadena ser�a incorrecta.

C�digo: 

<pre>
#include&lt;stdio.h&gt;
#include&lt;algorithm&gt;
#include&lt;string.h&gt;
char pila[1000005];
int tam;

bool isempty()
{
    if(tam==0)
        return true;
    return false;
}

int psize()
{
    return tam;
}

void push(char x)
{
    pila[tam]=x;
    tam++;
}

void pop()
{
    if(!isempty())
    {
        tam--;
    }
}

char top()
{
    return pila[tam-1];
}

char sec[1000006];
int N;
int main()
{
    gets(sec);
    N=strlen(sec);
    for(int i=0; i&lt;N; i++)
    {
        if(sec[i]=='(')
            push(sec[i]);
        else
        {
            if(!isempty())
                pop();
            else
            {
                printf("NO");
                return 0;
            }
        }
    }
    if(!isempty())
        printf("NO");
    else
        printf("SI");
    return 0;
}
</pre>

# Tarea

* A jugar 2048

* Atestamiento del callej�n

* Notaci�n posfija

* Artista

* Guardias

* C�digo QROVI

* Globos

* Destruyendo edificios 

[1]: https://omegaup.com/arena/problem/COMI-Parentesis#problems

