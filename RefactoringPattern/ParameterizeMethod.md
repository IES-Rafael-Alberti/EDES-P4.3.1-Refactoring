# Por qué refactorizar
Si tienes métodos similares, probablemente tengas código duplicado, con todas las consecuencias que esto conlleva.

Además, si necesita agregar otra versión de esta funcionalidad, deberá crear otro método. En su lugar, podría simplemente ejecutar el método existente con un parámetro diferente.

## Inconvenientes
A veces, esta técnica de refactorización puede llevarse demasiado lejos, lo que da como resultado un método común largo y complicado en lugar de varios más simples.

También tenga cuidado al mover la activación/desactivación de la funcionalidad a un parámetro. Eventualmente, esto puede conducir a la creación de un gran operador condicional que deberá tratarse a través de Reemplazar parámetro con métodos explícitos .

## Cómo refactorizar
Cree un nuevo método con un parámetro y muévalo al código que es el mismo para todas las clases, aplicando el método de extracción . Tenga en cuenta que a veces solo una cierta parte de los métodos es realmente la misma. En este caso, la refactorización consiste en extraer solo la misma parte a un nuevo método.

En el código del nuevo método, reemplace el valor especial/diferente con un parámetro.

Para cada método anterior, busque los lugares donde se llama, reemplazando estas llamadas con llamadas al nuevo método que incluyen un parámetro. Luego elimine el método anterior.