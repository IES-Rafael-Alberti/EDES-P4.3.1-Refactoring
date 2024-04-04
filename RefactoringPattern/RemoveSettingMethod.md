# Eliminar método de configuración

## Problema

El valor de un campo debe establecerse solo cuando se crea, no en ningún momento después de eso. En el caso de kotlin el lenguaje ya nos crea los métodos getter y setter, por lo tanto, no es necesario crear un método.

![](./assets/RemoveSettingMethod-Before.png)

## Solución

Simplemente, elimina los métodos que establecen el valor del campo.

![](./assets/RemoveSettingMethod-After.png)

## Por qué refactorizar

Quieres evitar cualquier cambio en el valor de un campo.

## Cómo refactorizar

1. El valor de un campo debe poder cambiarse solo en el constructor. Si el constructor no contiene un parámetro para establecer el valor, agrega uno.
2. Encuentra todas las llamadas de setter.

   * Si una llamada de setter se encuentra justo después de una llamada para el constructor de la clase actual, mueve su argumento a la llamada del constructor y elimina el setter.
   * Reemplaza las llamadas de setter en el constructor con acceso directo al campo.
3. Elimina el setter.
