# Generalidad Especulativa (Speculative Generality)

## Signos y síntomas

Es una clase, método, campo o parámetro sin uso.

![](/CodeSmell/assets/speculative-generality-01.png)

## Razones del problema

A veces se crea código "por si acaso" para anticiparse a futuras utilidades que nunca van a ser implementadas.
Como resultado el código se vuelve difícil de entender y de mantener.

## Tratamiento

- Para eliminar clases abstractas, intenta reducir la jerarquia.

- La delegación innecesaria de una funcionalidad a otra clase puede ser eliminada via Inline Class.

- ¿Tienes métodos que no se usan? Usa Inline Methods para desacerte de ellos.

- Los métodos con parámetros que no se usan deberian revisarse con la ayuda de un Remove Parameter

- Los campos que no se usen pueden simplemente ser eliminados.

![](/CodeSmell/assets/speculative-generality-02.png)

## Beneficios

- Código más delgado.

- Soporte más fácil.

### Actuación

- Si está trabajando en un marco, es eminentemente razonable crear una funcionalidad que no se usa en el marco en sí, siempre que los usuarios de los marcos necesiten la funcionalidad.

- Antes de eliminar elementos, asegúrese de que no se utilicen en pruebas unitarias. Esto sucede si las pruebas necesitan una forma de obtener cierta información interna de una clase o realizar acciones especiales relacionadas con las pruebas.
