# Pasando sql a Exel
```php
function pasar_exel_cuestionario_gestor($datos)
{
    if(!empty($datos)) {

        $filename = "cuestionario.xls";
        
        header("Content-Type: application/vnd.ms-excel");
        
        header("Content-Disposition: attachment; filename=".$filename);
        $mostrar_columnas = false;
        foreach($datos as $dato) {
        if(!$mostrar_columnas) {
        echo implode("\t", array_keys($dato)) . "\n";
        $mostrar_columnas = true;
        }
        echo implode("\t", array_values($dato)) . "\n";
        }
        }else{
        echo 'No hay datos a exportar';
        }
        exit;
}
```
