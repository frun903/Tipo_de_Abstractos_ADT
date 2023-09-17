## Definición y Estructura 
Las listas enlazadas o ligadas son estructuras compuestas por 2 partes, una mantiene a la información (un valor de un tipo de dato) y la otra apunta (por medio de un puntero) al siguiente nodo de la lista enlazada. Un nodo sera la composición de las dos partes antes mencionadas.  

![[Pasted image 20230814071211.png]]

A diferencia del arreglo que tienen posiciones fijas las listas enlazadas tienen _el dinamismo brindado por los punteros_ por lo tanto c/d elemento de la lista no esta uno al lado del otro en memoria lo que implica que en memoria todos mis nodos están desparramados. 

A grandes rasgos las listas enlazadas admite memoria dinámica. es flexible y permite guardar solo los elementos necesarios. Sin embargo es lento buscar elementos en el.  


### Ventajas para su Aplicación 
- Dinámica no tiene un tamaño fijo, por lo tanto puedo tener todos los elementos que quiera incluso después de haber declarado la lista.
- Puedo agregar elementos entre nodos sin tener que eliminar todos los que siguen.
![[Pasted image 20230814072105.png]]
Por medios de mis punteros creo un método que haga señalar al nuevo nodo y que el nuevo apunte al siguiente.

- Ahorro de memoria: como sus nodos se van colocando diatónicamente, no tengo memoria fija _por lo tanto solo ocupo lo que necesito._ 

### Desventajas para su Aplicación
Como en una lista no tengo posiciones fijas en las búsquedas de elementos deberé revisar c/d nodo hasta encontrar la búsqueda. Recorrer los nodos de una lista para encontrar algún elemento es mas laborioso.  


## Mecánicas y Funciones de las Listas Enlazadas
[[Estructura de una Lista Simplemente Enlazada]] 

Las acciones que puedo realizar sobre una lista ligada son:

| Funciones | Lo que hace XD |
|------------|-----------------|
| P = Getnode() | Crea nodo vacio|
| GuardarInfo(x) | Guarda informacion en el sector de datos del nodo|
|GuardaPuntero(p) | Guarda la posicion del proximo nodo |
| x= verInfo() | muestra informacion de datos del nodo |
|p_2= VerPuntero() | Muestra la posicion donde apunta el nodo |

### Insertar Nodos en una Lista

Por medio de la función _GetNode( )_ estas inserciones pueden ser:

- _Insertar al Principio de la lista_: para ser al principio busco la posicion de memoria del primero lo coloco ahi. Si ya existe uno inicial lo pongo ahi y señalo al original.

- _Insertar al Final de la lista:_ Recorro toda la lista hasta el ultimo elemento (que sera el que señala al null) y hare que este sañale el nuevo nodo.

- _Insertar entre 2 nodos de la lista_


### Eliminar Nodo

Por medio de la función _EliminarNodo( ) o DeleteNode( )_ en esta eliminaciones pueden ser:

- _Elminar al Final de la Lista_: Esta operación ahora es muy simple, ya que el último nodo tiene acceso a su predecesor. Busco el elemento que apunte a null y retrocedo al nodo anterior desde este penúltimo hago que su puntero mire a null. **Este retroceso puede ser con recursividad**  

- _Eliminar entre dos nodos_: 

- _Eliminar al Principio_:

Para eliminar un elemento primero cambio la dirección de los punteros. Y luego elimino el nodo a eliminar. 

**Ojo!** No olvidemos que intentar borrar un elemento de una lista vacia pudiera ocasionar que nuestro programa fracasara, asi que habrá que verificar siempre que la lista no esté vacía antes de borrar. 

Una **lista vacía** que no contiene nodos se representa con el nodo “frente” en null.

## Tipo de Listas

#### Lista Simplemente Enlazada
Cada nodo contiene un único enlace que conecta al nodo siguiente o sucesor.

![[Pasted image 20230814080756.png]]

Se recorre solo hacia adelante.

#### Lista Doblemente Enlazada
Cada nodo contiene 2 punteros es complejo poner nodos nuevos entre medio pero es útil para ir y venir entre los nodos.

![[Pasted image 20230814081438.png]]

Este nodo estaría compuesto por 3 partes "head-cabeza" que señala al anterior, contenido y "tail-cola" que señala al próximo. 

![[Pasted image 20230814081647.png]]


[[Estructura de una Lista doblemente Enlazada]] 

#### Lista Circular Simplemente Enlazada
Similar a la lista simplemente enlazada sólo que el último nodo enlaza con el primero.

![[Pasted image 20230814081151.png]]

En esta lista c/d nodo tiene un sucesor.


#### Lista Circular Doblemente Enlazada 


