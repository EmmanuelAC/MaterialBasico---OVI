# Introducci�n

El algoritmo de b�squeda en amplitud es un m�todo para visitar todos los elementos de un espacio de b�squeda, exactamente una vez y en un orden tal que, el primer elemento visitado es la ra�z, luego se visitan todos los elementos a un "paso" de la ra�z, luego todos los elementos a "dos" pasos de la ra�z, etc.


# Problema de ejemplo y explicaci�n del algoritmo

Tienes una calculadora de **4** d�gitos decimales que s�lo puede realizar **2** operaciones: multiplicar por **A** y dividir entre **B**. Si el resultado de multiplicar un n�mero por **A** es un n�mero de m�s de **4** d�gitos la calculadora da como resultado **1**. Si el resultado de dividir entre **B** no es un n�mero entero, entonces la calculadora trunca el resultado entregando �nicamente la parte entera. Por ejemplo, si A=2A=2 y B=3B=3 entonces 20�A=4020�A=40 y 20/B=620/B=6 mientras que 6,000�A=16,000�A=1 y 6,000/B=2,0006,000/B=2,000. La calculadora siempre comienza con el n�mero 11 y almacena el �ltimo resultado obtenido para utilizarlo en la siguiente operaci�n. Escribe un programa que dados AA y BB encuentre el n�mero m�nimo de pasos que se tienen que realizar con la calculadora para obtener un n�mero NN comenzando en el 11 y utilizando �nicamente las dos operaciones v�lidas.

# Algoritmo
