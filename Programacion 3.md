
**Profe:** Eliezer Salcedo
**Mail:** Eliezer.Salcedo@ucc.edu.ar

## Programa

|Semana | Tema |
|---------|-------|
|1/07| Recursividiad y Repaso|
| 7/08 | Recursividad |
| 14/08| Listas |
| 28/08 al 08/09| Pilas y Colas |
| 11/09 |  Arboles |
| 18/09 | **Parcial 1**  |
| 25/09 | Arboles y Grafos |
| 2/10 | Tablas de Hash |
| 09/10 | Ordenamiento |
| 16/10 | Ordenamiento y Busqueda |
| 23/10 | Busqueda |
|30/10 | **2do Parcial** |
|06/11| Recuperatorio| 




## Cursada

Promoción: Promedio >=8 pero la nota de los ejercicios y los parciales no debe ser menor que 7. 

**En C++ debo crear una apliacion por consola o console aplication en ingles.**



## Repaso POO

```C++
#include<iostream>
using namespace std;

//Creamos la clase Geometria como clase abstracta que tendra los metodos que utilizaran las clases hijas

class Geometria{

	//Creo las variables que despues tendran mis objetos
	int ancho;
	int alto;

	public: color color;
    Geometria (){};
  //Creo set y gets
    
    int getAlto(){return alto;}
    
    void setAlto(int a){
     alto=a;
    }
	int getAncho(){return ancho;}
	void setAncho(int a){ ancho=a;}

	//Declaro las funciones virtuales 
	
	virtual float
     
}

```

Creamos la clase abstracta color 

```c++

#include<stdint.h>
class color{
	 
	 private //las tres variables como dice el uninciado 
	uint8_t rojo, verde, azul;
//uint es un tipo de variables especial para optimizar le  memoria unit8_t equivale a 8 bits y unit32_t equivale a 32 bits, existen ciertos estandares para esa cantidad de bits 
	public //Los metodos publicos
	unit32_t getColor();
	void tenirColor(unit8_t r, unit8_t v, unit8_t a);

};

unit32_t getColor(){

unit32_t color=0;
color+=rojo+256+256;
color+= verde+256;
color+= azul;

//El tema de los 256 es una cuestion del pixel del color 
return color;
}

//Notese como lo llamo con clase::metodo()
 void color::tenirColor(unit8_t r, unit8_t v, unit8_t a){
 rojo+= r;
 verde+= v;
 azul += a; 
 
 }
```

Ahora creamos la clase cuadrado hija de la clase Geometria

```c++
#include "Geometria.h" //llamamos a geomatria ya que hereda de ella
#include <cmath>
class Cuadrado: public Geometria{
	public
	Cuadrado(int alto, int ancho); Geometria (alto,ancho)()
   float getDiagonal();
   float getSuperficie();
   float getPerimetro();

};

float Cuadrado::getDiagonal(){
 return sqrt((alto*ancho)+(alto*ancho))
};

float Cuadrado::getSuperficie(){
return ancho+alto;
};

float Cuadrado::getPerimetro(){
 return (2*ancho)+(2*alto)
};


```

Entonces las clases abstractas son clases que tienen metodos que para cuando haya una que herede si o si deba llamarla a la progenitora. _Buscar una mejor defincion_  

#### Manejo de Excepcion/ Try and Catch

Dentro del try va el código que quiera ejecutar y en el cathc pondré mi mensaje de error. 

```c++
template<class T>
T Calculadora<T>::dividir(T a, T b)
{
	
}
```

El trowh corta con la ejecución del programa por lo que no llegara mas lejos en el mismo. 
Lo negativo de este método es que es _bastante lento_ por el manejo de memoria. 


#### Template/Plantillas:
Funciones donde cuando se declaran con tipo template para poder usar cualquier tipo de variable en el futuro. Desde esta podremos colocar cualquier tipo de variable.

```c++
#include <iostream>
using namespace std;

template<class T>
class Calculadora{
public:
    T sumar(T a, T b);
    T restar(T a, T b);
    T multiplicar(T a, T b);
    T dividir(T a, T b);
};

template<class T>
T Calculadora::sumar(T a, T b){
    return a + b;
}

template<class T>
T Calculadora::restar(T a, T b){
    return a - b;
}

template<class T>
T Calculadora::multiplicar(T a, T b){
    return a * b;
}

template<class T>
T Calculadora::dividir(T a, T b){
    return a / b;
}

int main(){
    Calculadora<int> calcEnteros;
    cout<<calcEnteros.sumar(2, 5)<<endl;
    cout<<calcEnteros.restar(10, 3)<<endl;
    cout<<calcEnteros.multiplicar(6, 4)<<endl;
    cout<<calcEnteros.dividir(8, 2)<<endl;

    return 0;
}
```

Recordar que c++ o c no saben en cuales esta la plantilla por eso coloco  template<class T> este sabrá que corresponde a una función del tipo template. 
Ojo al escribir los template y los métodos deberé tener en cuenta que tipo de datos utilizare ya que no todos los operadores son compatibles con esto. Por ejemplo no puedo dividir dos string.



 
