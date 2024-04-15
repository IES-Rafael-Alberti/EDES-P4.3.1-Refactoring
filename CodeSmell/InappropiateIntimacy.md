# Intimidad Inapropiada (Inappropriate Intimacy)

## Signos y síntomas

Una clase usa los campos y métodos internos de otra clase.

![](/CodeSmell/assets/inappropriate-intimacy-01.png)

## Razones del problema

Estate atento a las clases que pasan demasiado tiempo juntas. Las buenas clases deben saber lo menos posible unas de otras.
Clases asi son más fáciles de mantener y reutilizar.

## Tratamiento

- La solución más simple es usar Move Method y Move Field para mover partes de una clase a la clase en la que se usan esas partes. Pero esto funciona solo si la primera clase realmente no necesita estas partes.

![](/CodeSmell/assets/inappropriate-intimacy-02.png)

- Otra solución es usar Extract Class y Hide Delegate en la clase para hacer que las relaciones de código sean "oficiales".

- Si las clases son mutuamente interdependientes, debe usar cambiar la asociación bidireccional a unidireccional.

- Si esta "intimidad" es entre una subclase y la superclase, considera reemplazar esta delegación mediante la herencia.

![](/CodeSmell/assets/inappropriate-intimacy-03.png)

## Beneficios

- Mejora la organización del código.

- Simplifica el soporte y la reutilización de código.

