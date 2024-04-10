# Clases Alternativas con Diferentes Interfaces

## Signos y Síntomas

Dos clases cumplen las mismas funciones, pero sus métodos tienen nombres distintos.

![](../CodeSmell/assets/alternative-classes-with-different-interfaces-01.png)

## Razones del Problema

El programador que creo una de las clases probablemente no sabía que había una clase funcionalmente equivalente.

## Tratamiento

Intenta poner la interfaz de las clases en términos de un denominador común:
- [Renombra los métodos](../RefactoringPattern/RenameMethod.md) para hacerlos idénticos en todas las clases alternativas.
* [Mover Método](../RefactoringPattern/MoveMethod.md), [Añadir Parámetro](../RefactoringPattern/AddParameter.md) y [Parametrizar Método](../RefactoringPattern/ParameterizeMethod.md) para hacer que la firma y la implementación de los métodos sean iguales.
- Si solo parte de la funcionalidad de las clases está duplicada, intenta usar [Extraer Superclase](../RefactoringPattern/ExtractSuperclass.md). En este caso, las clases existentes se convertirán en subclases.
* Después de haber determinado qué método de tratamiento usar y haberlo implementado, deberías ser capaz de eliminar una de las clases.

## Recompensa

- Te deshaces del código duplicado innecesario, haciendo que el código resultante sea menos voluminoso.
* El código se vuelve más legible y comprensible (ya no tienes que adivinar la razón de la creación de una segunda clase que realiza exactamente las mismas funciones que la primera).
![](../CodeSmell/assets/alternative-classes-with-different-interfaces-02.png)

## Cuando Ignorarlo

A veces, fusionar clases es imposible o tan difícil que resulta inútil. Un ejemplo es cuando las clases alternativas están en diferentes bibliotecas que cada una tiene su propia versión de la clase.