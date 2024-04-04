# Reemplazar Parámetro por Llamada a Método

## Problema

Llamar a un método y pasar sus resultados como parámetros a otro método en vez de que ese método llame directamente a la consulta.

```
val precioBase: Int = cantidad * precioArticulo
val descuentoEstacional: Double = obtenerDescuentoEstacional()
val cuotas: Double = obtenerCuotas()
val precioFinal: Double = precioDescontado(precioBase, descuentoEstacional, cuotas)
```

## Solución

En vez de pasar el valor a través de un parámetro, intente colocar una llamada de consulta dentro del cuerpo del método.

```
val precioBase: Int = cantidad * precioArticulo
val precioFinal: Double = precioDescontado(precioBase)
```

## Por qué refactorizar

Una larga lista de parámetros es difícil de entender. Además, las llamadas a tales métodos a menudo parecen una serie de 
cascadas, con cálculos de valores sinuosos y emocionantes que son difíciles de navegar, pero que deben pasarse al método. 
Entonces, si se puede calcular el valor de un parámetro con la ayuda de un método, hágalo dentro del método en sí y 
deshágase del parámetro.

## Beneficios

Nos deshacemos de parámetros innecesarios y simplificamos las llamadas a los métodos. Dichos parámetros a menudo se 
crean no para el proyecto tal como está ahora, sino pensando en futuras necesidades que nunca llegarán.

## Desventajas

Es posible que necesite el parámetro mañana para otras necesidades, lo que lo obligaría a reescribir el método.

## Cómo refactorizar

1. Asegúrese de que el código que obtiene el valor no use parámetros del método actual, ya que no estarán disponibles 
desde otro método. Si es así, mover el código no es posible.

2. Si el código relevante es más complicado que una sola llamada de método o función, use [Extraer Método](./ExtractMethod.md) para aislar 
este código en un nuevo método y hacer que la llamada sea simple.

3. En el código del método principal, reemplace todas las referencias al parámetro que se está reemplazando con llamadas 
al método que obtiene el valor.

4. Use [Eliminar Parámetro](./RemoveParameter.md) para eliminar el parámetro que ya no se usa.
