# Inline Temp

## Problema

Tienes Una variable temporal a la que se le asigna el resultado de una expresión simple y nada más.

```kotlin
fun hasDiscount(order: Order) : Boolean {
    val basePrice = order.basePrice()
    return basePrice > 1000
}
```

## Solución

Reemplaza las referencias a la variable con la misma expresión.

```kotlin
fun hasDiscount(order: Order) : Boolean {
    return order.basePrice() > 1000
}
```

## Por qué refactorizar

Las variables locales en línea casi siempre se usan como parte de [Reemplazar Temp con una Consulta](../RefactoringPattern/ReplaceTempwithQuery.md)
o para allanar el camino para [Método de Extracción](../RefactoringPattern/ExtractMethod.md).

## Beneficios

Esta técnica de refactorización por sí misma ofrece casi ningún beneficio. Sin embargo, si la variable se le asigna el resultado de un método, puedes mejorar marginalmente la legibilidad del programa al deshacerte de la variable innecesaria.

## Inconvenientes

A veces, se utilizan temporales aparentemente inútiles para almacenar en caché el resultado de una operación costosa
que se reutiliza varias veces. Por lo tanto, antes de usar esta técnica de refactorización, asegúrese de que la simplicidad
no se logre a costa del rendimiento.

## Como refactorizar

1. Encuentra todos los lugares que usan la variable. En lugar de la variable, utilice la expresión que le había sido 
asignada.
2. Elimine la declaración de la variable y su línea de asignación.
