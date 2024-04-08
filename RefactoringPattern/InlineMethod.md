# Método en linea

## Problema

Cuando el cuerpo de un método es más obvio que el propio método, utilice esta técnica.

```Kotlin
class EntregaDePizza {
    fun obtenerCalificacion(): Int {
        return if (masDeCincoEntregasTardias()) 2 else 1
    }

    fun masDeCincoEntregasTardias(): Boolean {
        return cantidadDeEntregasTardias > 5
    }
}
```

## Solución

Reemplace las llamadas al método por el contenido del método y elimine el propio método.

```Kotlin
class EntregaDePizza {
  fun obtenerCalificacion(): Int {
    return if (cantidadDeEntregasTardias > 5) 2 else 1
  }
}
```

## ¿Por qué Refactorizar?

*Un método simplemente delega en otro método. En sí misma, esta delegación no es un problema. Pero cuando hay muchos métodos de este tipo, se convierten en una maraña confusa que es difícil de resolver.<br><br>A menudo, los métodos no son demasiado cortos originalmente, pero se vuelven así a medida que se realizan cambios en el programa. Así que no tengas vergüenza de deshacerte de los métodos que han sobrevivido a su uso.

## Beneficiós

Al minimizar el número de métodos innecesarios, el código es más sencillo.

## Cómo refactorizar

1. Asegúrese de que el método no se redefina en subclases. Si se redefine el método, absténgase de esta técnica.

3. Busque todas las llamadas al método. Reemplace estas llamadas por el contenido del método.

5. Elimine el método.
