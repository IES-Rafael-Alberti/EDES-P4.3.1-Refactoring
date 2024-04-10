# Método largo

## Signos y síntomas

Un método contiene demasiadas líneas de código. Por lo general, cualquier método de más de diez líneas debería hacer que comiences a hacer preguntas.

![](https://refactoring.guru/images/refactoring/content/smells/long-method-01.png?id=ba3b4a6d8ef25a8f676543cee5e1e019)

## Razones del problema

Al igual que el Hotel California, siempre se agrega algo a un método, pero nunca se elimina nada. Dado que es más fácil escribir código que leerlo, este "olor" pasa desapercibido hasta que el método se convierte en una bestia fea y de gran tamaño.<br><br>Mentalmente, a menudo es más difícil crear un nuevo método que agregar a uno existente: "Pero son solo dos líneas, no sirve de nada crear un método completo solo para eso..." Lo que significa que se agrega otra línea y luego otra, dando a luz a una maraña de código de espagueti.

## Tratamiento

Como regla general, si siente la necesidad de comentar algo dentro de un método, debe tomar este código y ponerlo en un nuevo método. Incluso una sola línea puede y debe dividirse en un método separado, si requiere explicaciones. Y si el método tiene un nombre descriptivo, nadie necesitará mirar el código para ver lo que hace.

![](https://refactoring.guru/images/refactoring/content/smells/long-method-02.png?id=274350a92b305ae79848ab40b3bdb0cb)

* Para reducir la longitud del cuerpo de un método, utilice [método de extracción](../RefactoringPattern/ExtractMethod.md).

* Si las variables locales y los parámetros interfieren con la extracción de un método, utilice [reemplazar variables temporales con consultas](../RefactoringPattern/ReplaceTempwithQuery.md), [introducir objeto de parámetro](../RefactoringPattern/IntroduceParameterObject.md) o [conservar objeto completo](../RefactoringPattern/PreserveWholeObject.md) .

*  Si ninguna de las recetas anteriores ayuda, intente mover todo el método a un objeto separado a través de [reemplazar método con objeto de método](../RefactoringPattern/ReplaceMethodWithMethodObject.md).

* Los operadores condicionales y los bucles son una buena pista de que el código se puede mover a un método separado. En el caso de los condicionales, utilice [descomponer condicional](../RefactoringPattern/DecomposeConditional.md). Si los bucles están en el camino, pruebe el [método de extracción.](../RefactoringPattern/ExtractMethod.md).

## Beneficios

* Entre todos los tipos de código orientado a objetos, las clases con métodos cortos viven más tiempo. Cuanto más largo es un método o función, más difícil se vuelve entenderlo y mantenerlo.
* Además, los métodos largos ofrecen el escondite perfecto para el código duplicado no deseado.

![](https://refactoring.guru/images/refactoring/content/smells/long-method-03.png?id=82ce2d388aa14bdae4e8f62b875f0259)

### Actuación

¿Un aumento en la cantidad de métodos perjudica el rendimiento, como afirman muchas personas? En casi todos los casos, el impacto es tan insignificante que ni siquiera vale la pena preocuparse.

Además, ahora que tienes un código claro y comprensible, es más probable que encuentres métodos realmente efectivos para reestructurar el código y obtener ganancias de rendimiento reales si surge la necesidad.
