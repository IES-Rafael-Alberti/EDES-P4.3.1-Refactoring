
# Obsesión Primitiva

## Signos y Síntomas
-Uso de primitivos en lugar de objetos pequeños para tareas simples (como moneda, rangos, cadenas especiales para números de teléfono, etc.).

-Uso de constantes para información de codificación (como una constante `USER_ADMIN_ROLE = 1` para referirse a usuarios con derechos de administrador).

-Uso de constantes de cadena como nombres de campo para su uso en matrices de datos.

![imagen](https://refactoring.guru/images/refactoring/content/smells/primitive-obsession-01.png)

## Razones del Problema


Como la mayoría de los otros "olores" en el código, las obsesiones primitivas nacen en momentos de debilidad. "¡Solo un campo para almacenar algunos datos!", dijo el programador. ¡Crear un campo primitivo es mucho más fácil que hacer una clase completamente nueva, ¿verdad? Y así se hizo. Luego se necesitó otro campo y se agregó de la misma manera. He aquí que la clase se volvió enorme e inmanejable.

A menudo se usan primitivos para "simular" tipos. Entonces, en lugar de un tipo de datos separado, tienes un conjunto de números o cadenas que forman la lista de valores permitidos para alguna entidad. Se les dan nombres fáciles de entender a estos números y cadenas específicos a través de constantes, por eso están dispersos por todas partes.

Otro ejemplo de mal uso de primitivos es la simulación de campos. La clase contiene una gran variedad de datos y constantes de cadena (especificadas en la clase) que se usan como índices de matriz para obtener estos datos.

## Tratamiento

-Si tienes una gran variedad de campos primitivos, puede ser posible agrupar lógicamente algunos de ellos en su propia clase. Aún mejor, mueve el comportamiento asociado con estos datos también a la clase. Para esta tarea, prueba Reemplazar Valor de Datos con Objeto.

![imagen](https://refactoring.guru/images/refactoring/content/smells/primitive-obsession-01.png)

-Si los valores de los campos primitivos se usan en los parámetros de los métodos, utiliza Introducir Objeto de Parámetro o Preservar Objeto Completo.

-Cuando datos complicados están codificados en variables, utiliza Reemplazar Código de Tipo con Clase, Reemplazar Código de Tipo con Subclases o Reemplazar Código de Tipo con Estado/Estrategia.

-Si hay matrices entre las variables, utiliza Reemplazar Matriz con Objeto.


![imagen](https://refactoring.guru/images/refactoring/content/smells/primitive-obsession-03.png)
# Beneficios

-El código se vuelve más flexible gracias al uso de objetos en lugar de primitivos.

-Mejor comprensión y organización del código. Las operaciones en datos particulares están en el mismo lugar, en lugar de estar dispersas. Ya no hay que adivinar la razón de todas esas constantes extrañas y por qué están en una matriz.

-Más fácil encontrar código duplicado.