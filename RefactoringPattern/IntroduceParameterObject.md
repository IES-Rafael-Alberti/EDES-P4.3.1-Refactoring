# Introducir Objeto de Parámetro

## Problema
Los métodos contienen un grupo repetido de parámetros

![](./assets/IntroduceParameterObject-Before.png)

## Solución
Reemplazar estos parámetros con un objeto

![](./assets/IntroduceParameterObject-After.png)

## Porque Refactorizar
A menudo nos encontramos con grupos idénticos de parámetros en múltiples métodos. Esto causa duplicación de código, tanto de los parámetros en sí como de las operaciones relacionadas. Al consolidar los parámetros en una sola clase, también puedes mover los métodos para poder manejar estos datos, liberando a los demás métodos de este código.

## Beneficios
- Código más legible. En lugar de un revoltijo de parámetros, verás un único objeto con un nombre comprensible.
* Grupos idénticos de parámetros dispersos aquí y allá crean su propio tipo de duplicación de código: de esta forma no se llama a código idéntico, constantemente nos encontramos con grupos idénticos de parámetros y argumentos.

## Desventajas
Si solo mueves datos a una nueva clase y no planeas mover ningún comportamiento u operaciones relacionadas allí, esto podría ser un olor de tipo [Clase de Datos](../CodeSmell/DataClass.md).

## Como Refactorizar
1. Crea una nueva clase que representará tu grupo de parámetros. Haz que la clase sea inmutable.
2. En el método que deseas refactorizar, utiliza [Añadir Parámetro](../RefactoringPattern/AddParameter.md), que es donde se pasará el objeto parámetro. En todas las llamadas al método, pasa el objeto creado a partir de los parámetros del método antiguo a este parámetro.
3. Ahora comienza a eliminar los parámetros antiguos del método uno por uno, reemplazándolos en el código con los campos del parámetro del objeto. Prueba el programa después de cada vez que reemplaces un parámetro.
4. Cuando termines, comprueba si tiene sentido mover una parte del método (o a veces incluso el método completo) a la clase de objeto de parámetro. Si es así, utiliza [Mover Método](../RefactoringPattern/MoveMethod.md) o [Extraer Método](../RefactoringPattern/ExtractMethod.md).