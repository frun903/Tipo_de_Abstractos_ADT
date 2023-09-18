![[Arboles_Practico.excalidraw]]


Otra restriccion para la clase practica, si el dato existe no lo intruduzca osea no repetidos
## Estructura (Código) 

La estructura del nodo del arbol sera un dato y 2 punteros, con todos los Gets y Sets.


En la clase arbol lo primero que debo inicizalizar es la _raiz/root_ para saber que existe (Seria como el inicio en listas, queuqe, ect). 

### Constructor: 
La raiz apunta a null


### Search/Buscar
Es buscar un nodo en mi arbol este procedmiento debera ser recursivo en su recorrido. Para poderlo retornar voy a entrar por la raiz y de ahi me fijo si mi valor es mayor o menor para saber si debo ir por la derecha o izquierda. Este metodo recursivo **search_2** _estara en private ya que el usuario no tendra a acceso_ este me pedira un dato y la direccion de la raiz, luego recorrera recursivamente el arbol

```cpp
template <class T> T ArbolBinario<T>::search(T dato) {  
  /*Aqui llamo al metodo recursivo*/  
    return search_2(dato,root);  
}  
  
template <class T> T ArbolBinario<T>::search_2(T data, NodoArbol<T> *r){  
      
    //Caso de arbol vacio  
    if (r== nullptr){  
        throw 404;  
    }  
  
    //Caso de que el dato este en la raiz  
    if (r->getData()==data){  
        return r->getData();  
    }else if (r->getData()>data){  
        //Aqui vuelvo a entrar a la funcion d emanera recursiva por el lado izquierdo  
        //Y le mando la poscision Left izqu de mi nodo        return search_2(data,r->getLeft());  
    }else  
    {  
        //Aqui vueleco entrar por la derecha  
        return search_2(data,r->getRight());  
    }  
      
}
```

### Metodo Put
Similar al anterior haré una función privada Para la búsqueda recursiva **put_2**4


### Remover
El tema con remover es que hay varios casos. Ya que si el nodo tiene hijos debere acomodarlo 


