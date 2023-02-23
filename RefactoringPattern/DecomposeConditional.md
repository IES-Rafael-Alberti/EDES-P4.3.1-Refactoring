# Descomponer condicional
## Problema
Tienes un condicional complejo (/ o ).if-thenelseswitch

JavaC #.PHPPitónMecanografiado
if (date.before(SUMMER_START) || date.after(SUMMER_END)) {
charge = quantity * winterRate + winterServiceCharge;
}
else {
charge = quantity * summerRate;
} 

## Solución
Descomponga las partes complicadas del condicional en métodos separados: la condición, y .thenelse

if (isSummer(date)) {
charge = summerCharge(quantity);
}
else {
charge = winterCharge(quantity);
}
## Por qué Refactorizar
Cuanto más largo es un fragmento de código, más difícil es entenderlo. Las cosas se vuelven aún más difíciles de entender cuando el código está lleno de condiciones:

Mientras estás ocupado averiguando qué hace el código en el bloque, olvidas cuál era la condición relevante.then

Mientras estás ocupado analizando, olvidas lo que hace el código.elsethen

## Beneficios
Al extraer el código condicional a métodos con nombres claros, le facilita la vida a la persona que mantendrá el código más adelante (como usted, ¡dentro de dos meses!).

Esta técnica de refactorización también es aplicable para expresiones cortas en condiciones. La cadena es mucho más bonita y descriptiva que el código para comparar fechas.isSalaryDay()

## Cómo refactorizar
Extraiga el condicional a un método separado a través de Extract Method.

Repita el proceso para los bloques y.thenelse