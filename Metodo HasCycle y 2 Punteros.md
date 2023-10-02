Una lista es cíclica cuando un nodo tiene relación con otro nodo que ya tiene una relación preexistente en mi lista, esta relación extra genera que si yo itero y no tengo una forma de frenar, se repita infinitamente. 
El método **hasCycly** permite comprobar si en mi lista hay o no ciclos, esto por _medio del patrón de los 2 apuntadores, el apuntador rápido y el apuntador lento_

Ambos apuntadores inician en la misma posición inicial, pero la forma en la se mueven es distinta:

- El puntero Lento avanza de forma normal 
- El puntero Rápido avanza el doble (es decir va saltándose un nodo)

**![](https://lh5.googleusercontent.com/s5qWahEAy4aNNzK0oYvYIntKOkIcDrTPSrpVq6LcsIRA6jTJyHfGIICX0pBHi00fWEIXJZ4OkNcirstP0BmQKORXRiXPKj6VBDxYzx6RytuMhgxAqoLNAGF6ifzMRrm3m2j6Q0X3eMlVwjC_LgODfdY)**

El método hasCycle permite por medio de estos 2 ver si hay ciclo porque si el puntero lento alcanza o esta mas adelante del rápido quiere decir que hay algún ciclo como para que este se adelante.  Por otro lado si mi lista cíclica no tiene fin en algún momento estos dos se encontraran y el lento quedara adelante.  _Esta condición sera la que yo revise mientras mueva mis punteros_


### Código

```cpp

template<class T> bool Lista<T>::hasCycle(){
    Nodo<T> *rapido=inicio;
    Nodo<T> *lento=inicio;

    if (inicio== nullptr){
        throw 404;
    }

    if (inicio->getSiguiente()== nullptr){
        return false;
    }

    while (rapido->getSiguiente()!= nullptr || rapido== nullptr){

        if (rapido->getSiguiente()==lento || rapido==lento){
            //hay algun ciclo
            return true;
        }

        lento=lento->getSiguiente();
        rapido=rapido->getSiguiente()->getSiguiente();
    }

    return false;
}
```



## Ventaja Clave de los 2 apuntadores

Si yo alguna vez quisiera conocer el nodo que queda a la mitad de mi lista el método de los 2 punteros es clave. Ya que cuando el _puntero rápido llega al final de la lista, el lento **recién llega a la mitad de la misma**_ por lo tanto si yo con el puntero lento o colocando otro puntero referenciando ese y haciendo terminar el ciclo cuando rápido llegue a nulo o su próximo tendré fácilmente la mitad de mi lista. 

**![](https://lh6.googleusercontent.com/ONiJAXBLV2yGkQOrZF8m-jG5syhZB5q6XJ-Cu8Z9U_AkXnDVV2Ni2yqdxLRPE3XodaDMjN1Flvh-I8y6bm59NMWXdN0UOy6PlS6g2L3vYcnofVul9fvWJOuP_J_w1gBVQ53M7GRla5cLf2WBr3UEEeg)**




