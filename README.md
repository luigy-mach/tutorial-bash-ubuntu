# tutorial-bash-ubuntu
Ejemplos practicos de comandos bash en ubuntu



## comando grep

###### Se desea buscar una palabra en todos los archivos de texto contenidos en el directorio actual
``` 
  grep "palabra_a_buscar"
```
-  Si el directorio contiene directorio y sus subdirectorios (-r)

``` 
  grep -r "palabra_a_buscar"
```

-  Ademas se desea saber en que @linea se encuentra la coincidencia deseada (-n)

``` 
  grep -rn "palabra_a_buscar"
```

