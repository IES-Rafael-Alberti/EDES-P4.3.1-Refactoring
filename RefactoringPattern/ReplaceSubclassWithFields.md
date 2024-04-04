# Reemplazar Subclase con Campos

## Problema
Tienes subclases que difieren solo en sus métodos (que devuelven constantes).

![Reemplazar Delegación con Campos - Antes](https://refactoring.guru/images/refactoring/diagrams/Replace%20Subclass%20with%20Fields%20-%20Before.png?id=ea6525cc6b55e1a03fdb35def943c675)

## Solución
Reemplaza los métodos con campos en la clase padre y elimina las subclases.

![Reemplazar Delegación con Campos - Después](https://refactoring.guru/images/refactoring/diagrams/Replace%20Subclass%20with%20Fields%20-%20After.png?id=bd1b29687aa333b3adbeb2bfb3e78614)

## Por qué Refactorizar

A veces, el refactorizado es justo lo que necesitas para evitar el código de tipo.

En un caso así, una jerarquía de subclases puede ser diferente solo en los valores devueltos por métodos particulares. Estos métodos ni siquiera son el resultado de un cálculo, sino que están estrictamente definidos en los propios métodos o en los campos devueltos por los métodos. Para simplificar la arquitectura de la clase, esta jerarquía puede comprimirse en una sola clase que contenga uno o varios campos con los valores necesarios, según la situación.

Estos cambios pueden volverse necesarios después de mover una gran cantidad de funcionalidad de una jerarquía de clases a otro lugar. La jerarquía actual ya no es tan valiosa y sus subclases ahora son simplemente peso muerto.

## Beneficios

Simplifica la arquitectura del sistema. Crear subclases es excesivo si todo lo que quieres hacer es devolver diferentes valores en diferentes métodos.

## Cómo Refactorizar
1. Aplique **[Reemplazar constructor con método de fábrica](/RefactoringPattern/ReplaceConstructorWithFactoryMethod.md)** a las subclases.

2. Reemplace las llamadas al constructor de subclases con llamadas a métodos de fábrica de superclases.

3. En la superclase, declare campos para almacenar los valores de cada uno de los métodos de la subclase que devuelven valores constantes.

4. Cree un constructor de superclase protegido para inicializar los nuevos campos.

5. Cree o modifique los constructores de subclases existentes para que llamen al nuevo constructor de la clase principal y le pasen los valores relevantes.

6. Implemente cada método constante en la clase principal para que devuelva el valor del campo correspondiente. Luego elimine el método de la subclase.

7. Si el constructor de la subclase tiene funcionalidad adicional, use el **[método en línea](/RefactoringPattern/InlineMethod.md)** para incorporar el constructor al método de fábrica de la superclase.

8. Eliminar la subclase.


## Anti-refactorización
**[Reemplazar código de tipo con subclases](/RefactoringPattern/ReplaceTypeCodewithSubclasses.md)**