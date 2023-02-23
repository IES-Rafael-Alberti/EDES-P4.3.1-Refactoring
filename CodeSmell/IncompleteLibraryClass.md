# Clase de biblioteca incompleta

## Signos y síntomas

Llega un punto donde las bibliotecas dejan de satisfacer las necesidades de los ususarios. La unica solución al problema seria cambiar la biblioteca, eso a veces es imposible ya que la biblioteca es solo de lectura.

![Alt text](https://refactoring.guru/images/refactoring/content/smells/incomplete-library-class-01.png?id%3Dca51f740f7fd39b7de1430b64cae9f8c)

## Razones del problema

El autor del la biblioteca no crea las funciones necesarias o se niega a hacerlo.

## Tratamiento

· Para introducir metodos en una clase de biblioteca, utilice  Introduce Foreign Method

· Para grandes cambios en una biblioteca de clases, use Introduce Local Extension .

## Saldar

Reduce la duplicación de código (en lugar de crear su propia biblioteca desde cero, aún puede aprovechar una existente).

![Alt text](https://refactoring.guru/images/refactoring/content/smells/incomplete-library-class-02.png)

## Cuándo ignorar

Ampliar una biblioteca puede generar trabajo adicional si los cambios en la biblioteca implican cambios en el código.
