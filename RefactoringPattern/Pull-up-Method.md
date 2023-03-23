# Método Pull Up

## Problema

Tus subclases tienen métodos que realizan un trabajo similar.

**Pull Up Method - Antes**

![](https://refactoring.guru/images/refactoring/diagrams/Pull%20Up%20Method%20-%20Before.png)

## Solución

Haz que los métodos sean idénticos y luego muévelos a la superclase relevante.

**Pull Up Method - Después**

![](https://refactoring.guru/images/refactoring/diagrams/Pull%20Up%20Method%20-%20After.png)

## Por qué refactorizar

Las subclases crecieron y se desarrollaron independientemente unas de otras, lo que causó campos y métodos idénticos (o casi idénticos).

## Beneficios

Elimina el código duplicado. Si necesitas hacer cambios en un método, es mejor hacerlo en un solo lugar que tener que buscar
todos los duplicados del método en las subclases.

Esta técnica de refactorización también se puede utilizar si, por alguna razón, una subclase redefine un método de la superclase
pero realiza un trabajo esencialmente igual.

## Cómo refactorizar

1. Investiga métodos similares en superclases. Si no son idénticos, dales formato para que coincidan entre sí.

2. Si los métodos usan un conjunto diferente de parámetros, pon los parámetros en la forma que deseas ver en la superclase.

3. Copia el método a la superclase. Aquí puedes encontrar que el código del método utiliza campos y métodos que existen solo en las subclases y, por lo tanto, no están disponibles en la superclase. Para resolver esto, puedes:

    - **Para campos**: utiliza [Pull Up Field](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/tree/main/RefactoringPattern/Pull-Up-Field.md) o [Self-Encapsulate Field](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/tree/main/RefactoringPattern/Self-Encapsulate-Field.md) para crear getters y setters en las subclases; luego declara estos getters abstractamente en la superclase.

    - **Para métodos**: utiliza Pull Up Method o declara métodos abstractos para ellos en la superclase (ten en cuenta que tu clase se volverá abstracta si antes no lo era)
4. Elimina los metodos de las subclases 

5. Comprueba los lugares en los que llamas al metodo. En algunos podras reemplazarlo con el uso de una subclase de la superclase.
