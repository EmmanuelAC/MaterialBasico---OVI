# Introducci�n

El algoritmo de b�squeda en amplitud es un m�todo para visitar todos los elementos de un espacio de b�squeda, exactamente una vez y en un orden tal que, el primer elemento visitado es la ra�z, luego se visitan todos los elementos a un "paso" de la ra�z, luego todos los elementos a "dos" pasos de la ra�z, etc.

Se utiliza una cola para mantener el orden en que se visitan los elementos.

Si representamos los elementos a visitar como un �rbol, siendo el nodo 1 la ra�z, los elementos se visitar�an de la siguiente forma.

![bfs](bfs.gif)

Cada vez que un elemento est� en la cola ser� pintado de color gris, cuando se procesa se vuelve color negro, y sus hijos son agregados a la cola, por lo tanto se vuelven color gris. Esta animaci�n representa el orden como entran a la cola los elementos, para ser procesados despu�s.

![como](como.gif)

# Algoritmo

La idea principal de la b�squeda en amplitud que elementos que est�n cerca del punto inicial, se visitar�n antes que los elementos m�s lejanos al punto inicial. Para llevar el orden de los elementos a visitar se ocupa una cola, as�, los elementos que entran primero a la cola se procesan primero que los elementos que entraron despu�s.

La estructura general de una b�squeda en amplitud es

    {

       declarar cola de tipo Elemento

       declarar arreglo de elementos visitados

       declarar elementoRaiz,elementoHijo

       interstar elementoRaiz a la cola

       mientras !condici�n de parado

       {

         procesar elemento al frente de la cola
   
         insertar elementos hijos no visitados a la cola

       }

    }


# Problema de ejemplo y explicaci�n del algoritmo

Tienes una calculadora de **4** d�gitos decimales que s�lo puede realizar **2** operaciones: multiplicar por **A** y dividir entre **B**. Si el resultado de multiplicar un n�mero por **A** es un n�mero de m�s de **4** d�gitos la calculadora da como resultado **1**. Si el resultado de dividir entre **B** no es un n�mero entero, entonces la calculadora trunca el resultado entregando �nicamente la parte entera. Por ejemplo, si $A=2$ y $B=3$ entonces $20xA=40$ y $20/B=6$ mientras que $6,000�A=1$ y $6,000/B=2,000$. La calculadora siempre comienza con el n�mero $1$ y almacena el �ltimo resultado obtenido para utilizarlo en la siguiente operaci�n. Escribe un programa que dados $A$ y $B$ encuentre el n�mero m�nimo de pasos que se tienen que realizar con la calculadora para obtener un n�mero $N$ comenzando en el $1$ y utilizando �nicamente las dos operaciones v�lidas.

Para resolver este problema es muy �til una b�squeda en amplitud, porque queremos saber la m�nima cantidad de pasos para llegar a $N$ empezando desde 1, y como una b�squeda en amplitud visita primero todos los elementos a un "paso", luego los que est�n a dos "pasos", etc., entonces la primera vez que lleguemos a $N$, el n�mero de "pasos" que utilizamos ser� la respuesta.

El c�digo soluci�n podr�a quedar as�:

    {

    //Declaramos una cola, para mantener el orden de los numeros que vamos a calcular

    #include < stdio.h>

    #include< queue>

    using namespace std;

    int n,a,b;
    struct nodo

    {
        int pasos,valor;

    };

    queue< nodo>cola;

    nodo padre,hijo;
    bool v[10001];


    int main()

    {

    //leemos los datos de entrada

    scanf("%d %d %d",&a,&b,&n);

    //revisamos que no sea el caso especial n=1//
    if(n==1)
    {
        printf("%d",n);
        return 0;
    }

    //marcamos como visitado el n�mero 1, y lo 
    metemos en la cola con 0 pasos, para generar los
    dem�s n�meros iniciando por el 1

    v[1]=true;
    padre.valor=1;
    padre.pasos=0;
    cola.push(padre);

    //ahora visitamos n�meros uno por uno, guardando 
    los siguientes n�meros que se pueden visitar con 
    una operaci�n m�s, y como primero los n�meros que 
    podemos obtener con una operaci�n, luego con 2, 
    etc., el primer n�mero que obtengamos tendr� en 
    el n�mero de pasos la respuesta que buscamos

    while(!cola.empty())
    {
        padre=cola.front();
        cola.pop();
        hijo=padre;

        hijo.valor*=a;
        if(hijo.valor>9999)
            hijo.valor=1;


        if(v[hijo.valor]==false)
        {
            v[hijo.valor]=true;
            hijo.pasos++;
            cola.push(hijo);
            if(hijo.valor==n)
            {
                printf("%d",hijo.pasos);
                return 0;
            }
        }

        hijo=padre;
        hijo.valor/=b;
        
        //si no se ha visitado se marca y encola
        if(v[hijo.valor]==false)
        {
            v[hijo.valor]=true;
            hijo.pasos++;
            cola.push(hijo);
            if(hijo.valor==n)
            {
                printf("%d",hijo.pasos);
                return 0;
            }
        }

    }

    return 0;

    }


# Problemas de pr�ctica

https://omegaup.com/arena/problem/Intersecciones#problems
https://omegaup.com/arena/problem/OIEG2013SSA#problems

