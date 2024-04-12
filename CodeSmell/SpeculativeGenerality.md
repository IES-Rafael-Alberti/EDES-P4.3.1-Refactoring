# Generalidad Especulativa (Speculative Generality)

## Signos y síntomas

Existe una clase, método, campo o parámetro sin uso.

![](/CodeSmell/assets/speculative-generality-01.png)

## Razones del problema

A veces se crea código "por si acaso" para anticiparse a futuras utilidades en ocasiones nunca  son implementadas.
Como resultado, el código se vuelve difícil de entender y de mantener.

## Tratamiento

- Para eliminar clases abstractas, emplea [Colapsar Jerarquía](/RefactoringPattern/CollapseHeirarchy.md).

- La delegación innecesaria de una funcionalidad a otra clase puede ser eliminada empleando [Inline Class](/RefactoringPattern/InlineClass.md).

- ¿Tienes métodos que no se usan? Usa [Método en línea](/RefactoringPattern/InlineMethod.md) para deshacerte de ellos.

- Los métodos con parámetros sin utilizar deberían revisarse empleando [Borrar Parámetro](/RefactoringPattern/RemoveParameter.md)

- Los campos sin usar pueden ser simplemente eliminadas.

![](/CodeSmell/assets/speculative-generality-02.png)

## Beneficios

- Código más corto.

- Mantenimiento más fácil.

### Cuando Ignorar

- Si está trabajando en un framework, es sumamente razonable crear una funcionalidad que no se usa en el propio framework, siempre que los usuarios del framework necesiten la funcionalidad.

- Antes de eliminar elementos, asegúrese de que no se utilicen en pruebas unitarias. Esto sucede si las pruebas necesitan una forma de obtener cierta información interna de una clase o realizar acciones especiales relacionadas con las pruebas.
