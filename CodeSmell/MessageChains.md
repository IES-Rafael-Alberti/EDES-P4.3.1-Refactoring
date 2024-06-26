# Cadena de Mensajes

## Signos y Síntomas
Si en el código, podemos ver una serie de llamadas que se asemejan a `a.b().c().d()`

![](./assets/message-chains-01.png)

## Razones del Problema
Una cadena de mensajes ocurre cuando un cliente solícita otro objeto, ese objeto solicita otro más, y así sucesivamente. Estas cadenas significan que el cliente depende de la navegación a lo largo de la estructura de clases. Cualquier cambio en estas relaciones requiere modificar el cliente.

## Tratamiento
- Para eliminar una cadena de mensajes, usar [Ocultar Delegado](../RefactoringPattern/HideDelegate.md).
* A veces es mejor pensar por qué se usa el objeto final. Tal vez tendría sentido usar el [Método de extracción](../RefactoringPattern/ExtractMethod.md) para esta funcionalidad y moverlo al comienzo de la cadena, usando el [Método de movimiento](../RefactoringPattern/MoveMethod.md).

![](./assets/message-chains-02.png)

## Recompensa
- Reduce las dependencias entre las clases de una cadena.
* Reduce la cantidad de código inflado.

![](./assets/message-chains-03.png)

## Cuando Ignorarlo
Ocultar excesivamente los delegados puede causar código en el cual puede ser difícil identificar donde está ocurriendo la funcionalidad. Lo cual es otra forma de evitar el olor de [intermediario](../CodeSmell/MiddleMan.md) también.

