# Por qué refactorizar
A menudo se encuentran grupos idénticos de parámetros en múltiples métodos. Esto provoca la duplicación de código tanto de los propios parámetros como de las operaciones relacionadas. Al consolidar los parámetros en una sola clase, también puede mover los métodos para manejar estos datos allí, liberando a los otros métodos de este código.

## Beneficios
Código más legible. En lugar de una mezcolanza de parámetros, verá un solo objeto con un nombre comprensible.

Los grupos idénticos de parámetros dispersos aquí y allá crean su propio tipo de duplicación de código: mientras no se llama a un código idéntico, se encuentran constantemente grupos idénticos de parámetros y argumentos.

## Inconvenientes
Si mueve solo datos a una nueva clase y no planea mover ningún comportamiento u operación relacionada allí, esto comienza a oler a una clase de datos .
Cómo refactorizar
Crea una nueva clase que representará tu grupo de parámetros. Haz que la clase sea inmutable.

En el método que desea refactorizar, use Agregar parámetro , que es donde se pasará su objeto de parámetro. En todas las llamadas a métodos, pase el objeto creado a partir de parámetros de métodos antiguos a este parámetro.

Ahora comience a eliminar los parámetros antiguos del método uno por uno, reemplazándolos en el código con campos del objeto de parámetro. Pruebe el programa después de cada reemplazo de parámetros.

Cuando termine, vea si tiene sentido mover una parte del método (o, a veces, incluso todo el método) a una clase de objeto de parámetro. Si es así, use Move Method o Extract Method .