# Cambiar referencia a valor

## Problema

Tiene un objeto de referencia que es demasiado pequeño y que se modifica con poca frecuencia para justificar la gestión de su ciclo de vida.

![](./assets/ChangeReferenceToValue-Before.png)

## Solución

Conviertelo en un objeto de valor.



![](./assets/ChangeReferenceToValue-After.png)

## Por qué refactorizar

La inspiración para pasar de una referencia a un valor puede surgir del inconveniente de trabajar con la referencia. Las referencias requieren gestión por su parte:

- Siempre requieren solicitar al almacén el objeto necesario.

- Puede resultar incómodo trabajar con las referencias en la memoria.

- Trabajar con referencias es particularmente difícil, en comparación con valores, en sistemas distribuidos y paralelos.

Los valores son especialmente útiles si prefiere tener objetos inmutables que objetos cuyo estado pueda cambiar durante su vida.

## Beneficios

- Una propiedad importante de los objetos es que deben ser inmutables. Se debe recibir el mismo resultado para cada consulta que devuelva un valor de objeto. Si esto es cierto, no surgen problemas si hay muchos objetos que representan lo mismo.

- Los valores son mucho más fáciles de implementar.

## Desventajas

Si un valor se puede cambiar, asegúrese de que si algún objeto cambia, los valores de todos los demás objetos que representan la misma entidad se actualicen. Esto es tan engorroso que es más fácil crear una referencia para este propósito.

## Cómo refactorizar

1. Haz que el objeto sea inmutable. El objeto no debe tener definidores u otros métodos que cambien su estado y datos ( **[Eliminar método de configuración](/RefactoringPattern/RemoveSettingMethod.md)** puede ayudar aquí). El único lugar donde se deben asignar datos a los campos de un objeto de valor es un constructor.

2. Cree un método de comparación para poder comparar dos valores.

3. Compruebe si puede eliminar el método de fábrica y hacer público el constructor del objeto.


## Anti-refactorización
[Cambiar valor a referencia](/RefactoringPattern/ChangeValueToReference.md)
