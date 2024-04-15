# Intimidad Inapropiada (Inappropriate Intimacy)

## Signos y síntomas

Una clase usa los campos y métodos internos de otra clase.

![](/CodeSmell/assets/inappropriate-intimacy-01.png)

## Razones del problema

Estate atento a las clases que se usan muchas veces juntas. Una clase bien hecha debe saber lo menos posible de las otras en la medida de lo posible. Clases así son más fáciles de mantener y reutilizar.

## Tratamiento

- La solución más simple es usar [Move Method](/RefactoringPattern/MoveMethod.md) y [Movimiento de Campos](//RefactoringPattern/MoveField.md) para mover partes de una clase a la clase en la que estas partes son usadas. Pero esto solo funciona si realmente la primera clase no lo necesita.

![](/CodeSmell/assets/inappropriate-intimacy-02.png)

- Otra solución es usar [Extracción de clases](/RefactoringPattern/ExtractClass.md) y [Ocultar Delegado](/RefactoringPattern/HideDelegate.md) en la clase para hacer  relaciones de código que sean "oficiales".

- Si las clases son mutuamente interdependientes, deberías usar [Change Bidirectional Association to Unidirectional](/RefactoringPattern/changeBidirectionalAssociationToUnidirectional.md).

- Si esta "intimidad" es entre una subclase y su superclase, considera [Replace Delegation with Inheritance](/RefactoringPattern/ReplaceDelegationwithInheritance.md).

![](/CodeSmell/assets/inappropriate-intimacy-03.png)

## Beneficios

- Mejora la organización del código.

- Simplifica el mantenimiento y la reutilización de código.

