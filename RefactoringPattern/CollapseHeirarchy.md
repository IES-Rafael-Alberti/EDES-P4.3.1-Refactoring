# Colapsar Jerarquía (Collapse Heirarchy)

## Problema

Tienes una jerarquía de clases en la que la subclase es prácticamente la misma que su superclase.

![](./assets/Collapse%20Hierarchy%20-%20Before.png)

## Solución

Une la subclase y la superclase.

![](./assets/Collapse%20Hierarchy%20-%20After.png)

## Por qué refactorizar.

Tu programa ha crecido con el paso del tiempo, y la subclase y la superclase se han convertido en prácticamente lo mismo. Eliminas una característica de la subclase, se añade un método a la superclase, y acabas teniendo dos clases similares 

## Beneficios

* La complejidad del programa se reduce. Menos clases significa menos cosas que tener en tu cabeza y menos partes movibles rompibles de las que preocuparse de cara a un futuro cambio en el código.
* Navegar a través del código es más fácil cuando los métodos están definidos en una clase con anterioridad. No necesitas peinar la jerarquía en busca de un método en particular.

## Cuándo no usar

* ¿Tiene la jerarquía de clases que estás refactorizando más de una subclase? En ese caso, después de que la refactorización esté completa, las subclases restantes deben convertirse en herederas de la clase donde se ha colapsado la jerarquía.
* Ten en cuenta que esto puede llevar a violaciones del *Principio de sustitución de Liskov*. Por ejemplo, si tu programa simula una red de transporte de una ciudad y accidentalmente colapsas la superclase `Transporte` dentro de la subclase `Coche`, entonces la clase `Avión` puede convertirse en heredera de `Coche`. ¡Ups!

## Cómo refactorizar

1. Elige qué clase es más fácil de borrar: la superclase o la subclase.
2. Usa [Levantar Campo](./PullUpField.md) y [Levantar Método](./PullUpMethod.md) si decides ocuparte de la subclase. Si eliges eliminar la superclase, utiliza [Presionar Campo](./PushDownField.md) y [Método de Presión](./PushDownMethod.md).
3. Reemplaza todos los usos de la clase que estás borrando con los campos y métodos que van a ser migrados. A menudo esté será el método para crear clases, escribir variables y parámetros y documentación en comentarios de código.
4. Borra cualquier clase que haya quedado vacía.
