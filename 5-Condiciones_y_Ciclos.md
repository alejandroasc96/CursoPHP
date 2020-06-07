**Índice**   
1. [ if](#id1)
2. [ else](#id2)
3. [ elseif/else if](#id3)
4. [ while](#id4)
   -  [do-while](#id4.1)
5. [for](#id5)
6. [foreach](#id6)
7. [break](#id7)
8. [continue](#id8)
9. [switch](#id9)
10. [declare](#id10)
11. [return](#id11)
12. [include/include_once](#id12)
13. [require/require_once](#id13)
14. [goto](#id14)
15. [Sintaxis alternativas](#id15)

## 1. if <a name="id1"></a>

La estructura de control **if** permite la ejecución condicional de fragmentos de código.
```php
<?php
if ($x > $y) {
    echo "$x es mayor que $y";
}
```
> NOTA Las sentencias if se pueden incluir unas dentro de otras indefinidamente.

## 2. else <a name="id2"></a>
Sirve para ejecutar una sentencia cuando otra no se cumple. **else** extiende una sentencia **if**, y se ejecuta cuando ésta es **false**. Siguiendo el ejemplo anterior:

```php
<?php
if ($x > $y) {
    echo "$x es mayor que $y";
} else {
    echo "$y es mayor que $x";
}
?>
```
## 3. elseif / else if <a name="id3"></a>

Es una combinación entre **if** y **else**. Se ejecuta cuando if es **false**, pero sólo si la expresión condicional del **elseif** es **true**.

*Ejemplo*

```php
<?php
if ($x > $y) {
    echo "$x es mayor que $y";
} elseif ($x == $y) {
    echo "$x es igual que $y";
} else {
    echo "$y es mayor que $x";
}
?>
```
## 4. while <a name="id4"></a>

Es el tipo más sencillo de **loop** en **PHP**. Se ejecutan las sentencias dentro del **while** siempre y cuando se evalúen como true. El valor de la expresión se comprueba cada vez al inicio del loop, y la ejecución no se detendrá hasta que finalice la **iteración**

>**NOTA** Si la expresión **while** se evalúa como **false**, las sentencias no se ejecutarán ni siquiera una vez.

```php
<?php
$i = 1;
while($i <= 10){
    echo $i;
    $i++;
}
?>
```

## 5. do-while <a name="id5"></a>

Muy similares a los loops **while**, simplemente aquí la expresión para el loop se verifica al final en lugar de al principio, esto garantiza que el código se ejecute por lo menos la primera vez.

```php
<?php
$i = 0;
do {
    echo $i;
} while ($i > 0);
?>
```

## 6. for <a name="id6"></a>

Los loops(búcles) **for** son los más complejos en PHP.

```php
<?php
for ($i = 1; $i <= 10; $i++) {
    echo $i;
} // Devuelve 123456789
/* Explicación
- Las expresiones o conjunto de expresiones van separadas por punto y coma ; y sólo hay 3.
- La primera expresión, $i = 1, se ejecuta una vez incondicionalmente al comienzo del bucle.
- La segunda expresión, $i <= 10, es una condición, si es true, se ejecutará la tercera expresión.
- La tercera expresión, $i++, es la acción a realizar si se cumple la segunda expresión.
*/
```

Cada una de las expresiones pueden estar **vacías** o contener **múltiples expresiones**, lo que resulta útil en ciertas ocasiones. Si la expresión 2 está vacía, el loop será definido como **true**.

```php
<?php
// Todos los siguientes ejemplos son válidos y devuelven lo mismo, 123456789
// EJEMPLO 1
for($i = 1; $i <= 10; $i++) {
    echo $i;
}

// EJEMPLO 2
for ($i = 1; ; $i++){
    if($i > 10) {
        break;
    }
    echo $i;
}

// EJEMPLO 3
$i = 1;
for( ; ; ){
    if($i > 10){
        break;
    }
    echo $i;
    $i++;
}

// EJEMPLO 4
for ($i = 1, $j = 0; $i <= 10; $j += $i, print $i, $i++);
```

Uno de los u**sos más comunes** que vemos en el uso de los **loop for** se da a la hora de tener que **recorrer** un **array**.

```php
<?php
$gente = array(
    array('nombre' => 'Carlos', 'salt' => 123),
    array('nombre' => 'Maria', 'salt' => 124));
// Numero de gente
$size = count($gente);
// Loop que da un salt de 4 dígitos aleatorio
for ($i=0; $i < $size; ++$i) {
    $gente[$i]['salt'] = mt_rand(0000, 9999);
}
var_dump($gente);
/*
* array (size=2)
  0 =>
    array (size=2)
      'nombre' => string 'Carlos' (length=6)
      'salt' => int 2029
  1 =>
    array (size=2)
      'nombre' => string 'Maria' (length=5)
      'salt' => int 9724
*/
?>
```

## 7. foreach <a name="id7"></a>

**foreach** permite una forma fácil de iterar sobre **arrays** u **objetos**.

Cuando **foreach** inicia su ejecución, el puntero apunta directamente al primer elemento del **array**, por lo que no es necesario llamar a la función reset() antes que un loop foreach. Es recomendable no cambiar el puntero dentro del loop.

Se puede iterar de las siguientes dos formas:

```php
<?php
// Devuelve directamente el value de cada key, comenzando desde el primero
foreach ($array as $value) {
    // Lo que se desee mostrar
}
// Devuelve cada key con cada value, para poder trabajar con cualquiera de los dos
foreach ($array as $key => $value){
    // Lo que se desee mostrar
}
?>
```
### 7.1 Modificando elementos del array <a name="id7.1"></a>
Se pueden modificar los elementos del array dentro del loop, anteponiendo & a $value (asignándolo por referencia).

```php
<?php
$array = array(1, 2, 3, 4);
foreach ($array as &$value){
    $value = $value * 2;
}
// cada valor del array vale ahora : 2, 4, 6, 8
unset($value);
```
La función **[unset()](https://www.anerbarrena.com/php-unset-4808/)** elimina la referencia del último elemento, pero el array sigue valiendo 2, 4, 6, 8. Es recomendable hacer unset() porque la referencia del $valor y el último elemento del array permanecen aún después del loop foreach.

**foreach** y **list** pueden devolver los mismos resultados de la siguiente forma:

```php
<?php
$array = array("uno", "dos", "tres");
reset($array);
while (list($clave, $valor) = each($array)){
    echo "Clave: $clave; Valor: $valor </br>";
}

foreach ($array as $clave => $valor){
    echo "Clave: $clave; Valor: $valor </br>";
}
```
*Explicación*

La función **[list()](https://www.php.net/manual/es/function.list.php)** coge un array y lo **convierte** en **variables** **individuales**.

**each()** coge un array y devuelve el key y value actuales, es decir, donde está apuntando el cursor en el array. Es necesario hacer un reset() del array para asegurarse que el cursor comienza desde el principio (cosa que no es necesaria con el foreach).

Suele ser más óptimo y legible utilizar el **foreach** para iterar, aunque ambos se utilizan más o menos con la misma frecuencia.


### 7.2 Arrays multidimensionales y doble foreach <a name="id7.2"></a>

```php
<?php
$x = array();
$x[0][0] = "a";
$x[0][1] = "b";
$x[1][0] = "y";
$x[1][1] = "z";

foreach ($x as $primero){
    foreach ($primero as $segundo){
        echo "$segundo" . "</br>";
        }
    }
?>
```
>**NOTA** En el ejemplo anterior, si no se hace doble foreach con $x y se hace sólo un foreach surgirá un *Notice: Array to string conversion*.

Desde **PHP 5.5** se puede recorrer un **array de arrays** y utilizar el segundo array para asignar variables:

```php
<?php
$array = array(
    array('azul', 'rojo'),
    array('verde', 'amarillo')
    );

foreach ($array as list($a, $b)) {
    echo "A: $a; B: $b" . "</br>";
}
// Devuelve: A: azul; B: rojo</br>A: verde; B: amarillo</br>
?>
```

## 8. break <a name="id8"></a>
break termina la ejecución de las siguientes estructuras: for, foreach, while, do-while y switch.

Se puede añadir un argumento numérico opcional que indica de cuántas estructuras debe salir. El valor por defecto es 1:

```php
<?php
// Ejemplo sin valor numérico
$array = array('uno', 'dos', 'parar', 'tres');
while(list(, $valor) = each($array)){
    if($valor == 'parar'){
        break;
    }
    echo "$valor</br>";
}
// Ejemplo con valor numérico
$i = 0;
while (++$i){
    switch($i){
        case 5:
            echo "He llegado a 5 </br>";
            break 1; // Aquí sólo saldría del switch
        case 10:
            echo "He llegado a 10 </br>";
            break 2; // Sale del switch y del while
        default:
            break;
    }
}
?>
```

## 9. continue <a name="id9"></a>

Se **utiliza dentro de las estructuras iterativas** para **saltar** el resto de la iteración actual del loop y **continuar a la siguiente iteración** para su ejecución:

```php
<?php
for ($i=0; $i < 10; $i++) {
    if($i % 2 == 0)
        continue;
    print "$i ";
} // Devuelve 1 3 5 7 9

?>
```
*Explicación:*
El código anterior hace que cuando el número sea par, continue se ejecute y no muestre el print de después, sino que vuelva a empezar con la siguiente iteración. print sólo se ejecutará cuando $i sea impar.

Al igual que con **break**, se puede añadir un número a **continue** que indica el número de niveles de loops debe saltar:

```php
<?php
$i = 0;
while ($i++ < 5){
    echo "Uno </br>";
    while (1) {
        echo "Dos </br>";
        while (1) {
            echo "Tres </br></br>";
            continue 3;
        }
        echo "Esto no aparece.";
    }
    echo "Esto tampoco aparece.";
}
?>
```
*Explicación:*
En este ejemplo, cuando llega a **continue 3**, comienza de nuevo la iteración, y se comprueba otra vez la condición ($i++ < 5). Si se pone, por ejemplo, continue 2, salta al segundo while, cuya condición siempre se cumple, y se produce un **loop infinito** que imprime "Dos Tres" continuamente.

## 10. switch <a name="id10"></a>

**switch** es como una serie de sentencias **if**. Es útil para comparar una misma **variable o expresión** con valores direrentes y ejecutar un código diferente a otro dependiendo de esos valores.

```php
<?php
switch ($i) {
    case "perro":
        echo "\$i es un perro";
        break;
    case "gato":
        echo "\$i es un gato";
        break;
    case "avestruz":
        echo "\$i es un avestruz";
        break;
}
?>
```
Cuando una sentencia case coincide con el valor de la sentencia switch, PHP ejecuta el código dentro del case. PHP sigue ejecutando las sentencias hasta el final o hasta que choca con un break, que entonces finaliza la iteración.

>**NOTA** Si se omite break, swith ejecutará todos los cases restantes cuando encuentra uno que cumpla con la condición

En caso de que no haya ningún case válido, puede utilizarse default, para ejecutar algo cuando no se cumplen los case:

```php
<?php
switch($i) {
    case 0:
        echo "i es igual a 0";
        break;
    case 1:
        echo "i es igual a 1";
        break;
    default:
        echo "i no es ni 0 ni 1";
}
?>
```

* En los cases sólo se permiten **tipos simples**: int, float y string. Los **arrays y objetos** pueden utilizarse si se muestran como un tipo simple.
* Es posible escribir punto y coma ";" en lugar de dos puntos ":" después de un case.

## 11. declare <a name="id11"></a>

**declare** sirve para fijar directivas de ejecución para un bloque de código.

## 12. return <a name="id12"></a>
_**return**_ devuelve el control del programa al módulo que lo invoca. La ejecución vuelve a la siguiente declaración después del módulo que lo invoca. 

*   Si se usa en una **función**, return hace que la función termine, devolviendo los argumentos que le sigan como valor de la llamada a la función. 
*   Si se llama **globalmente**, finaliza la ejecución del script actual. 
*   Si el archivo actual fue incluido o requerido, el control regresa al archivo que llama al _**include**_ o _**require**_.
*   Si el archivo está incluído con _**include**_, los argumentos del return se devolverán como valor de la llamada _**include**_.
*   Si return se usa en el **archivo principal del script**, termina la ejecución del script.
*   También termina la ejecución de una sentencia _**eval()**_.

Es recomendable **no** usar paréntesis después de return. 

### 13. include/include_once

_**include**_ incluye y ejecuta un archivo. 

Los archivos se incluyen en base a la **ruta de acceso dada**, y si no se proporciona ninguna, se utiliza el [include_path](http://php.net/manual/es/ini.core.php#ini.include-path). Si el archivo tampoco se encuentra en el **include_path** se mirará en el **propio directorio** desde donde se hace la llamada, antes de devolver un **mensaje warning**. Es en el tipo de mensaje donde difiere con require, que devuelve un **error fatal**.  

*   Si se define una ruta absoluta (en Linux comenzando por /) o relativa al directorio actual (comenzando con . o ..) el **include_path** será ignorado.

Las variables del archivo del include estarán disponibles en el archivo desde el que se solicita:

```
<?php
// archivo1.php
$color = 'azul';
// archivo2.php
echo $color; // Devuelve un Notice: Undefined variable: color
include 'archivo1.php';
echo $color; // Devuelve azul
```

*   Si la inclusión se hace dentro de una **función**, el contenido del archivo es como si estuviera dentro de esa función, por tanto su contenido tendrá el mismo ámbito.
*   Cuando se incluye un archivo, el intérprete abandona el modo PHP e ingresa al modo HTML al comienzo del archivo incluído, y se reanuda de nuevo al final. Es por ello que cualquier código que tenga que ser interpretado como PHP debe incluir las etiquetas válidas de comienzo  y terminación (**<?php ?>**).

Si están activadas las **envolturas URL include**, se puede incluir un archivo a través de una URL (mediante HTTP u [otro protocolo](http://php.net/manual/es/wrappers.php)). Si el servidor objetivo interpreta el archivo como PHP, las variables se pueden pasar al archivo usando un string de petición como con HTTP GET. El resultado no es lo mismo que en local, pues el archivo se ejecuta en el servidor remoto y el resultado se incluye en el local.

```
<?php
include 'http://www.ejemplo.com/archivo.php?var=1';
$var = 1;
```

Por **seguridad** es mejor que el archivo remoto se procese en el servidor remoto y se reciba sólo la salida, con [_readfile()_](http://php.net/manual/es/function.readfile.php).

Es posible devolver valores desde los archivos include mediante **return**:

```
// archivo1.php con return
<?php
$var = 'PHP';
return $bar;
?>
// archivo2.php sin return
<?php
$var = 'PHP';
?>
//archivo3.php
<?php
$foo = include 'archivo1.php';
echo $foo; // devuelve PHP

$bar = include 'archivo2.php';
echo $bar; // Devuelve 1 porque el include ha sido exitoso, pero no tiene valor return. Si no hubiera funcionado devolvería false y un E_WARNING.
```

También se pueden incluir archivos PHP en variables con un buffering de salida:

```
<?php
$string = get_include_contents('archivo.php');

function get_include_contents($filename) {
    if(is_file($filename)) {
        ob_start();
        include $filename;
        return ob_get_clean();
    }
    return false;
}
```

Para incluir archivos automáticamente en scripts ver [auto_preprend_file](http://php.net/manual/es/ini.core.php#ini.auto-prepend-file) y [auto_append_file](http://php.net/manual/es/ini.core.php#ini.auto-append-file) de _php.ini_.

_**include_once**_ incluye el archivo especificado sólo una vez, si se incluye más veces tan sólo devuelve true. Es útil en casos donde el mismo fichero se podría incluir y evaluar más de una vez, para evitar así redefinir funciones o reasignar valores a variables.

### 14. require/require_once

_**require**_ hace lo mismo que _**include**_ pero en caso de fallar devuelve un **error fatal** de nivel **E_COMPILE_ERROR**, por lo que no puede continuar el script. _include_ sólo emite un **E_WARNING** que permite continuar el script.

_**require_once**_ es igual que _**require**_ pero PHP comprobará si el archivo ya ha sido incluído, y si es así no se incluirá otra vez. 

### 15. goto

_**goto**_ se utiliza para saltar a otra sección del script. La **etiqueta de destino** debe estar dentro del mismo fichero y ámbito. 

```
<?php
goto x;
echo 'Hola!';

x:
echo 'Adios!';  // sólo se imprimirá Adios!
```

También puede utilizarse en un **loop** en lugar de _**break**_:

```
<?php
for($i=0, $j=50; $i<100; $i++) {
    while($j--) {
        if($j==17) goto end;
        }
    }
echo "i = $i";
end:
echo 'j llegó a 17';
```

### 16. Sintaxis alternativas

PHP ofrece una **sintaxis alternativa** para _if_, _while_, _for_, _foreach_ y _switch_. Se cambia el corchete de apertura por dos puntos ":" y el corchete de cierre por _**endif**_, _**endwhile**_, _**endfor**_, _**endforeach**_, o _**endswitch**_. 

```
<?php if ($x == 3): ?>
X es 3
<?php endif; ?>
```

"X es 3" es un bloque HTML que se mostraría sólo si se cumple la condición.

Con **else** y **elseif**:

```
<?php
if($x == 3):
    echo "x igual a 3";
elseif ($x == 4):
    echo "x igual a 4";
else:
    echo "x no es ni 3 ni 4";
endif;
```
