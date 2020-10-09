# Herramienta para uso exclusio de Laboratorio Azul

## Permite importar datos hacia la aplicación Web de clientes

Esta herramienta es la encargada de migrar los datos en archivos con formato **CSV** de forma programada como manual. Además permite enviar archivos comprimidos *Zip* con los ficheros PDF de cada uno de los análisis finalizados.

### Instalación y configuración

1.    Descargue la última versión mediante el siguiente enlace: http://pragmatica.com.ar/veremos

2.    Descomprima el contenido del archivo *Zip* del punto anterior en una carpeta deseada (existente o nueva).

3.    Defina la variable de entorno **IMPORTACION-WEB** con el siguiente valor: *http://laboratorioazul.com.ar/clientes/js/cfg_importacion*

        A.    Abra el **Panel de control** y diríjase a **Sistema y seguridad** / **Sistema**.

        B.    Clic sobre **Configuración avanzada del sistema** y luego sobre el botón **Variables de entorno...**

        C.    En el área definida como *Variables del sistema* haga clic en el botón **Nueva...**.

        D.    En el cuadro de diálogo *Nueva variable del sistema* ingrese los datos mensionados en el punto 3.

        E.    Acepte todos los cambios y reinicie el equipo.


### Modo de uso

La herramienta puede utilizarse de dos formas:

```
la-importar-web -probar
```
> **Permite realizar una prueba de conexión al servidor Web.** Debería utilizarse una vez realizada la instalación, y cuando la configuración del equipo o la red cambien.

```
la-importar-web <archivos_importar> [-enc <valor-buscar | cantidad>]
```

> **Comienza el proceso de importación** según los parámetros definidos.

> El parámetro **<archivos_importar>** es una lista de uno o más archivos a incluir, separados por espacios. Puede indicar el nombre completo de cada uno o incluso utilizar comodines para indicar todos los archivos de una extensión (por ejemplo **\*.csv**).

> El parámetro **-enc** permite indicar la cantidad de líneas utilizadas como encabezado en los archivos *CSV*. También puede indicar un texto que indique el comienzo de la línea que separa el encabezado del resto del contenido. Consulte los ejemplos presentados más abajo.


### Funcionamiento

1.    Las extensiones aceptadas son: **.csv**, **.txt** y **.zip**. Cualquier otro tipo de archivo será simplemente ignorado.

2.    Los archivos con extensión **.csv** o **.txt** serán procesados como *CSV*. Si alguno de los archivos no supera la validación todo el proceso será cancelado. Las líneas "en blanco" en este tipo de archivos serán ignoradas.

3.    Para el caso de los archivos **.zip** solo serán enviados sin ningún tipo de validación. Estos archivos comprimidos deben contener los ficheros *PDF* con los respectivos análisis finalizados. Recuerde que el proceso de importación que se inicia una vez enviados todos los archivos ignora cualquier fichero que no sea de este tipo.

### Ejemplos

```
la-importar-web c:\temp\*.csv c:\temp\*.zip
```

> Importa todos los archivos **.csv** y **.zip** dentro de la carpeta **c:\temp**.

```
la-importar-web c:\temp\*.csv c:\temp\*.zip -enc 2
```

> El mismo ejemplo pero indicando que los archivos *CSV* cuentan con un encabezado de **2** líneas.

```
la-importar-web c:\temp\*.csv c:\temp\*.zip -enc "---"
```

> Una vez más el mismo ejemplo pero esta vez indicando que los archivos *CSV* tienen varias líneas de encabezado donde la última de este grupo comienza con **3** guiones.

```
la-importar-web veterinarios.csv *.txt *.zip
```

> Un ejemplo alternativo que muestra como indicar varios archivos con nombre único o mediante comodines. En este caso en la carpeta actual donde se encuentre.

---

Última fecha de actualización: **8/10/2020**. Desarrollado por **Pragmática** (http://pragmatica.com.ar)
