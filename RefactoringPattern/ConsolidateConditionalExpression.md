# Consolidar Expresión Condicional

## Problema

Tienes múltiples condicionales que conducen al mismo resultado o acción.

```kotlin
fun disabilityAmount(): Double {
    if (seniority < 2) {
        return 0.0
    }
    if (monthsDisabled > 12) {
        return 0.0
    }
    if (isPartTime) {
        return 0.0
    }
    // Calcular el monto de discapacidad.
    // ...
}

```

## Solución

Consolida todos estos condicionales en una sola expresión.

```kotlin
fun disabilityAmount(): Double {
    if (isNotEligibleForDisability()) {
        return 0.0
    }
    // Calcular el monto de discapacidad.
    // ...
    // Aquí debes colocar el cálculo real del monto de discapacidad
    // y devolver el resultado.
    // Por ejemplo:
    // return calculateDisabilityAmount()
    return 0.0 // Esto es solo un valor de ejemplo, debes reemplazarlo con el cálculo real.
}
```

## Por qué refactorizar

Tu código contiene muchos operadores alternativos que realizan acciones idénticas. No está claro por qué los operadores están divididos.

El propósito principal de la consolidación es extraer la condición a un método separado para mayor claridad.

## Beneficios

Elimina el código de flujo de control duplicado. La combinación de múltiples condicionales que tienen el mismo "destino" ayuda a mostrar que estás haciendo solo una verificación complicada que lleva a una acción.

Al consolidar todos los operadores, ahora puedes aislar esta expresión compleja en un nuevo método con un nombre que explique el propósito de la condición.

## Cómo refactorizar

Antes de refactorizar, asegúrate de que los condicionales no tengan ningún "efecto secundario" o que modifiquen algo en lugar de simplemente devolver valores. Los efectos secundarios pueden estar ocultos en el código ejecutado dentro del operador en sí, como cuando algo se agrega a una variable en función de los resultados de una condición.

1. Consolida los condicionales en una sola expresión usando `and` y `or`. Como regla general al consolidar:

    - Los condicionales anidados se unen usando `and`.

    - Los condicionales consecutivos se unen con `or`.

2. Realiza [Extract Method](../RefactoringPattern/ExtractMethod.md) en las condiciones del operador y da un nombre al método que refleje el propósito de la expresión

