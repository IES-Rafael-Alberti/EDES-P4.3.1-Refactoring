# Movimiento de Método (Move method)

## Problema

Un método se usa más en otra clase que en su propia clase.

![](https://refactoring.guru/images/refactoring/diagrams/Move%20Method%20-%20Before.png?id=4abd2ccfc636cdcffe30f5593868bbfa)

## Solución

Crea un nuevo método en la clase que usa más este método, entonces move el código del nuevo método a aquí. Convierte el código del método original en una referencia al nuevo método en la otra clase o bórralo completamente.

![](https://refactoring.guru/images/refactoring/diagrams/Move%20Method%20-%20After.png?id=df9892b4d0a367b12881e93e7d0ea0c0a)

## Por qué refactorizar

1. Quieres mover un método a una clase que contiene la mayoría de los datos usados por ese método. Esto hace a las clases más coherentes internamente.

2. Quiere mover un método para reducir o eliminar la dependencia de la clase llamando al método en la clase en la que está localizado. Esto puede ser útil si la llamda a la clase ya es dependiente de la clase a la que estás planeando mover el método. Esto reduce la dependencia entre clases.

## Como refactorizar

1. Verifica todas las característica usadas usadas por el viejo método. Ouede ser una buena idea moverlas también. Como regla, si una característica se usa solo para el método bajo consideración, deberías mover la característica al mismo. Si la característica se usa en otros métodos también, deberías mover esos métodos también. A veces es más facil mover un gran número de métods que establecer relaciones entre ellos en diferentes clases.

    Asegúrate de que el método no se ha declarado en superclases y subclases. Si este es el caso, deberías evitar moverlo o en su defecto, aplicar algún tipo de polimorfismo en la clase destinataria para asergurar la funcionalidad variable de un método dividido entre claseses donantes.

2. Declara un nuevo método en la clase destinataria. Debes darle un nuevo nombre al método para que sea más apropiado para su nueva clase.

3. Decide cómo te referirás a la destinataria. Debes tener un campo o método que devuelve un objeto apropiado, pero si no, necesitarás escribir un nuevo método o campo para almacenar el objeto de la clase destinataria.

    Ahora deberías tener una forma de referirte al objeto destinatario y un nuevo método en su clase. Con todo eso hecho, puedes convertir el viejo método en una referencia al nuevo método.

4. Observa: ¿puedes borrar el viejo método completamente? Si la respuesta es sí, crea una referencia al nuevo método en todos los lugares donde se haya usado el antiguo.