Comenzando por lo mas simple tengo mi nodo que contendrá mi dato y una referencia al nodo siguiente en forma de puntero.

```cpp
template<class T>
class Nodo{
    private:
        T dato;
        Nodo<T> *siguiente;

```

Para el nodo tendre sus SET que seran para establecer el dato por ende ingresaremos variables por teclado y sus Get para obtener el dato

```cpp
    public:
       T getDato(){
           return dato;
       }

       void setDato(T d){
           dato = d;
       }

       Nodo<T> *getSiguiente(){
           return siguiente;
       }

       void setSiguiente(Nodo<T> *siguiente){
           this->siguiente = siguiente;
       }


};```

Para el desarrollo de la clase lista definiré un nodo de inicio que sera el punto de referencia de mi lista (es decir donde comenzara esta).

```cpp
template <class T> class Lista {
private:
  Nodo<T> *inicio;
```


### Constructor:
Dentro del constructor haré que el inicio apunte al nullptr.

```cpp
template <class T> Lista<T>::Lista() { inicio = nullptr; }
```


### Insertar entre 2 elementos de la lista:
Para Poder realizar esta acción deberé recorrer mi lista y llegar al punto donde yo quiera colocar este elemento. Para hacerlo requiero de 3 elementos:
- un contandor ("posActual")
- un puntero del tipo template nodo auxiliar que recorra que mi lista desde el inicio (_*aux_)
- El nodo nuevo que colocare en la lista (_*nuevo_)

Entonces al puntero aux lo colocare señalando al nodo inicial osea en el inicio y al posActual=0, por otro lado debo como "cargar en un nodo" al dato que yo quiero agregar a la lista por eso al _nodo *nuevo le setiaremos_ el dato


```cpp
template <class T> void Lista<T>::insertar(int pos, T dato) {
  int posActual = 0;
  Nodo<T> *aux = inicio;
  Nodo<T> *nuevo;
  nuevo = new Nodo<T>; //defino a nuevo como un nuevo nodo
  nuevo->setDato(dato); //le seteo el dato que ingrese por parametro
```

Ahora _consideremos el caso extremo donde mi lista este vacía o nos hayan pasado por parámetro la posición 0_  ante esto deberé colocar el nuevo nodo en el inicio. A este punto yo ya declare a nuevo como un nodo (nuevo= new nodoT) y le setie un dato. Entonces _coloco a nuevo como el inicio recordemos que la función de setSiguiente tiene como parámetro el elemento en el que que se convertirá
```cpp
 void setSiguiente(Nodo<T> *siguiente){
           this->siguiente = siguiente;
       }
//Yo al llamar la funcion diria:
  nuevo->setSiguiente(inicio);

```
Le pasaría por paramento el inicio ahora el nuevo es el inicio
y despyes traspaso sus datos dicendo que el inicio= nuevo.
```cpp
  if (pos == 0) {
    nuevo->setSiguiente(inicio);
    inicio = nuevo;
    return;
  }
```

Yendo al caso donde coloco entre 2 nodos debo considerar que deberé recorrer la lista, _mi condición de frenado sera hasta que la lista sea vacía_ (nos daremos cuenta de esto cuando auxiliar apunte ya a nullptr) o _un lugar antes de la posición donde yo quiero agregar mi nodo_, un lugar antes porque ahí es donde yo colocare el nuevo elemento.

![[Estructura Lista.excalidraw]]

Entonces una vez definido como frenara mi ciclo el mismo lo que hará es mover mi puntero hasta llegar a la posición deseada.
Una vez llegue, salgo del ciclo y hago que el nodo nuevo apunte al nodo siguiente (esto por medio de puntero aux en el nodo anterior) y que el anterior apunte al nuevo.

```cpp
 while (aux != nullptr && posActual < pos - 1) {
    aux = aux->getSiguiente();
    posActual++;
  }

  if (aux == nullptr) {
    throw 404;
  }

  nuevo->setSiguiente(aux->getSiguiente());
  aux->setSiguiente(nuevo);
}
```

De aquí podemos crear dos métodos mas **agregar ultimo** y **agregar al inicio** ambos variaciones del anterior para agregar ultimo solo modifico el ciclo while ahora controlare que _el elemento siguiente a aux sea distinto a nullptr_ cuando se deje de cumplir esa propiedad es porque el próximo elemento es nullpt estamos ante el final de la lista. En ese lugar repito el procedimiento el nodo donde apunto aux apunte a nuevo y nuevo a nullptr por medio del siguiente de aux:
```cpp
template <class T> void Lista<T>::insertarUltimo(T dato) {
  Nodo<T> *aux = inicio, 
  Nodo<T> *nuevo;
  nuevo = new Nodo<T>;
  nuevo->setDato(dato);

  if (aux == nullptr) {
    nuevo->setSiguiente(inicio);
    inicio = nuevo;
    return;
  }

  while (aux->getSiguiente() != nullptr) {
    aux = aux->getSiguiente();
  }

  nuevo->setSiguiente(aux->getSiguiente());
  aux->setSiguiente(nuevo);
}```

Para **agregar al inicio** tengo 2 opciones usar el método agregar entre con pocision cero pero sera poco eficiente llamar a una función dentro de otra función. O simplemente hacer lo que esta dentro del if verificando que la lista este vacía.
```cpp
template <class T> void Lista<T>::insertarPrimero(T dato) { insertar(0, dato); }
```


### Eliminar elemento de la Lista
Para borrar un elemento de la lista, también requiero de 3 elementos
- Un puntero aux que sera el que recorra la lista
- Un contador
- Un puntero del tipo nodo _*aBorrar_ que me indicara cual elemento barrare


La recorrida de la lista es la misma que en insertar nodo, una vez llego a un elemento antes del que quiere borrar, guardo en _aBorrar_ el elemento siguiente a donde esta auxiliar (osea el elemento que quiero borrar). 

Una vez echo eso digo el nodo señalado por aux ahora apuntara al siguiente del de 
borrar y al nodo que señala aBorrar lo elimino.  

```cpp
template <class T> void Lista<T>::remover(int pos) {
  Nodo<T> *aux = inicio, *aBorrar;
  int posActual = 0;

  if (pos == 0) {
    inicio = inicio->getSiguiente();
    delete aux;
    return;
  }

  while (aux != nullptr && posActual < pos - 1) {
    aux = aux->getSiguiente();
    posActual++;
  }

  if (aux == nullptr) {
    throw 404;
  }

//Parte descripta mas arriba

  aBorrar = aux->getSiguiente();
  aux->setSiguiente(aBorrar->getSiguiente());

  delete aBorrar;
}
```


![[Borrar elemento en lista.excalidraw]]


### Obtener Dato de una Lista
Para obtener un elemento de la lista, requiero de 2 elementos
- Un puntero aux que sera el que recorra la lista
- Un contador
La recorrida es muy similar a las anteriores pero esta vez a nuestro puntero del tipo nodo axu lo llevaremos _hasta el elemento que queremos._ Una vez fuera del ciclo y en el elemento que queríamos hacemos un set dato del nodo señalado por auxiliar. 

```cpp
template <class T> void Lista<T>::reemplazar(int pos, T dato) {
  Nodo<T> *aux = inicio;
  int posActual = 0;

  while (aux != nullptr && posActual < pos) {
    aux = aux->getSiguiente();
    posActual++;
  }

  if (aux == nullptr) {
    throw 404;
  }

  aux->setDato( dato );
}
```