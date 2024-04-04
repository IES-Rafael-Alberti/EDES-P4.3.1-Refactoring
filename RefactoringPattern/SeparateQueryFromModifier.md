# Separar Consulta de Modificador

### Problema
¿Tienes un método que devuelve un valor pero también cambia algo dentro de un objeto?

### Solución
Divide el método en dos métodos separados. Como podrías esperar, uno de ellos debería devolver el valor y el otro modificar el objeto.

![imagen](https://refactoring.guru/images/refactoring/diagrams/Separate%20Query%20from%20Modifier%20-%20Before.png?id=b28976c01f67d02e8b4574b1c825d10d)

![imagen](https://refactoring.guru/images/refactoring/diagrams/Separate%20Query%20from%20Modifier%20-%20After.png?id=c2b8e0722c1c8500302326ab60db80e5)

### Por qué Refactorizar
Esta técnica de refactorización implementa la <i>Segregación de Comando y Consulta de Responsabilidad.</i> Este principio nos dice que debemos separar el código responsable de obtener datos del código que cambia algo dentro de un objeto.

El código para obtener datos se llama <i>consulta.</i> El código para cambiar cosas en el estado visible de un objeto se llama <i>modificador.</i> Cuando se combinan una <i>consulta</i> y un <i>modificador</i>, no tienes una forma de obtener datos sin hacer cambios en su estado. En otras palabras, haces una pregunta y puedes cambiar la respuesta incluso mientras la estás recibiendo. Este problema se vuelve aún más grave cuando la persona que llama a la consulta puede no conocer los "efectos secundarios" del método, lo que a menudo conduce a errores en tiempo de ejecución.

Pero recuerda que los efectos secundarios son peligrosos solo en el caso de modificadores que cambian el estado visible de un objeto. Estos podrían ser, por ejemplo, campos accesibles desde la interfaz pública de un objeto, entrada en una base de datos, en archivos, etc. Si un modificador solo almacena en caché una operación compleja y la guarda dentro del campo privado de una clase, difícilmente podría causar efectos secundarios.

### Beneficios
Si tienes una consulta que no cambia el estado de tu programa, puedes llamarla tantas veces como quieras sin tener que preocuparte por cambios no deseados en el resultado causados simplemente por llamar al método.

### Desventajas
En algunos casos, es conveniente obtener datos después de realizar un comando. Por ejemplo, al eliminar algo de una base de datos, quieres saber cuántas filas se eliminaron.

### Cómo Refactorizar
1. Crea un nuevo método de consulta para devolver lo que hacía el método original.

2. Cambia el método original para que devuelva solo el resultado de llamar al nuevo método de consulta.

3. Reemplaza todas las referencias al método original con una llamada al método de consulta. Justo antes de esta línea, realiza una llamada al <i>método modificador</i>. Esto te salvará de efectos secundarios en caso de que el método original se haya utilizado en una condición de un operador condicional o un bucle.

4. Elimina el código que devuelve valores en el método original, que ahora se ha convertido en un método <i>modificador adecuado.</i>