# Grupos de datos (Data Clumps)

## Signos y síntomas

A veces, diferentes partes del código contienen grupos idénticos de variables (como parámetros para conectarse a una base de datos). Estos grupos deben convertirse en sus propias clases.

![](./assets/data-clumps-01.png)

## Razones del problema

A menudo, estos grupos de datos se deben a una estructura deficiente del programa o "programación de copiar y pegar".

Si desea asegurarse de que algunos datos sean o no un grupo de datos, simplemente elimine uno de los valores de datos y vea si los otros valores aún tienen sentido. Si este no es el caso, es una buena señal de que este grupo de variables debe combinarse en un objeto.

## Tratamiento

- Si los datos repetidos comprenden los campos de una clase, use [Extraer clase](../RefactoringPattern/ExtractClass.md) para mover los campos a su propia clase.

- Si se pasan los mismos grupos de datos en los parámetros de los métodos, use [Introducir objeto de parámetro](../RefactoringPattern/IntroduceParameterObject.md) para establecerlos como una clase.

- Si algunos de los datos se pasan a otros métodos, piense en pasar todo el objeto de datos al método en lugar de solo campos individuales. [Preservar todo el objeto](../RefactoringPattern/PreserveWholeObject.md) ayudará con esto.

- Mire el código usado por estos campos. Puede ser una buena idea mover este código a una clase de datos.

![](./assets/data-clumps-02.png)

## Saldar

- Mejora la comprensión y organización del código. Las operaciones en datos particulares ahora se recopilan en un solo lugar, en lugar de hacerlo al azar en todo el código.

- Reduce el tamaño del código.

![](./assets/data-clumps-03.png)

## Cuándo ignorar

Pasar un objeto completo en los parámetros de un método, en lugar de pasar solo sus valores (tipos primitivos), puede crear una dependencia no deseada entre las dos clases.