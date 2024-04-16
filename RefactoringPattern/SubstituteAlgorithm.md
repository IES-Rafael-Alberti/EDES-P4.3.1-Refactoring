# Algoritmo de sustitución

## Problema

¿Así que quieres sustituir un algoritmo existente por uno nuevo?
```kotlin
fun foundPerson(people: Array<String>): String? {
    for (i in people.indices) {
        if (people[i] == "Don") {
            return "Don"
        }
        if (people[i] == "John") {
            return "John"
        }
        if (people[i] == "Kent") {
            return "Kent"
        }
    }
    return ""
}
```
## Solución
Reemplaza el cuerpo del método que implementa el algoritmo con uno nuevo.
```kotlin
fun foundPerson(people: Array<String?>): String? {
    val candidates: List<*> = Arrays.asList(*arrayOf("Don", "John", "Kent"))
    for (i in people.indices) {
        if (candidates.contains(people[i])) {
            return people[i]
        }
    }
    return ""
}
```
## Porque refactorizar
1. La refactorización gradual no es el único método para mejorar un programa. A veces, un método está tan repleto de problemas que es más fácil partir a cachos el método y empezar de nuevo. Y quizás hayas encontrado un algoritmo que es mucho más simple y más eficiente. Si este es el caso, simplemente tienes que reemplazar el algoritmo anterior por el nuevo.

2. A medida que pasa el tiempo, es posible que tú algoritmo se incorpore a una biblioteca o framework conocido y quieras deshacerte de tú implementación independiente para simplificar el mantenimiento.

3. Los requisitos para tú programa pueden cambiar tanto que el algoritmo existente no pueda usarse para la nueva finalidad.

## Cómo refactorizar

1. Asegúrate de haber simplificado el algoritmo existente tanto como sea posible. Mueva el código sin importancia a otros métodos usando el [método de extracción](./ExtractMethod.md). Cuantas menos partes móviles tenga el algoritmo, más fácil será reemplazarlo.


2. Crea el nuevo algoritmo en un nuevo método. Reemplaza el antiguo algoritmo con el nuevo y comienza a probar el programa.


3. Si los resultados no coinciden, vuelve a la implementación anterior y compara los resultados. Identifica las causas de la discrepancia. Si bien la causa suele ser un error en el algoritmo anterior, es más probable que se deba a algo que no funciona en el nuevo.


4. Cuando todas las pruebas se completen con éxito, ¡elimine el algoritmo anterior para siempre!
