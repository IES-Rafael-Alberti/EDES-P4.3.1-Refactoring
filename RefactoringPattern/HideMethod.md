# Esconder Método (Hide Method)

## Problema

Un método no es utilizado por otras clases o solamente se utiliza dentro de su propia jerarquía de clases.

~~~~
class ServicioDeNumeros(private val minimo: Int =0, private val maximo: Int =100) {
    var fuenteNumeros: MutableList<Int>
    val listaNumeros: List<Int> by lazy {
        List(maximo-minimo){
            minimo+it
        }
    }
~~~~

## Solución

Cambiar la forma del método para que este privada (private) o protegida (protected)

~~~~
class ServicioDeNumeros(private val minimo: Int =0, private val maximo: Int =100) {
    private lateinit var fuenteNumeros: MutableList<Int>
    private  val listaNumeros: List<Int> by lazy {
        List(maximo-minimo){
            minimo+it
        }
    }
~~~~

## Por qué Refactorizar
Muy a menudo, la necesidad de ocultar métodos para obtener y establecer valores se debe al desarrollo de una interfaz más rica que proporciona un comportamiento adicional,
especialmente si comenzó con una clase que agregó poco más allá de la mera encapsulación de datos.

A medida que se incorpora un nuevo comportamiento en la clase, es posible que descubra que los métodos públicos de captador y setter ya no son necesarios y se pueden ocultar.
Si hace que los métodos getter o setter sean privados y aplica acceso directo a las variables, puede eliminar el método.

## Beneficios

1. Ocultar métodos facilita la evolución del código. Cuando cambia un método privado, solo necesita preocuparse por cómo no romper la clase actual,
   ya que sabe que el método no se puede usar en ningún otro lugar.

2. Al hacer que los métodos sean privados, subraya la importancia de la interfaz pública de la clase y de los métodos que siguen siendo públicos.

## Cómo refactorizar

1. Trate regularmente de encontrar métodos que puedan hacerse privados.
   El análisis de código estático y una buena cobertura de pruebas unitarias pueden ofrecer una gran ventaja.
2. Haga que cada método sea lo más privado posible.
