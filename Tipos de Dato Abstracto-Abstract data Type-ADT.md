## Introducción a las estructuras de Datos

Recordemos que la información se guarda en bits, 1 bit puede tener 2 posiciones 0-1, 8 bits son equivalentes a 1 byte. Por me dio de una cadena de bits o bytes por _convención_ puedo pasarlos a decimal o octal o hexadecimal.  Lo importante en este apartado es la palabra _convención donde un grupo de personas cuando la computación fue creciendo se pusieron de acuerdo en reglas para fomentar la retro compatibilidad entre tecnologías_.  

Otras convenciones fueron las de _complemento a uno_ donde el primer dígito representaba si el numero era positivo o negativo, en el caso de ser negativo se invierten todos los bits:

 38=001100110
-38=11011001

Con n bits se puede representar desde (-2-1)^n-1 hasta (2-1)^n-1. Con este metodo me quedarían 2 ceros un +0 y un -0.

Otra convención es el _complemento a dos_ el cual consiste en sumarle 1 a la reperesentacion del complemento a 1 del numero negativo. 

-38=11011010

La idea era ir mejorando estas convenciones con el fin **de no desperdiciar combinaciones de bits y espacios de memoria** recordemos que estos dos conceptos están íntimamente relacionados. 

Otra convención es el código ASCII a partir del cual empezamos hacer caracteres por lo tanto  con mi cadena de 8 bits (o un byte) puedo representar un carácter y se pueden representar hasta 256 caracteres diferentes. En esta cadenas puedo hacer desde letras, números y símbolos _estos serian los distintos Tipos de Datos._ 

##### Hardware o Software
La memoria de una computadora es simplemente un grupo de bits(0 o 1). Todas las computadoras tienen un conjunto de tipo de datos nativos, o sea que se construyo para manejar estos tipos de datos.  Alojar en una dirección de memoria la suma de las pautas de bits, alojados en otras 2 direcciones de memoria, estas son algunas de las funciones que están previstas en una computadora para poder manipular o hacer operaciones con estos bits.


## Concepto de implantación
Primero debemos separar el concepto de TIPO DE DATOS que se representa en una computadora, por el de TIPO DE DATO ABSTRACTO. Pero como represento un ADT. en la **Implantación de Hardware** se diseña y construye el circuito necesario para ejecutar la operación requerida. Por otro lado **Implantación de Software** se escribe un programa que consta de instrucciones existentes en el hardware para interpretar en la forma deseada las cadenas de caracteres y ejecutar las operaciones requeridas.


# Definición de ADT-Abstract Data Type

Los ADT son modelos (similares a las clases de POO), consideradas abstractas porque no existen en la vida real o físicamente pero tienen el comportamiento que yo quiera o necesite. Estas por ser muy utilizadas pueden ser creadas en el hardware y no solo estar en el software. 

_En un Abstract Data Type deberé definir de que se trata es decir la estructura de la misma y luego sus mecánicas o reglas de funcionamiento_. 

En palabras de vulcano "Una herramienta útil para especificar las propiedades lógicas de los tipos de datos, es el tipo de dato abstracto ADT, el cual es, una colección de valores y un conjunto de operaciones con esos valores.El término ADT se refiere al concepto matemático que define el tipo de datos"

Cuando use los ADT en mi código diré que los estoy _implantando_ en mi código. Un ejemplo seria que creara en C/C++ los números racionales o los fasores como estructura y luego definiera sus reglas. 

Los arreglos serian un tipo de dato abstracto lineal. Entre otros están las:
- [[Listas Enlazadas]]
- [[Pilas o Stock]]
- [[Colas o Queue]]
- [[Arboles]] y [[Recursividad]]


Estos últimos son  **No lineales**: No toda la información está al mismo nivel o almacenada con un orden especifico. Por ejemplo, en la estructura de árbol tenemos un tronco principal con diferentes ramificaciones que surgen a partir de este o, también, la estructura de grafos donde tenemos puntos de información dispersos pero interconectados entre sí.


### Arreglos como ADT
Los arreglos sun un ADT **lineales** esto quiere decir que la información se guarda de forma secuencial en memoria y si bien podemos personalizar el orden en que se guardan. Por ejemplo, de acuerdo a las fecha, siempre seran secuencial mente es decir uno después del otro.  

#### Arreglo unidimensional:
```C
int b[100];
```

Reserva 100 localidades _sucesivas de memoria_, cada una lo bastante grande para contener un solo entero.
En memoria la dirección de la primer localidad de mi arreglo b se _denomina dirección base_. Suponiendo que el tamaño de cada elemento individual del arreglo es x, para acceder al elemento número 8 del arreglo debemos dirigirnos a la posición de memoria _base + 8 * x_ esto me indica que en memoria un arreglo c/d elemento esta uno detrás del otro de manera continua. 

#### Arreglo Bidimensional :

```C
int b[3][5];
```
A esto lo llamamos arreglo bidimensional, y así lo imaginamos aunque el computador lo trate como un arreglo unidimensional de manera interna.El método para representar en memoria este arreglo es el denominado RENGLON-MAYOR. _De esta manera el primer renglón del arreglo ocupa el primer conjunto de localidades de memoria._ 

![[Pasted image 20230814064428.png]]


Suponiendo que deseamos alcanzar la dirección de memoria del elemento b |i1||i2| debemos calcularlo mediante base( b ) + ( i1 * r2 + i2 ) * x

![[Pasted image 20230814064623.png]]




