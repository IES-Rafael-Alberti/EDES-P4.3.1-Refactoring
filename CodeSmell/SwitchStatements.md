# Sentencias Switch
## Signos y Síntomas

Tienes un operador `switch` complejo o una secuencia de declaraciones `if`.

![imagen](https://refactoring.guru/images/refactoring/content/smells/switch-statements-01.png?id=1c5a538d451c3d2b2e43d0d4f53b994b)

## Razones del problema
El uso relativamente poco frecuente de los operadores `switch` y `case` es una de las características distintivas del código orientado a objetos. A menudo, el código para un solo `switch` puede estar disperso en diferentes lugares del programa. Cuando se agrega una nueva condición, es necesario encontrar todo el código del `switch` y modificarlo.

Como regla general, cuando veas un switch, deberías pensar en polimorfismo.

## Tratamiento
· Para aislar el `switch` y colocarlo en la clase correcta, es posible que necesites utilizar <u>**Extract Method**</u> y luego <u>**Move Method.**</u>

· Si un `switch` se basa en un código de tipo, como cuando se cambia el modo de ejecución del programa, utiliza <u>**Replace Type Code with Subclasses**</u> o <u>**Replace Type Code with State/Strategy.**</u>

· Después de especificar la estructura de herencia, utiliza <u>**Replace Conditional with Polymorphism.**</u>

· Si no hay demasiadas condiciones en el operador y todas llaman al mismo método con diferentes parámetros, el polimorfismo será superfluo. En este caso, puedes dividir ese método en varios métodos más pequeños con <u>**Replace Parameter with Explicit Methods**</u> y cambiar el `switch` en consecuencia.

· Si una de las opciones condicionales es nula, utiliza <u>**Introduce Null Object.**</u>

## Beneficios
Mejora de la organización del código.

![imagen](https://refactoring.guru/images/refactoring/content/smells/switch-statements-02.png?id=29ec9ad9c6d760d2b940a68a1d23c4be)

## Cuándo ignorar
Cuando un operador `switch` realiza acciones simples, no hay razón para realizar cambios en el código.

A menudo, los operadores `switch` se utilizan en patrones de diseño de fábrica (<u>**Factory Method**</u> o <u>**Abstract Factory**</u>) para seleccionar una clase creada.