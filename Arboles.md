La estructura de datos en forma de árbol se define de manera _recursiva_ esto quiere decir que tiene un caso base y una estructura repetitiva. Donde c/d nodo puede o no tener nodos hijos, y en el caso de tener hijos estos son también nodos. En el caso de que un nodo no tenga hijos es el caso base y si tiene ya son otro árbol. 

C/d nodo de un árbol puede tener varias raíces donde cada raíz es un nodo que puede tener arboles. 

Los arboles son  _n enarios_ cuando cada nodo puede tener n ramas. En cursado usaremos _arboles binarios_ es decir por cada nodo puede tener 2 ramas. 

**![](https://lh6.googleusercontent.com/MfOorupf6NDhtjDPAg6zRMxUnK8VF8gpSOliyYlfMC7K-YsUhGz-g9C7ckMu0JwSRFFzdHvVhp3orLGhZncRNK5Jo0GM6796mHK9C8KBxDbZehdiHb2HRaOUS015TVq3nhKr8uo73RYMYRpDd30SekI)**

#### ¿Que cosas No admite un arbol?

- No se admite que dos nodos sean padres de un mismo nodo 
**![](https://lh6.googleusercontent.com/LLfRIuSMGBlE4NpK3FwrdUGl7jr6gMIBQvc6kZsV9DcEP-Q7NbYGS2oK2FsdzY8k8_9EgFFoDHnRpyHL2VsjqplfuY0iZ-kISYNJ0P3WG1_kOt48OAYW9highGQ7Xu5dwx3BjmIPifodS1suXQKU7ew)**
- No se admite que un nodo hijo sea padre de su mismo nodo padre
**![](https://lh4.googleusercontent.com/gm-ALww5NOWN4sJATna8i0yvwCEfyaVM3iyicpSfW2e529kE-nzXEwo8ehTjapzj2YFPsJ6V39eeKot7OltiL206po4UHgdl_uY0MPFwV14Xp9qbJq6gVW18fwMqd9oYr_sjNK1CvtSePPRG2bY3vlU)**

#### Arbol Estrictamente Binario
Que un árbol sea estrictamente binario quiere decir que _solo puede tener 2 nodos hijos o hojas, o directamente ninguno_. Es decir no puede tener una hoja sola.

**![](https://lh4.googleusercontent.com/HE--FpGhK261-iG5J41uTaohxfhD1zQfRhjxOnTEB4QWraEmxOV0V2AebfgiQ1jAq8bKFTmyp7oWH0zoRq8_jEXAm6681mj8dd9FDYeAY_bvmOBqCckDv9AuNfjHpKDiDFdU0X08P_bthswRUKQ45UA)**

### Niveles de Profundidad 
Los niveles de los arboles se definen de la siguiente manera, _el primer nodo o raíz del árbol tiene el nivel 0_ y de ahí para abajo tengo mas niveles (es decir cada nodo es un nivel mas que su padre).
**![](https://lh3.googleusercontent.com/9qGhFUcqj_QoUFvwwTUVgDBJ8WNvhUHMbS4RHMvrPlo4DrI-Fahth8tb75nYSmI31JlWja_OvqXTexgLyQp4Ejmeyug2H9keIA7uWShXFQYsd4_blvqwQz06rE0pjmHC1pzqUT0bbddd-sLZ6Pd4VgA)**
## Nodos y Representación Ligada 
Para que un árbol se utiliza la representación ligada o dinámica donde cada nodo tiene cierta información y un par de punteros para los otros 2 nodos.

**![](https://lh3.googleusercontent.com/hCo4ZcUTA5TmcOYL5x0wxTQFSPZgCli3aRLDq5QCxtWJd1YHOi1cQXB-ChSXzUsbU_4o64MHbJEqVcxfU_o9N6hGZrtadP0AVIw47kdnWpsXW4cyoJmxoVE1z_bPrCXXfnz0PtI1HXCbPH62njJCyw4)**
**![](https://lh3.googleusercontent.com/wk3PXpfAfPm1hfsGz9K7xN6zoO6T95h6D1pUZiXpA59uilbG0gpBJ5C88fvoPR7MvCUNI3ygUZsFmpO1QT-YjVaznzf9vOsvrD5rhw78b8qidLD9l5qTAAM786h5eAb3Ys0q2L7khsE00SbGXq2Yy4s)**

Si fuese n-enario tendría mi información y n punteros. 

## Aplicaciones, Ventajas y Desventajas

### Ventajas y Aplicaciones
- **Clave para organizar y encontrar  información rápida**. Por ejemplo nuestros discos esta dividido en arboles, uno para mi Sistema Operativo, otro para el word, ect.
- Sirven para la _representación de funciones matemáticas_.
- Sirve para representar juegos tipo tablero (ta-te-ti, damas, ajedrez, ect).
- **Al tener una estructura ordenada de por si, encontrar datos es mas rápido**. Es decir su árbol se ordena por naturaleza y se equilibran. 

### Desventaja
Por ser **recursivo consume mucha memoria**, tanto recorrer o buscar un en árbol consume memoria. 

## Organizar y buscar en un Árbol (balanceado y no balanceado)
La organización durante este curso sera de _los elementos mayores por la derecha y los menores por la izquierda._ Una tenga mi primer nodo y se cumpla esta regla los futuros nodos padres usaran este criterio y cada nodo tendrá su criterio de organización. 

**![](https://lh6.googleusercontent.com/W-5rW02zVyhQEC5qdifL06Nj0xThQjmNe_vqcmSEb8tsf3W8xcNZ4oyDCbTb_VtlfsRsRNHv2lccMhYRxO6IPtRN9bep05brKcKyR7IHnzMxI-H42dfJ_wwPWuaMoDseX1nwWLliX57T6-cQ5KkXeTE)**

>[!nota] Ejemplo Busqueda en Arbol
> Si busco el nueve, es mayor que el 14 NO entonces voy por la izquierda, es nueve? No es 4 nueve es mayor que 4 SI voy por la derecha es el nueve? si Listo.

La estructura del árbol **simplifica la cantidad de if** ya que no tengo que ir haciendo la consulta en c/d nodo del recorriendo elemento por elemento.

Otra cosa que debo tener bien en cuenta es el _**criterio de selección**_  es decir la pregunta es clave para tener un árbol bien _balanceado_. 

En el caso de arboles binarios la pregunta debe ser la mejor para dividir todos mis datos en 2. Por ejemplo si tengo 1000 números y el 14 es mi raíz _no conviene_ ya que de un lado tendré 13 números y del otro 982 esta división no es tan correcta. 

Los arboles tienen la capacidad de romperse o ser poco prácticos a la hora de optimizar mis datos, ahí entra _si mi árbol es balanceado o no_. Un árbol bien **balanceado es aquel donde ambas ramas o lados de un árbol tienen un tamaño similar** 

```
        10
       /  \
      5    15
     / \   / \
    3   7 12  18
```

>[!nota] ChatGPT Dice
En un árbol binario _bien balanceado_, la altura de los subárboles izquierdo y derecho de cualquier nodo difiere en un máximo de 1 nivel. Esto significa que el árbol está equilibrado y tiende a ser eficiente en términos de búsqueda y otras operaciones. En contraste, un árbol binario _no balanceado_ tiene diferencias significativas en la altura entre los subárboles izquierdo y derecho de los nodos. Esto puede conducir a un rendimiento deficiente en ciertas operaciones, especialmente en la búsqueda

```
		10
       /   \  
      5    15
     /   
    3   
   /    
  2
```

Si un árbol tiene una rama muy amplia de un lado y del otro no, estamos en parecencia de un árbol no balanceado.  

#### Observaciones:
- En un arbol bien balenceado un solo if ya divide la mitad de los datos
- La nutarleza del arbol se va ir ordenando mientras la armo por el mismo criterio de seleccion de los nodos, esto trae a su vez el factor de riesgo de que se me amplie una de las ramas. 


## Formas de Recorrer un Árbol
Existen diferentes estrategias para recorrer las ramas de un árbol (sin repetir la rama por la que pase). 

### Recorrer un Árbol en PreOrder
Con prioridad a la profundidad esta revisa mas rápida el fondo del árbol.  
- Reviso Raiz si no es continua por la izquierda
- Visita todo subArbol izquierdo siempre que exista
- Si no hay mas nodo por la izquierda visito la derecha volviendo  por la raiz.

Si no queda mas por la derecha retorno nuevamente por la raíz busco izquierda sino derecha. 
**![](https://lh4.googleusercontent.com/Ugn-MWB17DJTquNWb83fpuXDQ58HARd3oMQ84nOnlKfd7ij1SzbT6rCHYl7lSrATTFbixSMh7ENfYA7nYIzYEN-IimMNF6nV_YEEAWPVSYp2S3mEJZR4TH0RHnZVEuMJ9iZkDuCjROMP0J3hb2CIXgc)**
Lo bueno de la **recursividad** es que c/d "ciclo de busqueda" es como una instancia nueva donde yo puedo repetir este patrón.  

### Recorrer un Árbol en Orden 
Otra manera de recorrer el árbol es en orden, u orden simétrico.
- 1ro visito el hijo izquierdo _mas profundo en orden_ hasta que no haya mas izquierdos
- 2do visita la raiz (significa que ya no hay nada a la izquierda consulta derecha) 
- 3ro recorrer el subarbol dercho en orden

**![](https://lh5.googleusercontent.com/odFP5luWPxvTsEt-mHa0zqlJ6P3W4CMuAsUwaOHUMTQp3lL79Usyr6E5LyIKgOzU347s7rOh3qB_f9YKGMQiz3g_rx_j7ylB64A7teENmMJ1ufjljPEPIrzwVBaVpcxWPPDttoRoTBWCBRJrCktKT6I)**
_Es importante considerar que los finales hijos son considerados raíces._ 

### Recorrido en PostOrder
- Recorre todo el subArbol Izquierdo (hasta el ultimo nodo izquierdo)
- No hay mas izquierdo recorro todo el subArbol derecho (hasta el ultimo nodo derecho)
- No queda nada por izquierda y derecha, recién ahí reviso la raíz. 
**![](https://lh4.googleusercontent.com/Cni4AR00nRffFqDfvpxQzL8O0EFwP3LDfthVsPPTm0hnq8RrBRIK0guDJ7arTE3bJSvU5gjL0rWpRtjgW2BbOkw6E0t0smg3_18KC3xslmeu2DjQhSio4QVxUv2I9qrYI7XR1Gmab6Flhop5X0fJVaU)**

## Código 
[[Arboles Código]]


