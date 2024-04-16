# Extraer variable

## Problema
Tienes una expresión que es difícil de entender.

## Solución
Coloca el resultado de la expresión o sus partes en variables separadas que se expliquen por sí mismas.

- Antes
 ```kotlin
fun renderBanner() {
    if (platform.toUpperCase().indexOf("MAC") > -1 && browser.toUpperCase().indexOf("IE") > -1 &&
        wasInitialized() && resize > 0
    ) {
        // do something
    }
}
 ```

- Después

```kotlin
fun renderBanner() {
    val isMacOs = platform.toUpperCase().contains("MAC")
    val isIE = browser.toUpperCase().contains("IE")
    val wasResized = resize > 0

    if (isMacOs && isIE && wasInitialized() && wasResized) {
        // do something
    }
}
```

## Por qué refactorizar
La principal razón para extraer variables es para que una expresión compleja sea más comprensible, dividiéndola en partes intermedias. Esto podría aplicarse cuando:

- La condición de un operador```if()```  o un parte de un operador ```? (Null Safety)```: operadores basados en lenguajes de C.

- Una expresión aritmética larga sin resultados intermedios.

- Líneas largas de varias partes.

Extraer una variable puede ser el primer paso para realizar el [método de extracción](./ExtractMethod.md) si ves que la expresión extraída se usa en otros lugares de su código.

## Beneficios

¡Código más legible! Trata de dar a las variables extraídas nombres adecuados que anuncien claramente su propósito. Más legibilidad, menos comentarios cortos. Usa nombres como ```valorImpuestoCliente```, ```tasaDesempleoCiudad```, ```stringSaludoCliente``` , etc.

## Inconvenientes

- Más variables están presentes en su código. Pero esto es contrarrestado por la facilidad de lectura del código.


- Al refactorizar expresiones condicionales, recuerda que lo más probable es que el compilador las optimice para minimizar la cantidad de cálculos necesarios para establecer el valor del resultado. Digamos que tienes la siguiente expresión ```if (a() || b()) ....``` El programa no llamará al método ```b``` si el método ```a``` devuelve ```true``` porque el valor resultante seguirá siendo ```true```, sin importar qué valor devuelva ```b```.

Sin embargo, si extraes las partes de esta expresión en variables, siempre se llamará a ambos métodos, lo que podría perjudicar el rendimiento del programa, especialmente si estos métodos realizan un trabajo pesado.

## Cómo refactorizar


1. Inserta una nueva línea antes de la expresión destacada y declara una nueva variable ahí. Asigna parte de la expresión compleja a esta variable.


2. Reemplaza esa parte de la expresión con la nueva variable.


3. Repite el proceso para todas las partes complejas de la expresión.
