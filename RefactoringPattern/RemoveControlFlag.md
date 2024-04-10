# Eliminar la bandera de control

### Problema
Tienes una variable booleana que actúa como una bandera de control para múltiples expresiones booleanas.

### Solución
En lugar de la variable, utiliza `break`, `continue` y `return`

### Por qué Refactorizar
Las banderas de control se remontan a los días antiguos, cuando los "programadores adecuados" siempre tenían un punto de entrada para sus funciones (la línea de declaración de la función) y un punto de salida (al final de la función).

En los lenguajes de programación modernos, este estilo está obsoleto, ya que tenemos operadores especiales para modificar el flujo de control en bucles y otras construcciones complejas:

`break`: Detiene el bucle

`continue`: Detiene la ejecución de la rama actual del bucle y pasa a verificar las condiciones del bucle en la siguiente iteración

`return`: Detiene la ejecución de toda la función y devuelve su resultado si se proporciona en el operador

### Beneficios
El código de la bandera de control a menudo es mucho más pesado que el código escrito con operadores de flujo de control.

### Cómo Refactorizar
1. Encuentra la asignación de valor a la bandera de control que causa la salida del bucle o la iteración actual.

2. Reemplázalo con `break`, si se trata de una salida de un bucle; `continue`, si se trata de una salida de una iteración, o `return`, si necesitas devolver este valor desde la función.

3. Elimina el código restante y las comprobaciones asociadas con la bandera de control.