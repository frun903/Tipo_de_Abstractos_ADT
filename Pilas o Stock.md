Una pila es una colección ordenada de elementos en la que pueden _insertarse y suprimirse elementos por un extremo llamado TOPE._ Es como si se apilaran cosas y cuando saco debo sacar la ultima en entrar, esto se lo conoce como **LIFO** Last in first out significa Ultimo entrar primero en salir.
![[Pilas.excalidraw]]

En este tipo de estructurara de datos cuento con una serie de desventajas solo puedo ver el ultimo elemento ingresado (solo puedo ver el tope y no los que están debajo de el), esto conlleva que no pueda sacar o colocar elementos del medio de la pila, ademas tampoco puedo recorrerla como si fuera una lista (si quisiera hacerlo deberé sacar todos los elementos de la pila).

A pesar de sus limitaciones es muy útil y se utiliza mucho. Por ejemplo si yo buscar una estructura de datos que me devolviera los elementos en el orden inverso al que los ingrese utilizaría una pila. 


### Funciones
Las únicas operaciones que pueden realizarse con pilas son las siguientes:

- _CreaPila( ):_ Crea una Pila vacía.
- _PilaVacia( )_: Responde si la pila se encuentra vacía. 
- _Poner( X ):_ Inserta un elemento X en la pila.
- _Sacar( ):_ Antes de saca un elemento de la pila siempre hay que preguntar si la pila esta vacía o no. Si no pregunto esto podría dar error. Una vez consultada la funcion Sacar saca un elemento de la pila. 
- _ValorTope( ):_  Devuelve el valor del tope de la pila, sin modificar la pila. En si es una composición entre las funciones Sacar( )......Reviso que "elemento" es....... Poner(elemento) De esa forma la pila quedara sin cambios.

### Las Pilas en la vida diaria
Las Pilas o Stock son muy importante ya que la memoria de las computadoras funciona como una pila; todo el análisis y verificación se hace con una pila.
![[Pilas_2.excalidraw]]
- ( 2 ) C/d vez que hago cualquier procesos en mi Pc se agrega a una Pila (nueva) y y una ves los cierro hace returns y sale de la pila (lineas verdes). Cualquier elemento con software se vale de una pila. 
- ( 1 ) Al prender mi Pc mi pila se va cargando con verficiaciones bios-->ok, ect, todas esta verificaciones van a una pila que una vez apague mi sistema se ira descargando y verificando nuevamente estos procesos. 



## Construcción de una Pila (Código)

Todos los datos de la pila van a salir inversamente de como entraron. Como diseño la pila es mas rígida que una lista por lo tanto no puedo sacar los elementos del centro sin sacar todos los anteriores antes. 


- _Constructor_ necesitamos que el tope marque al null.
```cpp

```

- _Push_ : Poner elementos a mi pila. Hacemos que el nuevo dato sea el tope y su puntero apunte al anterior. No es importante ver si esta vacía porque siempre voy a ingresar un elemento (sin importar si es vacía o no).

```cpp
template <class T> void Pila<T>::push(T dato) {  
    Nodo<T> *nuevo= new Nodo<T>; 
    //guardo dato 
    nuevo->setDato(dato);  
    //Que apunte al tope viejo
    nuevo->setSiguiente(tope); 
    //Y ahora el tope es el nuevo 
    tope=nuevo;  
}```

Abajo de tope en su puntero ya quedo el viejo elemento.

- _Pop_:  Sacamos los elementos de la pila. Primero debo saber si o si si esta vacía o no.  Luego guardo el dato del tope, una vez guardado pongo el tope el elemento siguiente de la pila. 

```cpp
template <class T> T Pila<T>::pop() {  
    if (esVacia()){  
        throw 404;  
    }  
//Guardo en un aux el tope
    Nodo<T>*aux=tope;  

//en una var dato guardo el elemento de auxiliar osea mi ex tope
    T dato=aux->GetDato();  

//El tope nuevo es elemento siguiente
    tope=tope->getSiguiente();  

//Liberamos el dato de aux que es el que usamos para recorrer la pila
    delete aux;  

//Retornamos el dato
    return dato;  
    }
```

- _esVacia_ Solo debo ver si tope es igual nullptr
```cpp
template <class T> bool Pila<T>::esVacia() {  
    return tope== nullptr;  
  
    /*
    la condicion hace el retorno true o false. es lo mismo que esto:
    
    if (tope== nullptr){  
        return true;    }else{        return false;    
        }
        
        */
        }
```

- _Destructor_: Deberemos hacer un ciclo While para que haga mucho pop hasta que mi pila este vacía

```cpp
template <class T> Pila<T>::~Pila() {  
    while (!esVacia()){  
        pop();  
    }  
  
    //Para terminar d eleiminar la pila debemos elimiar el tope  
    delete tope; }
```

