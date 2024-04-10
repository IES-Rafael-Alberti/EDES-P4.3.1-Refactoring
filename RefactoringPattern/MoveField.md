# Movimiento de Campos (Move Field)

## Problema

Un campo se usa más en otra clase que en su propia clase.

![Move Field - Before.png](assets%2FMove%20Field%20-%20Before.png)

## Solución

Crea un campo en una nueva clase para redirigir a todos los usuarios del viejo campo al nuevo.
![Move Field - After.png](assets%2FMove%20Field%20-%20After.png)

## Por qué refactorizar

A menudo los campos se mueven como parte de la [ExtractClass.md](ExtractClass.md). Decidir a que clase dejar el campo puede ser dificil. Aquí está nuestra regla: **pon un campo en el mismo lugar que los métodos que lo usan**(o donde más de estos métodos haya).

Esta regla te ayudará en otros casos cuando un campo está simplemente localizado en el lugar incorrecto.

## Como refactorizar

1. Si el campo es público, refactorizar será mucho más fácil si haces lo campos privados y le das métodos de acceso públicos(para hacer esto, puedes usar[Campo encapsulado](https://refactoring.guru/es/encapsulate-field)).

2. Crear el mismo campo con métodos de acceso en la clase destinataria.

3. Decide como te referirás a la clase destinataria. Puede que ya tengas un campo o método que devuelve el objeto apropiado; si no, tendrás que escribir un nuevo método o campo que almacene el objeto de la clase destinataria.

4. Reemplaza todas las referencias al viejo campo con las llamadas apropiadas a métodos en la clase destinataria. Si el campo no es privado, encárgate de que este se encuentre en las superclases y las subclases.

5. Borra el campo en la clase original.


