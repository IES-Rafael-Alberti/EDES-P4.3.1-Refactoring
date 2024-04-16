# Método de extracción

## Problema

Tienes un fragmento de código que se puede agrupar.

```Kotlin
fun printOwing() {
    printBanner()

    // print details
    println("name: $name")
    println("amount: ${getOutstanding()}")
}
```

## Solución

Mueva este código a un nuevo método (o función) independiente y reemplace el código antiguo por una llamada al método.

```Kotlin
fun printOwing() {
    printBanner()
    printDetails(getOutstanding())
}

fun printDetails(outstanding: Int) {
    println("name: $name")
    println("amount: $outstanding")
}
```

## Porqué Refactorizar

Cuantas más líneas tenga un método, más difícil es averiguar qué hace el método. Esta es la principal razón de porque refactorizar.

Además de eliminar las asperezas en el código, la extracción de métodos también es un paso en muchos otros enfoques de la refactorización.

## Beneficios

* ¡Código más legible! Asegúrate de darle un nombre que describa el propósito del método: `createOrder()`, `renderCustomerInfo()`, etc.


* Menos código duplicado. A menudo, el código encontrado en un método se puede reutilizar en otros lugares del programa. Por lo tanto, puedes reemplazar duplicados con llamadas a tú nuevo método.


* Aísla partes independientes del código, lo que significa que los errores son menos probables (por ejemplo, si se modifica la variable equivocada).

## Cómo refactorizar

1. Crea un nuevo método y nómbralo de forma que describa su propósito de manera evidente.


2. Copia el fragmento de código útil en el nuevo método. Elimina el fragmento de su ubicación anterior y pon una llamada al nuevo método en su lugar.

     Busca todas las variables utilizadas en el fragmento de código. Si son declaradas dentro del fragmento y no se usan fuera de él, simplemente déjalos sin cambios: se convertirán en variables locales para el nuevo método.


3. Si las variables están declaradas antes del código que estás extrayendo, deberá pasar estas variables mediante parámetros al nuevo método para usar los valores contenidos anteriormente en estas. A veces es más fácil deshacerse de estas variables recurriendo a [Reemplazar variables temporales con consultas](./ReplaceTempwithQuery.md).


4. Si ves que una variable local cambia de alguna manera en tu código extraído, esto puede significar que el valor modificado será necesario después en el método principal. ¡Revísalo de nuevo! Y si este es el caso, devuelve el valor de esta variable al método principal para que todo siga funcionando.
