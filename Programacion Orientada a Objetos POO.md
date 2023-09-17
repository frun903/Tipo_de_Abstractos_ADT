La **Programación Orientada a Objetos** es un paradigma de programación, un estilo, una lógica, una organización, una forma de pensar para resolver problemas. Con este paradigma nuestras aplicaciones están basadas en **objetos** en lugar de comandos y en **datos** en lugar de lógica.

Pensar en nuestra aplicación como objetos independientes que componen la información y sus comportamientos nos aporta muchos beneficios.Además, por trabajar con objetos separados, cada objeto debe funcionar de forma independiente y debe revisar su lista de dependencias; nos aseguramos de no tener ninguna dependencia de sobra o haciendo falta

## Clases 
Una clase son un **tipo de dato complejo**, serian como el plano de un objeto que el programador define segun sus necesidades. 

Una analogía seria pesar en las clases como los molde de galletas porque nos ayuda a crear todas las galletas independientes unas de otras pero con el mismo tamaño y la misma forma dependiendo del molde que elegimos para crearlas.

### Instancias
Las instancias son los _objetos inicializados de una clase_, una entidad única basada en una clase. Podemos decir que cada galleta es una instancia de nuestro molde de galletas.

Constructor: Es la primera función que trea mi objeto al ser instanciado. Este no es necesario ponerlo pero en el caso de hacerlo lleva el nombre de la clase. NobredeClase(). Puedo tener mas de un constructor e incluso puedo agregarle parametros al mismo.

```cpp

class dog{
	public:
	string Name;

	//Cosntructor  1
	dog(){
		Name= "Puca";
	}
	//Connstructor 2
   dog(string nombre){
	   Name=nombre;
   }
	
}

int main(){

	dog  miPrimerPerro(Puca);

	std::cout<<dog.Name<<std::endl;

}
```

En el constructor 2 pase por parámetro un string el cual dentro de la funcion defini como nombre. Luego en el main defino el objeto colocando primero la clase, luego el nombre del objeto y en este caso agregando el parametro. 

Esta mal que haya mostrado el nombre del obejto de esa forma. En la POO lo ideal seria crear mis propios métodos los cuales utilizare para invocar diversos elementos de los mismos. Eso lo veremos en el encapsulamiento. 


### Encapsulacion

La encapsulación es el proceso de combinar datos y métodos en una misma clase para evitar que sean modificados directamente por factores externos, esto nos da un poco mas de seguridad a nuestro código o programa. Por lo tanto debemos restringir la modificación de algunas propiedades sin dejar la posibilidad de acceder a todos nuestros datos (debemos permitir la lectura pero no la modificación), **para que esto funcione correctamente en la estructura de la clase las variables y los métodos (o funciones) deben comunicarse eficientemente.**

```c++
class Dog{
private:
string Ename;
strign Eladrido;
	public:
	string Ename;
	strign Eladrido;


//Constructor
   dog(strign name, string ladrido){
   Ename=name;
   Eladrido=ladrido;
   }

	string GetName(){
		return Ename;
	}
//Con el Get permito la lectura (en este caso del nombre) encpasule la lectura de mi nombre con una funcion

void setName(string newName){
	Ename=newName
}
//Permitio la Colocacion en este caso del nombre a mi objeto.

string GetLadrido(){
		return Eladrido;
	}

};

int main(){

Dog PerroUno("Puca","Guau");
cout<<PerroUno.GetName()<<endl;
cout<<PerroUno.GetLadrido()<<endl;

}

```

Los cambios de propiedades solo podan hacerse a través de mis métodos o funciones.  **El nombramiento de mis funciones debe ser específicamente la tarea que van a realizar**. 

Los **elementos en la sección privada de la clase me indican que solo podrán ser modificados por los métodos de la misma y no de forma externa.** Nadie fuera de los métodos puede acceder a los atributos privados. 


### Abstracción

