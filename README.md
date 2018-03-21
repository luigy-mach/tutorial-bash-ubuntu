# tutorial-bash-ubuntu
Ejemplos practicos de comandos bash en ubuntu



## Comando `grep`

#### Se desea buscar una palabra en todos los archivos de texto contenidos en el directorio actual
###### NOTA: `grep` busca la sentencia deseada, sin importar si esta esta o no contenida dentro de otra palabra 

-  Si el directorio `no contiene directorio y sus subdirectorios`
``` 
  grep "palabra_a_buscar"
```
-  Si el directorio contiene `directorio y sus subdirectorios` (-r)

``` 
  grep -r "palabra_a_buscar"
```

-  Ademas se desea saber en que ` número de linea` se encuentra la coincidencia deseada (-n)

``` 
  grep -rn "palabra_a_buscar"
```

-  Si se desea realizar una busqueda en una ubicacion diferente a donde nos encontramos 
    > grep -rn [palabra_a_buscar] [ubicacion]

``` 
  grep -rn "palabra_a_buscar" .
```


## Comando `find`

#### Se desea buscar una archivo en el directorio actual
###### NOTA: `find` a diferencia de `grep` busca la sentencia deseada como coindicencia exacta, y de manera recursiva en todo el contenido del directorio. 


>-  find [ubicacion] \-name "[nombre_del_archivo]"
>   -  ejemplo en [ubicacion] : "." (direcorio actual) "/" (desde la raiz del sistema)
``` 
  find  . -name "palabra_a_buscar"
```

-  Si se desea buscar varios archivos con mismo final-de-palabra (extension de archivo por ejemplo: "\*.mp4")  
``` 
  find . -name  "*.mp4"
```


-  Si se desea buscar varios archivos con mismo inicio-de-palabra (extension de archivo por ejemplo: "a\*")  
``` 
  find . -name  "a*"
```

-  Si se desea buscar varios archivos sin importar la posicion de la palabra  (extension de archivo por ejemplo: "\*palabra-a-buscar\*")  
``` 
  find . -name  "*palabra-a-buscar*"
```




