# Intimidad Inapropiada (Inappropriate Intimacy)

## Signos y síntomas

Una clase usa los campos y métodos internos de otra clase.

![](/CodeSmell/assets/inappropriate-intimacy-01.png)

## Razones del problema

Estate atento a las clases que se usan muchas veces juntas. Una clase bien hecha debe saber lo menos posible de las otras en la medida de lo posible. Clases así son más fáciles de mantener y reutilizar.

## Tratamiento

- La solución más simple es usar Move Method y Move Field para mover partes de una clase a la clase en la que estas partes son usadas. Pero esto solo funciona si realmente la primera clase no lo necesita.

![](/CodeSmell/assets/inappropriate-intimacy-02.png)

- Otra solución es usar Extract Class y Hide Delegate en la clase para hacer  relaciones de código que sean "oficiales".

- Si las clases son mutuamente interdependientes, deberías usar cambiar la asociación bidireccional a unidireccional.

- Si esta "intimidad" es entre una subclase y su superclase, considera reemplazar delegación mediante la herencia.

![](/CodeSmell/assets/inappropriate-intimacy-03.png)

## Beneficios

- Mejora la organización del código.

- Simplifica el mantenimiento y la reutilización de código.

