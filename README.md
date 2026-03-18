###**Laboratorio de Sistemas Operativos: Introducción al lenguaje C**

##**Práctica No. 1**

#**a) Integrantes:**

- Michael Stiven Tabares Tobón
Correo: michael.tabares@udea.edu.co
Cédula: -------

- Maria Fernanda Atencia Oliva
Correo: mariaf.atencia@udea.edu.co
Cédula: 1064980223

#**b)  Documentación de todas las funciones desarrolladas en el código.**

- **Wcat**
    - *Descripción:* Esta función se encarga de leer el contenido de uno o más archivos pasados como argumentos en la línea de comandos y mostrarlo en la salida estándar (pantalla).
    - *Parámetros:* 
        - argc: número de argumentos recibidos por el programa desde la linea de comandos.
        - argv: arreglo de cadenas que contiene los argumentos pasados al programa, donde cada argumento es el nombre de un archivo a leer.
    - *Retorno:* Devuelve **0** si la función se ejecuta correctamente, o **1** si ocurre un error al abrir alguno de los archivos.
    - *Funcionamiento:* 
        1. Inicialmente, se verifica si se recibieron argumentos, en caso de que no (argc == 1) se termina el programa.
        2. Se itera sobre cada argumento (archivo) recibido, intentando abrirlo con la función `fopen`.
        3. Si el archivo no se puede abrir, se muestra un mensaje de error en la salida estándar de errores, se retorna **1** y finaliza.
        4. Si el archivo se abre correctamente, se lee su contenido línea por línea usando `fgets()` y se imprime en la salida estándar.
        5. Finalmente, se cierra el archivo con `fclose()` y se continúa con el siguiente archivo hasta procesar todos los argumentos.
- **Wgrep**
    - *Descripción:* Esta función busca una cadena específica dentro de uno o más archivos pasados como argumentos en la línea de comandos y muestra las líneas que contienen esa cadena.
    - *Parámetros:* 
        - argc: número de argumentos recibidos por el programa desde la linea de comandos.
        - argv: arreglo de cadenas que contiene los argumentos pasados al programa, donde el primer argumento (argv[1]) es la cadena a buscar y los siguientes (argv[2] en adelante) son los nombres de los archivos a revisar.
    - *Retorno:* Devuelve **0** si la función se ejecuta correctamente, o **1** si ocurre un error al abrir alguno de los archivos (por ejemplo, argumentos insuficientes o fallo al abrir un archivo).
    - *Funcionamiento:* 
        1. Se verifica que se hayan recibido suficientes argumentos (al menos dos), en caso contrario se termina el programa.
        2. El primer argumento (argv[1]) se guarda como la cadena a buscar.
        3. Se itera sobre cada archivo pasado como argumento (desde argv[2] hasta argv[argc-1]), intentando abrirlo con `fopen`.
        4. Si el archivo no se puede abrir, se muestra un mensaje de error en la salida estándar de errores, se retorna **1** y finaliza.
        5. Si el archivo se abre correctamente, se lee su contenido línea por línea usando `fgets()`, y para cada línea se verifica si contiene la cadena buscada utilizando `strstr()`.
        6. Si la línea contiene la cadena buscada, se imprime esa línea en la salida estándar.
        7. Finalmente, se cierra el archivo con `fclose()` y se continúa con el siguiente archivo hasta procesar todos los argumentos.
- **Wzip**
    - *Descripción:* Esta función comprime el contenido de uno o más archivos pasados como argumentos en la línea de comandos utilizando una técnica de compresión simple basada en la repetición de caracteres.
    - *Parámetros:* 
        - argc: número de argumentos recibidos por el programa desde la linea de comandos.
        - argv: arreglo de cadenas que contiene los argumentos pasados al programa, donde cada argumento es el nombre de un archivo a comprimir.
    - *Retorno:* Devuelve **0** si la función se ejecuta correctamente, o **1** si ocurre un error al abrir alguno de los archivos.
    - *Funcionamiento:* 
        1. Se verifica que se hayan recibido argumentos, en caso contrario se termina el programa.
        2. Inicializa variables:
            * prev: almacena el carácter anterior.
            * count: lleva el conteo de repeticiones consecutivas.
            * firstChar: indica si se está procesando el primer carácter.
        3. Se itera sobre cada archivo pasado como argumento, intentando abrirlo con `fopen`.
        4. Si el archivo no se puede abrir, se muestra un mensaje de error en la salida estándar de errores, se retorna **1** y finaliza.
        5. Si el archivo se abre correctamente, se lee su contenido carácter por carácter usando `fgetc()`, y se cuenta cuántas veces consecutivas aparece cada carácter.
        6. Para cada secuencia de caracteres repetidos, se escribe en la salida estándar el número de repeticiones seguido del carácter correspondiente (por ejemplo, "3a" para tres 'a' seguidas).
        7. Finalmente, se cierra el archivo con `fclose()` y se continúa con el siguiente archivo hasta procesar todos los argumentos.
- **Wunzip**
    - *Descripción:* Esta función descomprime el contenido generado por la función Wzip, leyendo una secuencia de caracteres comprimidos y expandiéndolos a su forma original.
    - *Parámetros:* 
        - argc: número de argumentos recibidos por el programa desde la linea de comandos.
        - argv: arreglo de cadenas que contiene los argumentos pasados al programa, donde cada argumento es el nombre de un archivo comprimido a descomprimir.
    - *Retorno:* Devuelve **0** si la función se ejecuta correctamente, o **1** si ocurre un error al abrir alguno de los archivos.
    - *Funcionamiento:* 
        1. Se verifica que se hayan recibido argumentos, en caso contrario se termina el programa.
        2. Se itera sobre cada archivo pasado como argumento, intentando abrirlo con `fopen`.
        3. Si el archivo no se puede abrir, se muestra un mensaje de error en la salida estándar de errores, se retorna **1** y finaliza.
        4. Si el archivo se abre correctamente, se lee su contenido carácter por carácter usando `fgetc()`, interpretando cada par de caracteres como un número (cantidad) seguido de un carácter (el carácter a repetir).
        5. Para cada par leído, se escribe en la salida estándar el carácter repetido la cantidad de veces indicada por el número (por ejemplo, "3a" se expandiría a "aaa").
        6. Finalmente, se cierra el archivo con `fclose()` y se continúa con el siguiente archivo hasta procesar todos los argumentos.