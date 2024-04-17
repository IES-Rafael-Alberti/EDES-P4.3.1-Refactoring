# Push Down Field 

## Problema
¿Es un campo utilizado solo en algunas subclases?

![Push-Down-Field-Before.png](assets%2FPush-Down-Field-Before.png)

## Solución
Mueva el campo a estas subclases.

![Push-Down-Field- After.png](assets%2FPush-Down-Field-%20After.png)

## ¿Por qué refactorizar?
Aunque estaba previsto utilizar un campo de forma universal para todas las clases, en realidad el campo sólo se utiliza en algunas subclases. Esta situación puede producirse, por ejemplo, cuando las funciones previstas no dan resultado.

Esto también puede ocurrir debido a la extracción (o eliminación) de parte de la funcionalidad de las jerarquías de clases.

## Beneficios
* Mejora la coherencia interna de la clase. Un campo se encuentra donde realmente se utiliza.


* Al pasar a varias subclases simultáneamente, puede desarrollar los campos independientemente unos de otros. Esto crea duplicación de código, sí, así que empuje hacia abajo los campos sólo cuando usted realmente tiene la intención de utilizar los campos de diferentes maneras.

## Cómo refactorizar
1. Declare un campo en todas las subclases necesarias.

2. Elimine el campo de la superclase..