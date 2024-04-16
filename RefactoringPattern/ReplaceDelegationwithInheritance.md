# Replace Delegation with Inheritance

## Problema
Una clase contiene muchos métodos simples que delega todos los métodos de otra clase.

![Reemplazar Delegación con Herencia - Antes](/RefactoringPattern/assets/Replace Delegation with Inheritance-01.png)

## Solución
Hacer que la clase sea una herencia delegada, lo que hace que delegar los métodos sea innecesario.

![Reemplazar Delegación con Herencia - Después](/RefactoringPattern/assets/Replace Delegation with Inheritance-02.png)

## Por qué Refactorizar

La delegación es un enfoque más flexible que la herencia, ya que permite cambiar cómo se implementa la delegación y 
colocar allí también otras clases. No obstante, la delegación deja de ser beneficiosa si se delegan acciones solo a una clase y a todos sus métodos públicos.

En ese caso, si reemplaza la delegación con la herencia, limpia la clase de una gran cantidad de métodos de delegación
y se ahorra la necesidad de crearlos para cada nuevo método de clase delegado.

## Beneficios

Reduce la longitud del código. Los métodos de delegación ya no son necesarios.

## Cuándo no usarlo

- No uses esta técnica si la clase delega solo de una parte de los métodos públicos de la clase delegada. Hacerlo, violaría el principio de sustitución de Liskov.

- Esta técnica solo se puede utilizar si la clase aún no tiene padres.

## Cómo Refactorizar

1. Hacer que la clase sea una subclase de la clase delegada.

2. Colocar el objeto actual en un campo que contenga una referencia al objeto delegado.

3. Eliminar los métodos con delegación simple uno por uno. Si sus nombres son diferentes, usa la técnica
[Renombrar Método](./RenameMethod.md) 
para darles a todos un nombre diferente.

4. Reemplaza todas las referencias al campo delegado con referencias al objeto actual.

5. Elimina el campo delegado.