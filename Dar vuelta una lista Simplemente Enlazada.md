
Si yo quisiera dar vuelta una lista simplemente enlazada. El tema es que solo tengo acceso al nodo siguiente _(eso por propiedad de la lista simplemente enlazada)_ deberé cambar las relaciones y para tendré _referencias al nodo actual,siguiente y de anterior_. Esto se puede hacer por medio de punteros.

Tengo entonces referencia de 3 nodos el actual, el futuro (o siguiente) y  mi anterior  que si estamos al inicio de la lista es igual null.
![[darVueltaUnaListaSE.excalidraw]]

Lo que quedaría por definir es el ciclo iterativo, yo se que futuro existe (ya que por un if definí que mi lista tenga mas de 2 elementos), entonces el que no se si existirá es un siguiente a Anterior->Anterior osea un próximo actual. Por eso la condicion es que mi ciclo while termine si actual=nullptr o no existe. Luego de eso defino mi ultimo anterior como el inicio.


```cpp
template<class T> void Lista<T>::reversion() {  
    Nodo<T> *anterior= nullptr;  
    Nodo<T> *actual=inicio;  
    Nodo<T>*futuro;  
  
    //Si la lista esta vacia da un error  
    if (inicio== nullptr) {  
        throw 404;  
    }  
  
    //Si la lista tiene un solo nodo  
    if (inicio->getSiguiente()== nullptr) {  
        return;  
    }  
  
  
  
    while (actual!= nullptr) {  
  
        futuro=actual->getSiguiente();  
  
        actual->setSiguiente(anterior);  
        anterior=futuro->getSiguiente();  
        futuro->setSiguiente(actual);  
  
        actual=anterior;  
        anterior=futuro;  
  
    }  
  
    inicio=anterior;  
  
}```
