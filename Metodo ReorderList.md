El metodo **Reorder List** Incluye todos los métodos vistos anteriormente. El mismo consiste en tomar la mitad inferior de mi lista y dar vuelta sus elementos.

**![](https://lh4.googleusercontent.com/PW2lefNJ2I_pJtiBSuE3w_TSLyGFUpnlBiwe6yvuq5HIBmEse3oXKJZu4ugxs5Gp1YEfJInGs3AywIRXMFgNM4MoxjdTV9ucRospiHEZaY808OUw5mQNx0Wez3l17HSEzr4OYM6wloTo5FJKFmsGIJw)**

1. Hallo la mitad de la lista con mi método de dos apuntadores
2. Creo un puntero estático que guarde esa segunda mitad de la lista
3. Utilizo el método de dar vuelta una lista para dar vueltas todos sus elementos 
4. Hago la union entre las dos mitades (como lento quedo en la mitad hago lento.getSigiuente(mitadmas))

#### Observación

**![](https://lh6.googleusercontent.com/oK4iLCgnm8BPEp-SrwqYzrK3GwX-pZU3kOnN1Qi4g98ANrxyhP6WUzCm7p-J7CPEd2R02zJx6yZGWyktocqHi4g6dmB6zK2uDIgQdZK7iLbJ1xnWP_9n-wuXS9JB66q-UOSYWnr4h_DLqjQdhygQpPs)**

**![](https://lh6.googleusercontent.com/wngs7wKwxrANQoGd5T5faH8wAmezTawojAUxeFv0JhzHDVMP4Bj0GVgPbS0VU2RXXwG3698Ble9LAWG5Kzos9d_F6s7F13831pXdmYNl73jxxzoeNZFMfxYy23nOpefMhRHyi6RuYB3T87uZbG5XUzg)**

En otras palabras si mi lista era par el medio quedaba de forma incorrecta para el Reorder List para eso se modifico el while para que quedara una posicion antes el puntero lento si mi lista era par para poder re acomodar correctamente.   

### Código

```cpp

template<class T> void Lista<T>::Reorder() {

    if (inicio== nullptr){
        throw 404;
    }

    //Primero a encontrar mi mitad
    Nodo<T> *rapido=inicio;
    Nodo<T> *lento=inicio;
    Nodo<T> *medio= nullptr;


    while (rapido->getSiguiente()->getSiguiente() != nullptr && rapido->getSiguiente() != nullptr){
       rapido=rapido->getSiguiente()->getSiguiente();
       lento=lento->getSiguiente();
    }

  medio=lento->getSiguiente();


    //A dar vuelta la 2da mitad
    Nodo<T> *anterior= nullptr;
    Nodo<T> *actual= medio;
    Nodo<T> *futuro= nullptr;

    while (actual!= nullptr) {

        futuro=actual->getSiguiente();

        actual->setSiguiente(anterior);
        anterior=futuro->getSiguiente();
        futuro->setSiguiente(actual);

        actual=anterior;
        anterior=futuro;

    }

    medio=anterior;



    //Falta unir ambas!
   lento->setSiguiente(medio);



}
