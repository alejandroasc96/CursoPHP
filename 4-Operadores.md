**Índice**   
1. [ Operadores de comparación](#id1)
2. [ Comparaciones entre varios tipos](#id2)
3. [ Operadores aritméticos](#id3)
4. [ Operadores de asignación](#id4)
   -  [4.1 Operadores de asignación](#id4.1)
   - [4.2 Operador combinado](#id4.2)
5. [Operadores lógicos](#id5)
6. [Operadores para strings](#id6)
7. [Operadores para arrays](#id7)
8. [Operador Ternario](#id8)
9. [Operador Elvis](#id9)
10. [Operador Fusión Null](#id10)



# Operandos <a name="id0"></a>

Hay tres tipos:

**Unarios**   -5

**Binarios** 10 + 12

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

><strong style="color:red;">NOTA</strong> Si se **compara** un **número** con un **string** o la comparación es entre strings numéricos, cada string se convierte en número y la comparación se realiza numéricamente (esto también se incluye con el uso de switch). Cuando se hacen comparaciones idénticas como === esto no tiene sentido ya que también se comparan los tipos.

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

><strong style="color:red;">NOTA</strong> Debido a la forma en que son interpretados internamente los _floats_, su comparación puede dar resultados inesperados, aunque existen [formas de poder compararlos](http://php.net/manual/es/language.types.float.php#language.types.float.comparison).

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

## 4. Operadores de asignación <a name="id4"></a>
Existen **operadores básicos** y **combinados**:

### 4.1 Operador básico <a name="id4.1"></a>

El **operador básico** de asignación es "=", que actúa como **definidor**, **no** como **igualador**. El valor de una expresión de asignación es el valor que se le ha asignado, esto es: "$x = 3" tiene un valor de 3.

En el **caso** de **arrays**, se asigna un valor a una clave nombrada mediante el operador "=>".

### 4.2 Operador combinado <a name="id4.2"></a>

Los **operadores combinados** permiten usar un valor en una expresión y establecer su nuevo valor como resultado de esa expresión:

```php
$x = 3;
$x += 5;
// $x vale ahora 8

$y = "Hola ";
$y .= ", ¿Qué tal?";
// $y vale ahora "Hola, ¿Qué tal?"
```

Hay una **excepción** a la asignación por valor en PHP, y son los **objetos**, que se asignan por referencia. Los objetos se copian mediante la palabra **clone**.

## 4.3 Asignación por referencia <a name="id4.3"></a>

La **asignación por referencia** significa que las variables apuntan a los **mismos valores**, **sin** hacer ninguna **copia**:

```php
<?php
$x = 3;
$y = &$x;
print "$x, $y"; // Mostrará 3, 3

$x = 5;
print "$x, $y"; // Mostrará 5, 5
```

Las **referencias** actúan como cuando se crea un **acceso directo** o **alias** de un archivo o carpeta en el ordenador.

## 5. Operadores lógicos <a name="id5"></a>

| Operador  	| Resultado                                  	|
|-----------	|--------------------------------------------	|
| $x and $y 	| true si $x y $y son true                   	|
| $x or $y  	| true si uno de los dos es true (o los dos) 	|
| $x xor $y 	| true si sólo uno de los dos es true        	|
| !$x       	| true si $x no es true                      	|
| $x && $y  	| true si $x y $y son true                   	|

>NOTA **&&** y **||** tienen preferencia sobre **and** y **or**

Ejemplos:

```php
$x = true;
$y = false;
if($x and $y){echo 'entra'}else{echo 'no entra'}; // salida no entra
if($x or $y){echo 'entra'}else{echo 'no entra'}; // salida entra
if($x xor $y){echo 'entra'}else{echo 'no entra'}; // salida entra
if(!$x){echo 'entra'}else{echo 'no entra'}; // salida no entra
if($x && $y){echo 'entra'}else{echo 'no entra'}; // salida no entra
if($x || $y){echo 'entra'}else{echo 'no entra'}; // salida entra
```

## 6. Operadores para strings <a name="id6"></a>
Existen dos operadores para strings:

 * **Operador de concatenación** '**.**'  concatena los argumentos derecho e izquierdo.
* **Operador de asignación sobre concatenación** '**.=**', añade el argumento del lado derecho al argumento del lado izquierdo.

*Ejemplos*
```php
<?php
$x = "Hola";
$y = $x . ", ¿Qué tal?"; // $y = "Hola, ¿Qué tal?"

$x = "Hola ";
$x .= ", ¿Qué tal?"; // $x = "Hola, ¿Qué tal?"
```
## 7. Operadores para arrays <a name="id7"></a>

| Operador  	| Resultado                                                                      	|
|-----------	|--------------------------------------------------------------------------------	|
| $x + $y   	| Unión de $x e $y                                                               	|
| $x == $y  	| true si $x e $y tienen las mismas parejas key => value                         	|
| $x === $y 	| true si $x e $y tienen mismas parejas key => value, mismo orden y mismos tipos 	|
| $x != $y  	| true si $x no es igual a $y                                                    	|
| $x <> $y  	| true si $x no es igual a $y                                                    	|
| $x !== $y 	| true si $x no es idéntica a $y                                                 	|

El operador **+** devuelve el array derecho (**$y**) añadido al del izquierdo (**$x**). Si hay keys que existen en ambas, se utilizarán las keys del array izquierdo.

*Ejemplos unión*
```php
$a = array("x" => "perro", "y" => "gato");
$b = array("x" => "pato", "y" => "liebre", "z" => "conejo");
// Unión de $a y $b
$c = $a + $b;
echo "Unión de \$a y \$b: \n";
var_dump($c);
/*
* array (size=3)
  'x' => string 'perro' (length=5)
  'y' => string 'gato' (length=4)
  'z' => string 'conejo' (length=6)
*/
// Unión de $b y $a
$c = $b + $a;
echo "Union de \$b y \$a: \n";
var_dump($c);
/*
* array (size=3)
  'x' => string 'pato' (length=4)
  'y' => string 'liebre' (length=6)
  'z' => string 'conejo' (length=6)
*/
```
*Ejemplo de comparación*

```php
$x = array("perro", "gato");
$y = array(1 => "gato", "0" => "perro");

var_dump($x == $y); // bool(true)
var_dump($x === $y); // bool(false)
```

## 8. Operador Ternario <a name="id8"></a>

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

## 9. Operador Elvis <a name="id9"></a>

El operador Elvis tiene un funcionamiento similar al ternario pero en este caso solo tenemos un valor por defecto

*Ejemplo*

```php
<?php
$y = 5;
$x = $y ?: 'No hay valor'// Salida: 5

$y = null;
$x = $y ?: 'No hay valor'// Salida: No hay valor
?>
```

>NOTA con el operador Elvis en ejemplo mencionado si $y no tuviese valor nos saltaría un error para arreglarlo deberíamos escribirlo con el método isset() => isset($y)?:'No hay valor';

## 10. Operador Fusión Null <a name="id10"></a>

Para resolver el problema con el operador Elvis en el caso de que la variables nos tengan valor, se introdujo en la versión php 7 el operador Fusión Null.

*Ejemplo*

```php
<?php
$y = 5;
$x = $y ?? 'No hay valor'// Salida: 5

$y;
$x = $y ?? 'No hay valor'// Salida: No hay valor
?>
```

