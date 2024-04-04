# Descomponer condicional (Descompose Conditional)

## Problema
Tienes un bloque condicional complejo (`if-then`/`else` o `switch`).

```kotlin
if (date.before(SUMMER_START) || date.after(SUMMER_END)) {
    charge = quantity * winterRate + winterServiceCharge
} else {
    charge = quantity * summerRate
}
```

## Solución
Descomponga las partes complicadas del condicional en métodos separados: la condición `then` y `else`.
```kotlin
if (isSummer(date)) {
    charge = summerCharge(quantity)
} else {
    charge = winterCharge(quantity)
}
```

## Por qué refactorizar
Cuanto más largo sea un fragmento de código, más dificil de entender será. Cuando el código está lleno de condicionales la dificultad se incrementa:
- Mientras intentas entender que hace el código del bloque `then`, ya has olvidado cual era la condición.
- Y mientras intentas entender el código del bloque `else`, ya habrás olvidado lo que hacía el código del bloque `then`.

## Beneficios
- Al extraer la condición a un método con un nombre descriptivo, le facilitarás la vida a la persona que después tenga que mantener el código (como tú, ¡dentro de dos meses!).
- Esta técnica de refactorización también se puede aplicar a expresiones simples en los condicionales. La cadena isSalaryDay() es mucho más clara y más descriptiva que el código para comparar fechas.

## Cómo refactorizar
1. Extrae las condiciones a un método separado usando **Extraer método**.
2. Repite el proceso para los bloques `then` y `else`.


## Elimina el olor
Enlace a [Método largo](/CodeSmell/LongMethod.md)