# LISTA LARGA DE PARAMETROS

## SIGNOS Y SINTOMAS
Hay más de tres o cuatro parámetros para un método.


## RAZONES DEL PROBLEMA
 Una lista larga de parámetros puede ocurrir cuando se juntan varios algoritmos en un método. Una lista larga puede haber sido creada para controlar de qué manera se ejecutará el algoritmo.

 Las listas largas de parámetros también pueden ser el subproducto de esforzarse por hacer que las clases sean más independientes entre sí. Por ejemplo, el código para crear objetos específicos necesarios en un método se movió del método al código para llamar al método, pero los objetos creados se pasan al método como parámetros. Por lo tanto, la clase original ya no reconoce las relaciones entre los objetos y la dependencia ha disminuido. Pero si varios de estos objetos se crean, cada uno de ellos requerirá su propio parámetro, lo que significa una lista de parámetros más larga.

 Es difícil entender estas listas, que se vuelven contradictorias y difíciles de usar a medida que crecen. En lugar de una lista larga de parámetros, un método puede usar los datos de su propio objeto. Si el objeto actual no contiene los datos necesarios, otro objeto (que obtendrá los datos necesarios) se puede pasar como parámetro del método.

## TRATAMIENTO
 - Comprueba qué valores son pasados por parámetros. Si alguno de los argumentos son solo resultados de llamadas de métodos a otro objeto, usa Reemplazar parámetro con llamada a método. Este objeto puede colocarse en el campo de su propia clase o pasarse como un parámetro de método.

- En lugar de pasar un grupo de datos recibidos de otro objeto como parámetros, pasa el objeto al método, usando Preserve Whole Object.

- Pero si estós parámetros vienen de fuentes diferentes, puedes pasarlo como un único parámetro objeto a través de Introducir objeto de parámetro.


## RECOMPENSA
 - Código más legible y corto.

 - Refactorizar puede revelar código duplicado que antes no se había detectado.

## CUANDO IGNORAR
 - No te deshagas de los parámetros si al hacerlo causaría una dependencia indeseada entre clases.