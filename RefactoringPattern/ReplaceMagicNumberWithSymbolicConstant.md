# Reemplazar el número mágico con una constante simbólica (Replace Magic Number with symbolic constant)

## Problema 
Su código utiliza un número que tiene un significado determinado.

```kotlin
 fun potentialEnergy(mass: Double, height: Double): Double {
    return mass * height * 9.81
}
```

## Solución
Reemplace este número con una constante que tenga un nombre legible por humanos que explique el significado del número.

```kotlin
val GRAVITATIONAL_CONSTANT: Double = 9.81

fun potentialEnergy(mass: Double, height: Double): Double {
    return mass * height * GRAVITATIONAL_CONSTANT
}
``` 

## Por qué refactorizar
Un número mágico es un valor numérico que se encuentra en la fuente pero que no tiene un significado obvio ( no está asignado a una constante ). Este "antipatrón" dificulta la comprensión del programa y la refactorización del código.

Aún surgen más dificultades cuando es necesario cambiar este número mágico. Buscar y reemplazar no funcionará para esto: el mismo número puede usarse para diferentes propósitos en diferentes lugares, lo que significa que tendrá que verificar cada línea de código que use este número.

## Beneficios
- La constante simbólica puede servir como documentación viva del significado de su valor.

- Es mucho más fácil cambiar el valor de una constante que buscar este número en todo el código base, sin el riesgo de cambiar accidentalmente el mismo número utilizado en otro lugar para un propósito diferente.

- Reduzca el uso duplicado de un número o cadena en el código. Esto es especialmente importante cuando el valor es complicado y largo (como 3.14159 o 0xCAFEBABE).

## Bueno saber
**No todos los números son mágicos.**
Si el propósito de un número es obvio, no es necesario reemplazarlo. Un ejemplo clásico es:

```kotlin
for (i in 0 until count) {
    // Código a ejecutar en cada iteración
}
``` 

**Alternativas**
1. A veces, un número mágico se puede reemplazar con llamadas a métodos. Por ejemplo, si tiene un número mágico que indica la cantidad de elementos de una colección, no necesita usarlo para verificar el último elemento de la colección. En su lugar, utilice el método estándar para obtener la longitud de la colección.
2. A veces se utilizan números mágicos como código tipográfico. Supongamos que tiene dos tipos de usuarios y utiliza un campo numérico en una clase para especificar cuál es cuál: los administradores 1 y los usuarios comunes 2.

En este caso, debe utilizar uno de los métodos de refactorización para evitar escribir código:

- **[Reemplazar código de tipo con clase](/RefactoringPattern/ReplaceTypeCodeWithClass.md)**

- **[Reemplazar código de tipo con subclases](/RefactoringPattern/ReplaceTypeCodewithSubclasses.md)**

- **[Reemplazar código de tipo con estado/estrategia](/RefactoringPattern/ReplaceTypeCodeWithStateStrategy.md)**


## Cómo refactorizar
1. Declara una constante y asígnale el valor del número mágico.

2. Encuentra todas las menciones del número mágico.

3. Para cada uno de los números que encuentres, vuelve a verificar que el número mágico en este caso particular corresponda al propósito de la constante. En caso afirmativo, reemplace el número con su constante. Este es un paso importante, ya que el mismo número puede significar cosas absolutamente diferentes (y reemplazarse con constantes diferentes, según sea el caso).