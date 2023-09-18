Una COLA es una colección ordenada de elementos de la que se pueden borrar elementos en un extremo (FRENTE de la cola) o insertarlos en el otro (FINAL de la cola). Este _abstract data type_ utiliza la propiedad **FIFO first in first aut primero entrar primero en salir**. Siempre sale primero el que entro. Sus funciones son similares a las de una pila pero el funcionamiento es distinto. 

### Operaciones a Realizarse en una Cola

| Operación   | Descripción  |
|--------|----------|
|CrearCola() |Crea una Cola Vacia|
| ColaVacia() | Revisa si la cola se encuentra vacia  |
| Poner( x )    | Insertar un elemento x en la Cola     |
| x=sacar | Saca un elemento de la cola y lo almacena en x| 




![[Filas.excalidraw]]

El primer dato que entro esta en el _tope_ y es el primero que va a salir. Por otro lado el ultimo elemento _o fondo_ apunta al null. Es como que el Tope apunta a los otros y elementos. Deberé conocer como tanto el tope como el nodo. 

## Estructura (Código)

 Deberé conocer como tanto el tope como el nodo, por eso deberé declararlos y inicializarlos en el constructor. 
 ```cpp
private:  
Nodo<T> *fondo, *tope; //fin inicio

//Constrctor
template <class T> Cola<T>::Cola() {  
    tope= nullptr;  
    fondo= nullptr;  
}
```

Para esVacio solo debo ver si inicio o tope es igual nullptr. Yo podría elegir tanto el fondo o el inicio ya que el análisis es el mismo.

Para _encolar_ pongo un nodo nuevo. Luego recordemos que la cola el nodo nuevo va detrás del anterior, por lo tanto el que esta en el fondo actual apunte al nuevo, luego hago que el nuevo sea ahora el fondo. 

```cpp
template <class T> void Cola<T>::encolar(T dato) {  
    Nodo<T> *nuevo= new Nodo<T>();  
    nuevo=new Nodo<T>();  
    nuevo->setDato(dato);  
    fondo->setSiguiente(nuevo);  
    fondo= nuevo;
```

En el caso de que considere el caso de que la cola este vacía tendría, que comprobar eso y convertir el tope en el nuevo, Y si no esta vacía el fondo va a a apuntar al nuevo y el nuevo sera mi fondo actual.

```cpp
template <class T> void Cola<T>::encolar(T dato) {  
    Nodo<T> *nuevo= new Nodo<T>();  
    nuevo=new Nodo<T>();  
    nuevo->setDato(dato);  
      
  
    if (esVacia()){  
        tope=nuevo;  
    } else{  
        fondo->setSiguiente(nuevo);  
    }  
  
    fondo= nuevo;  
  
}
```

Para desencolar reviso si esta vacía y si lo esta lanzo error. Ahora hago que el tope sea el elemento siguiente (sea null o no) y luego elimino el viejo tope y recién asigno el elemento siguiente al tope (todo es moviendo los punteros de los elementos tope).

```cpp
template <class T> T Cola<T>::desencolar() {  
    if (esVacia()){  
        throw 404;  
    }  
    T dato=tope->getDato();  
    Nodo<T> *aBorrar=tope;  
    tope=tope->getSiguiente();  
  
    if (tope== nullptr){  
        fondo= nullptr;  
    }  //(1)
      
    delete aBorrar;  
    return dato;  
}
```

En  T dato=tope->getDato(); cree una variable dato. y guardo el dato del tope

En aBorrar guardo el viejo tope, luego en el tope=tope->getSiguiente(); cambio el tipe al proximo.

se if ( 1 ) hace referencia a cuando el tope apunte a vacio que quite todos los elementos por lo tanto el fondo tambien esta vacia 

El final borro el aBorrar y retorno el dato. 