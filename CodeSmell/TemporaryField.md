# Campo temporal


## Signos y síntomas

Los campos temporales obtienen sus valores (y, por lo tanto, son necesarios para los objetos) solo bajo ciertas circunstancias. Fuera de estas circunstancias, están vacíos.


## Razones del problema

A menudo, los campos temporales se crean para su uso en un algoritmo que requiere una gran cantidad de entradas. Entonces, en lugar de crear una gran cantidad de parámetros en el método, el programador decide crear campos para estos datos en la clase. Estos campos se utilizan sólo en el algoritmo y no se utilizan el resto del tiempo.

Este tipo de código es difícil de entender. Espera ver datos en campos de objeto, pero por alguna razón casi siempre están vacíos.


## Tratamiento

Los campos temporales y todo el código que opera en ellos se pueden colocar en una clase separada a través de Extract Class. En otras palabras, está creando un objeto de método, logrando el mismo resultado que si realizara Reemplazar método con objeto de método.

Introduzca Null Object e intégrelo en lugar del código condicional que se utilizó para comprobar la existencia de los valores de campo temporales.

Gracias a esto tenemos mejor claridad y organización del código.