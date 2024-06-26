# Clase larga (Large Class)

## Síntomas y signos

La clase contiene muchos campos, métodos o líneas de código

![](./assets/large-class-01.png)

## Razones del problema

Las clases normalmente empiezan siendo pequeñas, pero poco a poco, estas se hinchan a medida que el programa crece. 

Como es el caso también de los métodos largos, los programadores, normalmente los programadores encuentran menos exigente crear una nueva funcionalidad en una clase ya existente, en vez de crear una nueva clase para esa funcionalidad.

![](./assets/large-class-02.png)

## Tratamiento

Cuando la clase tiene varios objetivos, piensa en separarlos

- [Extraer clases](../RefactoringPattern/ExtractClass.md): de ayuda cuando parte del comportamiento de la clase larga pueden ser separadas dentro de un componente diferente

- [Extraer subclase](../RefactoringPattern/ExtractSubclass.md): de ayuda si el comportamiento de la clase larga puede ser implementado en un sitio diferente o se usa raramente.

- [Extraer interfaz](../RefactoringPattern/ExtractSubclass.md): de ayuda si es necesario tener una lista de las operaciones y comportamientos que el cliente puede utilizar.

> Si una clase grande es responsable de la interfaz gráfica, puede intentar mover algunos de sus datos y comportamiento a un objeto de dominio separado. Al hacerlo, puede ser necesario almacenar copias de algunos datos en dos lugares y mantener los datos consistentes. Los [datos observados duplicados](../RefactoringPattern/DuplicateObservedData.md) ofrecen una manera de hacer esto.

![](./assets/large-class-03.png)

## Recompensa

- La refactorización de estas clases evita que los desarrolladores necesiten recordar una gran cantidad de atributos para una clase.

- En algunos casos, dividir clases largas en fragmentos más pequeños puede evitar la duplicación tanto de código como de funcionalidad.