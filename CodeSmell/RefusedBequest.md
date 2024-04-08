# Herencia Rechazada

## Signos y Síntomas

Si una subclase utiliza solo algunos de los métodos y propiedades heredados de sus padres, la jerarquía está desequilibrada. Los métodos no necesarios pueden quedar sin usar o ser redefinidos y generar excepciones.
![Ejemplo de mal olor de código: herencia rechazada](https://refactoring.guru/images/refactoring/content/smells/refused-bequest-01.png?id=7a1d79e75a3836c22ec865d72c98664e)
## Razones del Problema

Alguien se motivó a crear herencia entre clases únicamente por el deseo de reutilizar el código en una superclase. Pero la superclase y la subclase son completamente diferentes.
![Ejemplo de mal olor de código: herencia rechazada](https://refactoring.guru/images/refactoring/content/smells/refused-bequest-02.png?id=f9b0affd4bbf6fec22c05783fc75562e)
## Tratamiento

Si la herencia no tiene sentido y la subclase realmente no tiene nada en común con la superclase, elimina la herencia a favor de Reemplazar Herencia con Delegación.

Si la herencia es apropiada, elimina los campos y métodos no necesarios en la subclase. Extrae todos los campos y métodos necesarios por la subclase de la clase padre, colócalos en una nueva superclase y establece que ambas clases hereden de ella (Extraer Superclase).
![Ejemplo de mal olor de código: herencia rechazada](https://refactoring.guru/images/refactoring/content/smells/refused-bequest-03.png?id=2a84293620fa1caf4329fca1f4a44e08)
## Beneficios

Mejora la claridad y organización del código. Ya no tendrás que preguntarte por qué la clase "Perro" hereda de la clase "Silla" (aunque ambas tengan 4 patas).