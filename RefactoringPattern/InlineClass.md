# Clase alineada (Inline Class)

## Problema

Una clase no hace casi nada y no es responsable de nada, y no hay responsabilidades adicionales planificadas para esta.

![](https://refactoring.guru/images/refactoring/diagrams/Inline%20Class%20-%20Before.png?id=717d80baaa902d09acbaa55fd0539638https://refactoring.guru/images/refactoring/diagrams/Move%20Field%20-%20Before.png?id=b58c81b01a0c4ef8659f92cc64fa51a)

## Solución

Mueve todas las funcionalidades de la clase a otra.

![](https://refactoring.guru/images/refactoring/diagrams/Inline%20Class%20-%20After.png?id=7cb7db0fe2ab0d17f067d411f9e98f15https://refactoring.guru/images/refactoring/diagrams/Move%20Field%20-%20After.png?id=d7c21af94ec9df17575373bae745e96)

## Por qué refactorizar

A menudo se necesita esta técnica después de que las funcionalidades de una clase sean "trasplantadas" a otras clases, dejando esta clase sin apenas funcionalidad.

## Beneficios

Eliminar las clases innecesarias libera memoria a la máquina y estrés en tu cabeza.

## Como refactorizar

1. En la clase destinataria, crea campos y métodos públicos presentes en la clase donante. Los métodos deben referirse a los métods que equivalgan en la clase donante.
2. Reemplaza todas las referencias de la clase donantes con referencias a los campos y métodos de la clase recipiente.
3. Ahora prueba el programa y asegurate de que no se hayan creado nuevos errores. Si las pruebas demuestran que todo está funcionando bien, empieza a usar el [movimiento de métodos](MoveMethod.md) y el [movimiento de campos](MoveField.md) para trasplantar todas las funcionalidades de la clase recipiente desde la original. Continúa haciendo esto hasta que la clase original esté completamente vacía.
4. Borra la clase original.
