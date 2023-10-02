```cpp
/**
 * Implementar un metodo de la clase lista que reciba como parametro un valor Pos.
 * El metodo debe buscar el nodo en la posicion Pos y moverlo a la ultima posicion.
 * Realizar moviendo conexiones. No creando nodos nuevos
 * @tparam T
 * @param pos posicion donde se desea reemplazar
 *
 */
template <class T> void Lista<T>::byJuan_1(int pos) {
    Nodo<T> *referecnia= nullptr;
    Nodo<T> *anterior_ref=inicio;
    Nodo<T> *ultima_posicion=inicio;
    int cont=0;

    if (inicio== nullptr){
        std::cout<<"Lista ingresada vacia e invalida"<<std::endl;
        throw 404;
    }

    //Ciclo para llegar a la ultima pocision

    while (ultima_posicion->getSiguiente()!= nullptr){
        ultima_posicion=ultima_posicion->getSiguiente();

    }


    //Ciclo para paunteros referenciados en "pos"

    while (cont<pos-1){
        anterior_ref=anterior_ref->getSiguiente();
        referecnia=anterior_ref->getSiguiente();
        cont++;
    }


    anterior_ref->setSiguiente(referecnia->getSiguiente());
    referecnia->setSiguiente(nullptr);
    ultima_posicion->setSiguiente(referecnia);


}


/**
 * Implementar un metodo de la clase lista que reciba como parametro un valor I.
 * El metodo debe buscar todos los nodos a partir de la posicion I, e invertirlos.
 * Puede utilizar otras estructuras.
 * @tparam T
 * @param I posicion donde se desea reemplazar
 *
 */
template <class T> void Lista<T>::byJuan_2(int I){
    int count=0;
    Nodo<T> *pocision_anterior_refereciada=inicio;
    Nodo<T> *inicio_de_reversa= nullptr;

    //Reviso que mi lista no sea nula
    if (inicio==nullptr){
        std::cout<<"Lista ingresada vacia"<<std::endl;
        throw 404;
    }

    while (count<(I-1)){
        pocision_anterior_refereciada=pocision_anterior_refereciada->getSiguiente();
        count++;
    }


    //debe buscar todos los nodos a partir de la posicion I, e invertirlos

    inicio_de_reversa=pocision_anterior_refereciada->getSiguiente();


    //Reversa
    Nodo<T> *anterior= nullptr;
    Nodo<T> *actual=inicio_de_reversa;
    Nodo<T>*futuro;


    while (actual!= nullptr) {

        futuro=actual->getSiguiente();

        actual->setSiguiente(anterior);
        anterior=futuro->getSiguiente();
        futuro->setSiguiente(actual);

        actual=anterior;
        anterior=futuro;

    }

    inicio_de_reversa=anterior;


    pocision_anterior_refereciada->setSiguiente(inicio_de_reversa);


}

/**
 * Implementar un metodo de la clase lista que reciba como parametro un valor Pos.
 * El metodo debe buscar el nodo en la posicion Pos y moverlo a la primera posicion.
 * Realizar moviendo conexiones.
 * No creando nodos nuevos
 * @tparam T
 * @param pos posicion donde se desea reemplazar
 */
template <class T> void Lista<T>::byJuan_0(int pos) {
    Nodo<T> *referecnia= nullptr;
    Nodo<T> *anterior_ref=inicio;
    int cont=0;

    if (inicio== nullptr){
        std::cout<<"Lista ingresada vacia e invalida"<<std::endl;
        throw 404;
    }

    //Ciclo para paunteros referenciados en "pos"

    while (cont<pos-1){
        anterior_ref=anterior_ref->getSiguiente();
        referecnia=anterior_ref->getSiguiente();
        cont++;
    }

    anterior_ref->setSiguiente(referecnia->getSiguiente());
    referecnia->setSiguiente(inicio);
    inicio=referecnia;


}
```

