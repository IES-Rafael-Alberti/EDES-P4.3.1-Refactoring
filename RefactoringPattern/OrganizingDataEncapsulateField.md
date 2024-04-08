## Encapsular campo
# Problema
Tienes un campo público.
``` Kotlin
class Person {
  public String name;
}
```

# Solución
Haga que el campo sea privado y cree métodos de acceso para él.

``` Kotlin
class Person {
  private String name;

  public String getName() {
    return name;
  }
  public void setName(String arg) {
    name = arg;
  }
}
```

## ¿Por qué Refactorizar?
Uno de los pilares de la programación orientada a objetos es la encapsulación, la capacidad de ocultar datos de objetos. De lo contrario, todos los objetos serían públicos y otros objetos podrían obtener y modificar los datos de su objeto sin ningún tipo de control y equilibrio. Los datos se separan de los comportamientos asociados con estos datos, la modularidad de las secciones del programa se ve comprometida y el mantenimiento se complica.

## Beneficios
* Si los datos y el comportamiento de un componente están estrechamente interrelacionados y están en el mismo lugar en el código, es mucho más fácil para usted mantener y desarrollar este componente.

* También puede realizar operaciones complicadas relacionadas con el acceso a los campos de objeto.

## Cuándo no usar
En algunos casos, la encapsulación no es aconsejable debido a consideraciones de rendimiento. Estos casos son raros, pero cuando ocurren, esta circunstancia es muy importante.<br><br>Supongamos que tiene un editor gráfico que contiene objetos que poseen coordenadas x e y. Es poco probable que estos campos cambien en el futuro. Además, el programa involucra una gran cantidad de objetos diferentes en los que estos campos están presentes. Por lo tanto, el acceso directo a los campos de coordenadas ahorra ciclos de CPU significativos que, de otro modo, se consumirían llamando a los métodos de acceso.<br><br>Como ejemplo de este caso inusual, está la clase [Point](https://docs.oracle.com/javase/7/docs/api/java/awt/Point.html) en Java. Todos los campos de esta clase son públicos.

## Cómo refactorizar
1. Cree un captador o getter y un establecedor o setter para el campo.
2. Busque todas las invocaciones del campo. Reemplace la recepción del valor de campo por el captador y reemplace la configuración de nuevos valores de campo por el establecedor.
3. Una vez que se hayan reemplazado todas las invocaciones de campo, haga que el campo sea privado.

## Próximos pasos
Encapsular campo es solo el primer paso para acercar los datos y los comportamientos que involucran estos datos. Después de crear métodos simples para los campos de acceso, debe volver a comprobar los lugares donde se llama a estos métodos. Es muy posible que el código en estas áreas se vea más apropiado en los métodos de acceso.
