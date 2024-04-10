# Clase perezosa (Lazy Class)

## Síntomas y signos

Entender y mantener las clases siempre cuestan tiempo y dinero. 
Entonces, si una clase no hace lo suficiente para llamar tu atencion, debe eliminarse.

![](./assets/lazy-class-01.png)

## Razones del problema

Quizas la clase fue diseñada para cumplir una función, pero después de algunas refactorizaciones se ha vuelto ridículamente pequeña. 
O tal vez fue diseñado para apoyar el trabajo de desarrollo futuro y al final nunca se hizo.

## Tratamiento

- Los componentes que son casi inútiles deben recibir el tratamiento de clase en línea.

- Para subclases con pocas funciones, pruebe a contraer la jerarquía.

![](./assets/lazy-class-02.png)

## Recompensa

El tamaño del código se reduce y el mantenimiento se vuelve mas fácil.

## Cuando ignorar

A veces se crea una Lazy Class con el fin de delinear intenciones para el desarrollo futuro, en este caso,
trate de mantener un equilibrio entre la claridad y la simplicidad en su código.