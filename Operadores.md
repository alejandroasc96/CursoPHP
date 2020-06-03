<style>
#colorRed{
    color:red;
}
</style>
# Operandos <a name="id0"></a>
Hay tres tipos:

**Unarios**   -5

**Binarios** 10 +12

**Ternario** true? 'hola' : 'Adios'

## 1. Operadores de comparación <a name="id1"></a>

Los **operadores de comparación** permiten comparar dos valores. Estos valores dependen de los [tipos que tengan asignados](http://php.net/manual/es/language.types.type-juggling.php). Pueden verse las diferencias comparativas en la [tabla de comparación de tipos](http://php.net/manual/es/types.comparisons.php).

| Ejemplo   	| Nombre            	| Resultado                                            	|
|-----------	|-------------------	|------------------------------------------------------	|
| $x == $y  	| Igual             	| true sean del mismo tipo o no                        	|
| $x === $y 	| Idéntico          	| true sólo si son del mismo tipo                      	|
| $x != $y  	| Distinto          	| true si son diferentes sean del mismo tipo o no      	|
| $x <> $y  	| Distinto          	| true si son diferentes sean del mismo tipo o no      	|
| $x !== $y 	| No idéntido       	| true sólo si no son iguales y tampoco del mismo tipo 	|
| $x < $y   	| Menor que         	| true si $x es menor que y                            	|
| $x > $y   	| Mayor que         	| true si $x es mayor que $y                           	|
| $x <= $y  	| Menor o igual que 	| true si $x es menor o igual que $y                   	|
| $x >= $a  	| Mayor o igual que 	| true si $x es mayor o igual que $y                   	|

><strong id="colorRed">NOTA</strong> Si se **compara** un **número** con un **string** o la comparación es entre strings numéricos, cada string se convierte en número y la comparación se realiza numéricamente (esto también se incluye con el uso de switch). Cuando se hacen comparaciones idénticas como === esto no tiene sentido ya que también se comparan los tipos.

## 2. Comparaciones entre varios tipos <a name="id2"></a>

| Ejemplo   	| Nombre            	| Resultado                                            	|
|-----------	|-------------------	|------------------------------------------------------	|
| $x == $y  	| Igual             	| true sean del mismo tipo o no                        	|
| $x === $y 	| Idéntico          	| true sólo si son del mismo tipo                      	|
| $x != $y  	| Distinto          	| true si son diferentes sean del mismo tipo o no      	|
| $x <> $y  	| Distinto          	| true si son diferentes sean del mismo tipo o no      	|
| $x !== $y 	| No idéntido       	| true sólo si no son iguales y tampoco del mismo tipo 	|
| $x < $y   	| Menor que         	| true si $x es menor que y                            	|
| $x > $y   	| Mayor que         	| true si $x es mayor que $y                           	|
| $x <= $y  	| Menor o igual que 	| true si $x es menor o igual que $y                   	|
| $x >= $a  	| Mayor o igual que 	| true si $x es mayor o igual que $y                   	|

><strong id="colorRed">NOTA</strong> Debido a la forma en que son interpretados internamente los _floats_, su comparación puede dar resultados inesperados, aunque existen [formas de poder compararlos](http://php.net/manual/es/language.types.float.php#language.types.float.comparison).

## 3. Operadores aritméticos <a name="id3"></a>
Los **operadores aritméticos en PHP** son los mismos que en las matemáticas:

| Operadores artiméticos 	| Representación 	|
|------------------------	|----------------	|
| Suma                   	| $x + $y        	|
| Resta                  	| $x - $y        	|
| Multiplicación         	| $x * $y        	|
| División*              	| $x / $y        	|
| Módulo**               	| $x % $y        	|
| Exponenciación         	| $x ** $y       	|
| Negación               	| -$x            	|

**División** * devuelve un (int) si $x y $y son divisibles, o (float) si no lo son.

**Módulo** ** se **eliminarían** primero las **partes decimales** transformándose en (int) **en caso de ser (float)** y luego se haría la operación. El signo (+ o -) del resultado dependerá del dividendo**, por ejemplo: -5 % 3 mostraría -2.



## 4. Operador Ternario <a name="id4"></a>

```php
<?php
$x = "";
$accion = (empty($x)) ? 'valor1' : 'valor2'; // Devolverá (string) valor1

// Explicación Supongamos la expresión $x ? $y : $z. Si $x es true, se evaluará $y. Si $x es false, se evaluará $z.

// Lo anterior será lo mismo que:
if(empty($x)) {
    $accion = 'valor1';
} else {
    $accion = 'valor2';
}
```
> Una **forma más reducida del operador ternario** es mediante **?:** . Suponiendo $x ?: $y, devolverá $x si $x es true, y $y si $x es false.

