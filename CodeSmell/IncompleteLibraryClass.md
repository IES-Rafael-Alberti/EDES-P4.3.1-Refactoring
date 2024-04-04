# Incomplete Library Class

## Signos y síntomas

Tarde o temprano, las [**bibliotecas**](https://es.wikipedia.org/wiki/Biblioteca_(inform%C3%A1tica)) dejan de satisfacer las necesidades de los usuarios. 
La única solución al problema, cambiar la biblioteca, a menudo es imposible ya que la biblioteca es de solo lectura.

![](https://refactoring.guru/images/refactoring/content/smells/incomplete-library-class-01.png)

## Razones del problema
El autor de la biblioteca no ha proporcionado las funciones que necesita o se ha negado a implementarlas.

## Tratamiento
- Para introducir algunos métodos en una clase de biblioteca, utilice [Introduce Método extranjero](../RefactoringPattern/IntroduceForeignMethod.md) .
- Para grandes cambios en una biblioteca de clases, use [Introduce Extensión Local](../RefactoringPattern/IntroduceLocalExtension.md) .

## Beneficios

Reduce la duplicación de código (en lugar de crear su propia biblioteca desde cero, aún puede aprovechar una existente).

![](https://refactoring.guru/images/refactoring/content/smells/incomplete-library-class-02.png)

## Cuándo ignorar
Ampliar una biblioteca puede generar trabajo adicional si los cambios en la biblioteca implican cambios en el código.
