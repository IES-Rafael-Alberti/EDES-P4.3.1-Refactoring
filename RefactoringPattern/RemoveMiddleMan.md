# Eliminar intermediario

## Problema
Una clase tiene demasiados métodos que simplemente delegan en otros objetos.

![](https://refactoring.guru/images/refactoring/diagrams/Remove%20Middle%20Man%20-%20Before.png?id=f51110f3e0d4423b3f9088e92fc3dce4)

```Kotlin
interface Cliente{
    // Codigo de la Interfaz 
}
open class Departamento{
    fun getManager(){
        //Codigo de la funcion 
    }
}
class Persona : Cliente{
    fun getManager(){
        var departamento = Departamento()
        departamento.getManager()
    }

```


## Solución

Elimine estos métodos y obligue al cliente a llamar directamente a los métodos finales.

![](https://refactoring.guru/images/refactoring/diagrams/Remove%20Middle%20Man%20-%20After.png?id=f7de1016e76545f7c51af09463ce5f4c)

``` kotlin 

interface Cliente{
    //Codigo de la Interfaz 
}

open class Departamento : Cliente{
    fun getManager(){
        //Codigo de la clase 
    }
}
class Persona : Cliente{
    fun getDepartamento(){
        //Codigo de la clase
    }
}
```

## ¿Por qué Refactorizar?

Para describir esta técnica, usaremos los términos de [ocultar delegado](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/HideDelegate.md), que son:

* El servidor o server es el objeto al que el cliente tiene acceso directo.

* El delegado o delegate es el objeto final que contiene la funcionalidad que necesita el cliente.

Hay dos tipos de problemas:

1. La clase de servidor no hace nada por sí misma y simplemente crea una complejidad innecesaria. En este caso, piense si esta clase es necesaria en absoluto.

2. Cada vez que se agrega una nueva característica al delegado, debe crear un método de delegación para ella en la clase de servidor. Si se hacen muchos cambios, esto será bastante tedioso.

## Cómo refactorizar

1. Cree un captador para acceder al objeto de clase delegada desde el objeto de clase de servidor.

2. Reemplace las llamadas a los métodos de delegación en la clase de servidor por llamadas directas a los métodos de la clase de delegado.
