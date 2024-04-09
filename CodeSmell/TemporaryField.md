
# Campo Temporal (Temporary Field)
## Signos y Síntomas
Los campos temporales obtienen sus valores (y por lo tanto son necesarios para los objetos) solo en determinadas circunstancias. Fuera de estas circunstancias, están vacíos.

![Dibujo articulo Campo Temporal 1](./assets/temporary-field-01.png)

## Razones del Problema
Muchas veces, los campos temporales se crean para su uso en un algoritmo que requiere una gran cantidad de entradas. En lugar de crear una gran cantidad de parámetros en el método, el programador decide crear campos para estos datos en la clase. Estos campos se utilizan solo en el algoritmo y no se utilizan el resto del tiempo.


## Signos y síntomas


Los campos temporales obtienen sus valores (y, por lo tanto, son necesarios para los objetos) solo bajo ciertas circunstancias. Fuera de estas circunstancias, están vacíos.

![imagen](../CodeSmell\assets\temporary-field-01.png)

## Razones del problema

A menudo, los campos temporales se crean para su uso en un algoritmo que requiere una gran cantidad de entradas. Entonces, en lugar de crear una gran cantidad de parámetros en el método, el programador decide crear campos para estos datos en la clase. Estos campos se utilizan sólo en el algoritmo y no se utilizan el resto del tiempo.

Este tipo de código es difícil de entender. Espera ver datos en campos de objeto, pero por alguna razón casi siempre están vacíos.

![imagen](../CodeSmell\assets\temporary-field-02.png)

## Tratamiento

Los campos temporales y todo el código que opera en ellos se pueden colocar en una [clase separada](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/ExtractClass.md) a través de Extract Class. En otras palabras, está creando un objeto de método, logrando el mismo resultado que si realizara [Reemplazar método con objeto de método](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern%5CReplaceMethodWithMethodObject.md).

[Introducir objeto nulo](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/IntroduceNullObject.md) e intégrelo en lugar del código condicional que se utilizó para comprobar la existencia de los valores de campo temporales.

![imagen](../CodeSmell\assets\temporary-field-03.png)

![Dibujo articulo Campo Temporal 2](./assets/temporary-field-02.png)

## Tratamiento

- Los campos temporales y todo el código que opera en ellos se pueden colocar en una clase separada mediante [Extraer Método](../RefactoringPattern/ExtractMethod.md). En otras palabras, estás creando un objeto de método, logrando el mismo resultado que si realizaras [Reemplazar método con objeto de método](../RefactoringPattern/ReplaceMethodWithMethodObject.md).
- **[Introduce Null Object](/RefactoringPattern/IntroduceNullObject.md)** e intégralo en lugar del código condicional que se utilizaba para verificar la existencia de los valores de los campos temporales.

- ![Dibujo articulo Campo Temporal 3](./assets/temporary-field-03.png)


## Beneficio


Gracias a esto tenemos mejor claridad y organización del código.

Mejora la claridad y organización del código. 

