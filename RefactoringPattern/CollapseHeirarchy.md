# Colapsar Jerarquía (Collapse Heirarchy)

## Problema

Tienes una jerarquía de clases en la que la subclase es prácticamente la misma que su superclase.

![](https://refactoring.guru/images/refactoring/diagrams/Collapse%20Hierarchy%20-%20Before.png?id=e95d97b3a9d564fbdba5ec0b76748f88https://refactoring.guru/images/refactoring/diagrams/Move%20Field%20-%20Before.png?id=b58c81b01a0c4ef8659f92cc64fa51a)

## Solución

Une la subclase y la superclase.

![](https://refactoring.guru/images/refactoring/diagrams/Collapse%20Hierarchy%20-%20After.png?id=db86997e7b68eaac829168048cd02a8bhttps://refactoring.guru/images/refactoring/diagrams/Move%20Field%20-%20After.png?id=d7c21af94ec9df17575373bae745e96)

## Beneficios

* La complejidad del programa se reduce. Menos clases significa menos cosas que tener en tu cabeza y menis partes movibles rompibles de las que preocuparse de cara a un futuro cambio en el código.
* Naegar a través del código es más facil cuando los métodos están definidos en una clase con anterioridad. No necesitas peinar la jerarquía en busca de un método en particular.

## Cuando no usar

* ¿Tiene la jerarquía de clases que estás refactorizando más de una subclase? En el caso positivo, después de que la refactorización esté completa, las subclases restantes deben convertirse en herederas de la clase donde se ha colapsado la jerarquía.
* Ten en cuenta que esto puede llevar a violaciones del *Principio de sustitución de Liskov*. Por ejemplo, si tu programa simula una red de transporte de u8na ciudad y accidentalmente colapsas la superclase `Transporte` dentro de la subclase `Coche`, entonces la clase `Avión` puede convertirse en heredera de `Coche`. ¡Ups!

## Como refactorizar

1. Elige que clase es más facil de borrar: la superclase o la subclase.
2. Usa [Levantar Campo](https://refactoring.guru/es/pull-up-field) y [Levantar Método](https://refactoring.guru/es/pull-up-method) si decides ocuparte de la cubclase. Si eliges eliminar la superclase, utiliza [Presionar Campo](https://refactoring.guru/es/push-down-field) y [Método de Presión](https://refactoring.guru/es/push-down-method).
3. Reemplaza todos los usos de la clase que estás borrando con los campos y métodos que van a ser migrados. A menudo esté será el método para crear clases, escribir variables y parámetros y documentación en comentarios de código.
4. Borra cualquier clase que haya quedado vacía.
