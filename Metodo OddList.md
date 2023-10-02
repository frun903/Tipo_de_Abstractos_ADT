El método **oddList** es un método que consiste en hacer intercalar los elementos de una lista simplemente enlazada. De forma que todos los elementos pares (contando el 1er nodo como 1) queden después de todos los elementos impares

**![](https://lh3.googleusercontent.com/3RiYtyE8SVlOnlTgd4wQTQRzZfwrIhOP6QNY9rzZzg-hI9EIkI5Hjr4Cpy57j1BALbR9Qg1TF1t3j5ITzWG10Ghm3JGhq1MXb1-rRtTidOYQ0mmYvlLTl7Q3HxjAsEs1wDBsVLUHAlzig05w7Kztz2E)**
Esto lo haremos por medio de _2 punteros estáticos (es decir que no se moverán) y 2 dinámicos que se irán moviendo_. 
Dentro los punteros estáticos el primero (correspondiente a 1 impar) quedaron como el primer elemento en el inicio y el 2do estático ira siguiente a mi inicio_impar (correspondiente al nodo 2 par). La idea es que yo no pierda la referencia de estos dos punteros por eso son estáticos.

```cpp

    inicio_impar=inicio;
    impar=inicio_impar;
    inicio_par=inicio_impar->getSiguiente();
    par=inicio_par;


```

Los punteros dinámicos par e impar irán al inicio juntos a sus respectivos inicios pero luego la forma en que se moverán es distinta. 
Cada elemento apuntara a su siguiente pero el orden que se guardan es el siguiente:

**![](https://lh4.googleusercontent.com/GHOkiBqwp-o0QtjUFkfbsIdMu_Rv8Edddb-q20FSDGO215hkYKesllJvYOXyMJYko_OrQtkmLyqMtJMOjQFcpIPYSTy-_VqLrmJ-LPZ-vXXonC73xP6Z8YZWZBIsg5i1tspWBvcxCXrtoO9L2sr8jrc)**

```cpp
  while (par!= nullptr && par->getSiguiente() != nullptr){
            impar->setSiguiente(par->getSiguiente());
            impar=par->getSiguiente();
            par->setSiguiente(impar->getSiguiente());
            par=impar->getSiguiente();
    }

    impar->setSiguiente(inicio_par);
}
```


La condición sera que pare si el puntero a par es nullptr o que elemento siguiente a par sea nullptr es decir que no haya. 

Por ultimo pero no menos importante uno el ultimo elemento impar con el primer elemento par. Como? El ultimo nodo impar quedo referenciado con el puntero impar por lo tanto solo queda unirlo al inicio par gracia al puntero inicio par  


### Codigo Completo:

```cpp
// Odd Even Linked List

template<class T> void Lista<T>::oddLista() {
    //Defino los punteros fijos cabezas de linea
    Nodo<T>*inicio_impar= nullptr;
    Nodo<T>*inicio_par= nullptr;
    
    
    //punteros de movimiento o dinamicos
    Nodo<T> *par= nullptr;
    Nodo<T> *impar= nullptr;

    //Caso extremo un nodo o lista vacia
    if (inicio == nullptr || inicio->getSiguiente() == nullptr) {
        return;
    }

    inicio_impar=inicio;
    impar=inicio_impar;
    inicio_par=inicio_impar->getSiguiente();
    par=inicio_par;

    while (par!= nullptr && par->getSiguiente() != nullptr){
            impar->setSiguiente(par->getSiguiente());
            impar=par->getSiguiente();
            par->setSiguiente(impar->getSiguiente());
            par=impar->getSiguiente();
    }

    impar->setSiguiente(inicio_par);
}
```