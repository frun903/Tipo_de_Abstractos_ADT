Primero debemos crear nuestro nodo que sera luego el que se va enlazar. El nodo tendrá un valor y una relación con los siguientes  y anteriores nodos por medio de punteros.
Luego debere hacer el construcutor de mi nodo

```cpp

template<class T>  
class Nododoble{  
private:  
    T dato;  
    Nododoble<T> *siguiente; //me indica el siguiente nodo en la lista  
    Nododoble<T> *anterior; //me indica el nodo anterior en la lista  
  
//Un constructor sin mucho uso  
    Nododoble(T x){  
        dato=x;  
        siguiente=nullptr;  
        anterior=nullptr;  
    }  
  
public:  
    T getDato(){  
        return dato;  
    }  
  
    void setDato(T d){  
        dato=d;  
    }  
  
    Nododoble<T> *getSiguiente(){  
        return siguiente;  
    }  
  
  
    Nododoble<T> *getAnterior(){  
        return anterior;  
    }  
  
  
    void setSiguiente(Nododoble<T> *siguiente){  
/*Aqui estoy diciendo a este nodo "This->siguiente" hazlo igual a la pocicion de memoria que te estoy pasando osea siguiente*/  
        this->siguiente = siguiente;  
    }  
  
  
    void setAnterior(Nododoble<T> *anterior){  
/*Aqui estoy diciendo a este nodo "This->siguiente" hazlo igual a la pocicion de memoria que te estoy pasando osea siguiente*/  
        this->anterior = anterior;  
    }  
  
};
```


Ahora pasamos a definir la clase lista doblemente enlazada. Primero definimos los primeros elementos de mi lista doblemente enlazada (estos seran 2 uno correspiende al que sera siempre el primer elemente head-cabeza y el ultimo elemento el cual sera tail). Siguiendo las filminas de Vulcano "en una lista vacia, tanto head como tail apuntan al mismo nodo."

```cpp
template<class T>  
class LisDoble {  
protected:  
    Nododoble<T> head;  
    Nododoble<T> tail;  
  
public:  
    LisDoble(Nododoble<T> primerNodo){  
        //Como para este punto la lista esta vacia tanto el head como el tail apuntan a lo mismo  
        head= primerNodo;  
        tail= primerNodo;  
    }

```
 
Como mi lista es doblemente enlazada deberé tener mas de un método para la insercion de un nodo nuevo. Un metodo sera correspondiente solamente a colocar un nodo adelante como una lista simple como parametro debere aceptar el nuevo nodo que quiera agregar


### Insertar Datos entre dos nodos
![[ListaDoblementeEnlazada.excalidraw]]

Para Poder realizar esta acción deberé recorrer mi lista y llegar al punto donde yo quiera colocar este elemento. Para hacerlo requiero de 4 elementos:
- Un contandor ("posActual")
- Un puntero del tipo template nodo auxiliar que recorra que mi lista desde el inicio (_*aux_) hasta un elemento antes de donde quiero colocarlo.
- Un puntero del tipo template nodo auxiliar que recorra que mi lista desde el inicio (_*aux2_) hasta el elemento donde quiero colocarlo.
- El nodo nuevo que colocare en la lista (_*nuevo_)

Entonces al puntero aux y aux2 lo colocare señalando al nodo inicial osea en el inicio y al posActual=0, por otro lado debo como "cargar en un nodo" al dato que yo quiero agregar a la lista por eso al _nodo *nuevo le setiaremos_ el dato

```cpp
template<class T> void LisDoble<T>::insercion(int pos,T dato){  
    int PosActual=0;  
    Nododoble<T> *aux;  
    Nododoble<T> *aux_2;  
    Nododoble<T> *nuevo;  
    nuevo=new Nododoble<T>;  
    nuevo->setDato(dato);
    ```

_Recorro por medio de dos whiles a mis punteros._ Al de aux como en una lista simplemente enlazada lo llevo hasta un elementos antes de donde quiero poner el nodo nuevo, en cambio a aux_2 lo llevo a la poscision donde quiero poner al nuevo nodo.

```cpp
while (aux != nullptr && PosActual< pos-1){  
    aux = aux->getSiguiente();
    posActual++;
}

//Vuelvo a colocar a PosAcutal=0
posActual=0;

while (aux_2 != nullptr && PosActual< pos){  
	  aux_2 = aux_2->getSiguiente();
    posActual++;      
}