La abstracción es usada por los lenguajes de programación para enseñarle a los usuarios únicamente los datos esenciales, lo que necesitan para realizar sus actividades en el sistema, y esconder el funcionamiento o los datos innecesarios del programa.
_Vamos a enseñar los datos y métodos que sirvan al usuario y vamos a esconder aquellos que no necesite ver (como la lógica interna del programa)._ 

En palabras mas simples es utilizar _metodos privados_, estos no podrán ser accedidos por mi usuario, ni podrán ser llamados en el main(). Pero son la lógica necesaria detrás de mi programa. 

Un ejemplo seria un programa de desarrollo bancario. suponiendo que una persona desee hacer una transferencia primero se deberá chekear si esa persona tiene los pesos suficientes para hacerla, _ese chekeo puede hacerse en un metodo privado_ dentro del método transferencia. 
 
### Herencia 

En la palabras muy simples la herencia es un principio de la programación orientada a objetos que nos ayuda a crear nuevas clases que “heredan” (y pueden mejorar) los métodos y propiedades de la clase “padre”.

Debemos crear una nueva clase pero antes de abrir las llaves (`{}`) vamos a añadir dos puntos, la palabra `public` y el nombre de la clase que estamos heredando.

```c++
class Mage
{
public:
        int mana, hp, power;

        Mage (int iMana, int IHP, int iPower)
        {
                // ...
        }
};

class IceMage : public Mage //Se indica la clase la que se hereda 
{
public:
        IceMage(int iMana, int IHP, int iPower):Mage(iMana, IHP, iPower)
        {
                /*:Mage() inidca que hereado los atributos del constructor de*/
        }
};
```

Por lo tanto herencia es la capacidad que tienen algunas clases **(clase derivada)** de heredar miembros y funciones de otras clases padre **(clase base)** y así crear jerarquías en nuestro programa.  
Una parte importante en la herencia es el tipo de **acceso** que se tiene a la información y **miembros** de la clase, estos son los siguientes:

- **Public:** Los datos y funciones en esta área pueden ser accedidos por quien sea, al heredar de otra clase con sus datos se mantienen como públicos.  
- **Private:** Ahora, los datos y funciones en esta área solo pueden ser accedidos por la clase y no por otros. Usando apuntadores uno puede saltarse esta regla pero no es recomendado.  
- **Protected:** Funciona igual que private, la diferencia es que las clases derivadas pueden acceder a los datos miembro de la clase base que heredan cuando en private esto no es posible.

Las clases no heredan los atributos y métodos privados, ante esto debere hacerlos publicos o _protegidos_, los atributos protegidos tienen otro nivel de seguridad no al nivel de los privados pero tampoco son publicos. 


## Polimorfismo 

Es la característica de un objeto de tomar varias formas. Cuando un tipo de dato hereda de otro, este puede tomar la forma del heredo 


## Archivos encabeados y Codigo fuentes 

Los archivos de encabezado y de código fuente son archivos diferentes a nuestro archivo principal (`main.cpp`) donde podemos guardar partes de nuestro código para usarlo desde nuestro archivo principal sin necesidad de escribir todo el código en un solo lugar.

Solo debemos añadir el siguiente código para importar (o incluir) estos nuevos archivos como libreria en el encabezado de mi main:

```cpp
#include "Clase.h"
```

En estos archivos tendré mi archivo Clase.h donde _declarare mis atributos y métodos de la clase denominado archivos de encabezados_, en este puedo simplemente declararlos aunque también podemos de desarrollarlos (es decir definir que harán estos atributos y métodos). Sin embargo eso puede hacerse en otro archivo de encabezado denominado Clase.cpp este se denomina _código fuente!_. 

Dentro de archivo encabezado:

```cpp
#ifndef CLASE_H
#define CLASE_H

class clase{

Public:
	Clase();
	void CallInput();
	

protected:
 numero int;
 letra char;

};

#endif
```


Luego en mi archivo código fuente:

```cpp
#include<iostream>
#include "Clase.h"

Clase::Clase()
{
	numero=15;
	letra='A';
}

void Clase::CallInput()
{
	std::cout<<"Buen dia!"<<std::endl;
}

```



