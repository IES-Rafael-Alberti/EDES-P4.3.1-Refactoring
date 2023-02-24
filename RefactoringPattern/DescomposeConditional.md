# Problema
Tienes un condicional complejo ( if-then/ elseo switch).

if  ( fecha . antes de ( SUMMER_START ) || fecha . después de ( SUMMER_END ) ) { cargo = cantidad * tarifainvierno + cargoservicioinvierno ; } else { cargo = cantidad * tasaverano ; }

# Solución
Descomponga las partes complicadas del condicional en métodos separados: la condición theny else.


if  ( esVerano ( fecha ) )  { cargo = CargoVerano ( cantidad ) ; } else { cargo = cargoinvierno ( cantidad ) ; }


## Por qué refactorizar
Cuanto más larga es una pieza de código, más difícil es de entender. Las cosas se vuelven aún más difíciles de entender cuando el código está lleno de condiciones:

Mientras está ocupado averiguando qué thenhace el código en el bloque, olvida cuál era la condición relevante.

Mientras está ocupado analizando else, olvida lo que thenhace el código.

## Beneficios
Al extraer el código condicional a métodos con nombres claros, haces la vida más fácil para la persona que mantendrá el código más adelante (¡como tú, dentro de dos meses!).

Esta técnica de refactorización también es aplicable para expresiones cortas en condiciones. La cadena isSalaryDay()es mucho más bonita y más descriptiva que el código para comparar fechas.

## Cómo refactorizar
Extraiga el condicional a un método separado a través de Extract Method .

Repita el proceso para los bloques theny else.