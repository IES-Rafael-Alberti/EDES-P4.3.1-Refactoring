# Ocultar delegado (hide delegate)

## Problema

El cliente obtiene el objeto B de un campo o método del objeto А. Luego, el cliente llama a un método del objeto B.

![](./assets/Hide%20Delegate%20-%20Before.png)

## Solución

Cree un nuevo método en la clase A que delegue la llamada al objeto B. Ahora el cliente no conoce ni depende de la clase B.

![](./assets/Hide%20Delegate%20-%20After.png)

## Por qué Refactorizar

* El *servidor* es el objeto al que el cliente tiene acceso directo.
* *Delegado* es el objeto final que contiene la funcionalidad que necesita el cliente.

Una cadena de llamadas aparece cuando un cliente solicita un objeto de otro objeto, luego el segundo objeto solicita otro, y así sucesivamente. Estas secuencias de llamadas involucran al cliente en la navegación a lo largo de la estructura de clases. Cualquier cambio en estas interrelaciones requerirá cambios en el lado del cliente.

## Beneficios

Oculta la delegación del cliente. Cuanto menos necesite saber el código del cliente sobre los detalles de las relaciones entre los objetos, más fácil será realizar cambios en su programa.

## Inconvenientes

Si necesita crear una cantidad excesiva de métodos de delegación, la clase de servidor corre el riesgo de convertirse en un intermediario innecesario, lo que lleva a un exceso de [intermediarios (Middle Man)](./MiddleMan.md)

## Cómo refactorizar

1. Para cada método de la clase de delegado llamado por el cliente, cree un método en la clase de servidor que delegue la llamada a la clase de delegado.
2. Cambie el código del cliente para que llame a los métodos de la clase de servidor.
3. Si sus cambios liberan al cliente de la necesidad de la clase de delegado, puede eliminar el método de acceso a la clase de delegado de la clase de servidor (el método que se usó originalmente para obtener la clase de delegado).
