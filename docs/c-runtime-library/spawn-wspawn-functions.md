---
title: "_spawn, _wspawn (Funciones) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_spawn"
  - "_tspawnlp"
  - "_tspawnlpe"
  - "_tspawnve"
  - "_tspawnvp"
  - "_tspawnvpe"
  - "_tspawnl"
  - "spawn"
  - "_tspawnv"
  - "_tspawnle"
  - "wspawn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tspawnve (función)"
  - "_spawn (funciones)"
  - "_tspawnlpe (función)"
  - "tspawnvpe (función)"
  - "procesos, crear"
  - "tspawnve (función)"
  - "_tspawnvp (función)"
  - "spawn (funciones)"
  - "tspawnl (función)"
  - "tspawnlp (función)"
  - "_tspawnvpe (función)"
  - "_tspawnl (función)"
  - "tspawnvp (función)"
  - "tspawnv (función)"
  - "procesos, ejecutar nuevos"
  - "_tspawnv (función)"
  - "tspawnle (función)"
  - "creación de proceso"
  - "_tspawnlp (función)"
  - "tspawnlpe (función)"
  - "_tspawnle (función)"
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _spawn, _wspawn (Funciones)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada una de las funciones de `_spawn` crea y ejecuta un nuevo proceso:  
  
|||  
|-|-|  
|[\_spawnl, \_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[\_spawnv, \_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|  
|[\_spawnle, \_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[\_spawnve, \_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|  
|[\_spawnlp, \_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[\_spawnvp, \_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|  
|[\_spawnlpe, \_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[\_spawnvpe, \_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|  
  
 Las letras del final del nombre de función determinan la variación.  
  
 `e`  
 `envp`, matriz de punteros a la configuración de entorno, se pasa al nuevo proceso.  
  
 `l`  
 Los argumentos de la línea de comandos se pasan individualmente a la función `_spawn`.  Este sufijo se utiliza normalmente cuando varios parámetros a un nuevo proceso se conocen de antemano.  
  
 `p`  
 La variable de entorno `PATH` se usa para buscar el archivo que se va a ejecutar.  
  
 `v`  
 `argv`, matriz de punteros a los argumentos de la línea de comandos, se pasa a la función de `_spawn` .  Este sufijo se utiliza normalmente cuando varios parámetros a un nuevo proceso son variables.  
  
## Comentarios  
 `_spawn` funciona cada crea y ejecuta un nuevo proceso.  Controlan automáticamente argumentos de cadena de multibyte\- carácter según corresponda, reconociendo secuencias de multibyte\- carácter según la página de códigos multibyte actualmente en uso.  Las funciones de `_wspawn` son versiones de caracteres anchos de las funciones de `_spawn` ; no controlan las cadenas de multibyte\- carácter.  Si no, las funciones de `_wspawn` se comportan de forma idéntica a sus homólogos de `_spawn` .  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|  
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|  
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|  
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|  
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|  
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|  
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|  
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|  
  
 Suficiente memoria debe estar disponible para cargar y ejecutar el nuevo proceso.  El argumento de `mode` determina la acción realizada por el proceso de llamada antes y durante `_spawn`.  Los siguientes valores para `mode` se definen en Process.h:  
  
 `_P_OVERLAY`  
 Se superpone a un proceso de llamada con un nuevo proceso, destruyendo el proceso de llamada \(el mismo efecto que las llamadas de `_exec` \).  
  
 `_P_WAIT`  
 Suspende un subproceso de llamada hasta que la ejecución del nuevo proceso se complete \( `_spawn`sincrónico\).  
  
 `_P_NOWAIT` o `_P_NOWAITO`  
 Sigue ejecutando un proceso que llama simultáneamente al nuevo proceso \( `_spawn`asincrónico\).  
  
 `_P_DETACH`  
 Sigue ejecutando el proceso de llamada; el nuevo proceso se ejecuta en segundo plano sin el acceso a la consola o el teclado.  Las llamadas a `_cwait` con el nuevo proceso no \( `_spawn`asincrónico\).  
  
 El argumento de `cmdname` especifica el archivo que se ejecuta mientras el nuevo proceso y puede especificar una ruta de acceso completa \(raíz\), una ruta parcial \(del directorio de trabajo actual\), o simplemente un nombre de archivo.  Si `cmdname` no tiene una extensión de nombre de archivo ni la finaliza con un punto \(.\), la función de `_spawn` primero intenta la extensión de nombre de archivo .com y a continuación la extensión de nombre de archivo .exe, la extensión de nombre de archivo .bat, y finalmente la extensión de nombre de archivo .cmd.  
  
 Si `cmdname` tiene una extensión de nombre de archivo, sólo se utiliza esa extensión.  Si finaliza con un punto, las búsquedas de `cmdname` de llamada de `_spawn` para `cmdname` sin la extensión de nombre de archivo.  `_spawnlp`, `_spawnlpe`, `_spawnvp`, y búsqueda de las funciones de `_spawnvpe` para `cmdname` \(utilizando los mismos procedimientos\) en los directorios especificados por la variable de entorno `PATH` .  
  
 Si `cmdname` contiene un especificador de unidad o las barras diagonales \(es decir, si es una ruta de acceso relativa\), la llamada de `_spawn` busca únicamente el archivo especificado; no se realiza el ningún buscar de ruta.  
  
 En el pasado, algunos de ellos funcionan `errno` determinado a cero en correctamente; el comportamiento actual es dejar `errno` sin tocar en correctamente, especificado por el estándar de C.  Si necesita emular el comportamiento antiguo, establezca `errno` a cero justo antes de llamar a estas funciones.  
  
> [!NOTE]
>  Para garantizar la inicialización y la finalización adecuadas de baraja, no utilice la función de `setjmp` o de `longjmp` para escribir o para permitir una rutina de superposición.  
  
## Argumentos para el proceso generado  
 Para pasar argumentos al nuevo proceso, dé uno o varios punteros a cadenas de caracteres como argumentos en la llamada de `_spawn` .  Estas cadenas de caracteres forman la lista de argumentos para el proceso generado.  La longitud combinada de las cadenas que forman la lista de argumentos para el nuevo proceso no debe superar 1024 bytes.  El carácter null de terminación \(“\\0”\) para cada cadena no se incluye en el recuento, pero los caracteres de espacio \(automáticamente insertados para separar argumentos\) se incluyen.  
  
> [!NOTE]
>  Los espacios insertados en cadenas pueden generar un comportamiento inesperado; por ejemplo, si se pasa a `_spawn` la cadena `"hi there"`, el nuevo proceso obtendrá dos argumentos, `"hi"` y `"there"`.  Si se deseaba que el nuevo proceso abriera un archivo denominado “hi there”, el proceso produciría un error.  Para evitarlo, escriba la cadena entre comillas: `"\"hi there\""`.  
  
> [!IMPORTANT]
>  No pase datos proporcionados por el usuario a `_spawn` sin comprobar expresamente su contenido.  `_spawn` dará lugar a una llamada a [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425), por lo que debe tener presente que los nombres de ruta de acceso incompletos podrían dar lugar a vulnerabilidades de seguridad.  
  
 Puede pasar punteros de argumento como argumentos separados \(en `_spawnl`, `_spawnle`, `_spawnlp`, y `_spawnlpe`\) o como una matriz de punteros \(en `_spawnv`, `_spawnve`, `_spawnvp`, y `_spawnvpe`\).  Debe pasar al menos un argumento, `arg0` o `argv`\[0\], al proceso generado.  Por convención, este argumento es el nombre del programa a medida que se escribe en la línea de comandos.  Un valor diferente no genera un error.  
  
 `_spawnl`, `_spawnle`, `_spawnlp`, y las llamadas de `_spawnlpe` se utilizan normalmente en caso de que el número de argumentos se conoce de antemano.  El argumento `arg0` suele ser un puntero a `cmdname`.  Los argumentos `arg1` a `argn` son punteros a las cadenas de caracteres que forman la nueva lista de argumentos.  Después de `argn`, debe haber un puntero `NULL` para marcar el final de la lista de argumentos.  
  
 `_spawnv`, `_spawnve`, `_spawnvp`, y las llamadas de `_spawnvpe` son útiles cuando hay un número variable de argumentos al nuevo proceso.  Los punteros a los argumentos se pasan como matriz, *`argv`.* El argumento `argv`\[0\] suele ser un puntero a una ruta de acceso en modo real o al nombre del programa en modo protegido; de `argv`\[1\] a `argv`\[`n`\] son punteros a las cadenas de caracteres que forman la nueva lista de argumentos.  El argumento `argv`\[`n` \+1\] debe ser un puntero `NULL` para marcar el final de la lista de argumentos.  
  
## Entorno de proceso generado  
 Los archivos que están abiertos cuando se realiza una llamada de `_spawn` permanecen abiertos en el nuevo proceso.  En `_spawnl`, `_spawnlp`, `_spawnv`, y las llamadas de `_spawnvp` , el nuevo proceso hereda el entorno del proceso de llamada.  Puede utilizar `_spawnle`, `_spawnlpe`, `_spawnve`, y las llamadas de `_spawnvpe` para modificar el entorno para el nuevo proceso pasando una lista de configuración de entorno mediante el argumento de `envp` .  El argumento `envp` es una matriz de punteros de carácter, cada elemento \(excepto el último elemento\) cuyo señala una cadena terminada en null define una variable de entorno.  Esta cadena suele tener el formato `NAME`\=`value`, donde `NAME` es el nombre de una variable de entorno y `value` es el valor de cadena en el que se establece la variable. \(Observe que `value` no está entre comillas\). El último elemento de la matriz de `envp` debe ser `NULL`.  Cuando `envp` propio es `NULL`, el proceso generado hereda la configuración del entorno de proceso primario.  
  
 Las funciones de `_spawn` pueden pasar toda la información sobre los archivos abiertos, incluido el de modalidad de traducción, el nuevo proceso.  Esta información se pasa en modo real con la entrada de `C_FILE_INFO` en el entorno.  El código de inicio procesa normalmente esta entrada y la elimina del entorno.  Sin embargo, si una función de `_spawn` generar un proceso no \- c, permanece esta entrada del entorno.  Imprimir el entorno muestra los caracteres gráficos en la cadena de definición para esta entrada porque la información del entorno se pasa en formato binario en modo real.  No debe tener ningún otro efecto en las operaciones normales.  En modo protegido, información de entorno se pasa en forma de texto y por consiguiente no contiene ningún carácter gráfico.  
  
 Debe explícitamente vaciar \(mediante `fflush` o `_flushall`\) o cerrar cualquier secuencia antes de llamar a una función de `_spawn` .  
  
 Los nuevos procesos creados mediante llamadas a las rutinas de `_spawn` no mantienen los valores de la señal.  En su lugar, los valores de la señal de reinicios del proceso generado en el valor predeterminado.  
  
## El redireccionamiento generado  
 Si se llama a `_spawn` DLL o de una aplicación de GUI y desea redirigir el resultado a una canalización, tiene dos opciones:  
  
-   Utilice la API Win32 para crear una canalización, la llamada [AllocConsole](http://msdn.microsoft.com/library/windows/desktop/ms681944), establezca los valores de identificador en la estructura de inicio, y la llamada [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425).  
  
-   Llame a [\_popen, \_wpopen](../c-runtime-library/reference/popen-wpopen.md) que crean una canalización e invocar la aplicación mediante **cmd.exe \/c** \(o **command.exe \/c**\).  
  
## Ejemplo  
  
```  
// crt_spawn.c  
// This program accepts a number in the range  
// 1-8 from the command line. Based on the number it receives,  
// it executes one of the eight different procedures that  
// spawn the process named child. For some of these procedures,  
// the CHILD.EXE file must be in the same directory; for  
// others, it only has to be in the same path.  
//  
  
#include <stdio.h>  
#include <process.h>  
  
char *my_env[] =  
{  
   "THIS=environment will be",  
   "PASSED=to child.exe by the",  
   "_SPAWNLE=and",  
   "_SPAWNLPE=and",  
   "_SPAWNVE=and",  
   "_SPAWNVPE=functions",  
   NULL  
};  
  
int main( int argc, char *argv[] )  
{  
   char *args[4];  
  
   // Set up parameters to be sent:   
   args[0] = "child";  
   args[1] = "spawn??";  
   args[2] = "two";  
   args[3] = NULL;  
  
   if (argc <= 2)  
   {  
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );  
      exit( 1 );  
   }  
  
   switch (argv[1][0])   // Based on first letter of argument   
   {  
   case '1':  
      _spawnl( _P_WAIT, argv[2], argv[2], "_spawnl", "two", NULL );  
      break;  
   case '2':  
      _spawnle( _P_WAIT, argv[2], argv[2], "_spawnle", "two",   
               NULL, my_env );  
      break;  
   case '3':  
      _spawnlp( _P_WAIT, argv[2], argv[2], "_spawnlp", "two", NULL );  
      break;  
   case '4':  
      _spawnlpe( _P_WAIT, argv[2], argv[2], "_spawnlpe", "two",   
                NULL, my_env );  
      break;  
   case '5':  
      _spawnv( _P_OVERLAY, argv[2], args );  
      break;  
   case '6':  
      _spawnve( _P_OVERLAY, argv[2], args, my_env );  
      break;  
   case '7':  
      _spawnvp( _P_OVERLAY, argv[2], args );  
      break;  
   case '8':  
      _spawnvpe( _P_OVERLAY, argv[2], args, my_env );  
      break;  
   default:  
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );  
      exit( 1 );  
   }  
   printf( "from SPAWN!\n" );  
}  
```  
  
  **resultado del proceso secundario**  
**además de SPAWN\!**   
## Vea también  
 [Control de proceso y de entorno](../c-runtime-library/process-and-environment-control.md)   
 [abort](../c-runtime-library/reference/abort.md)   
 [atexit](../c-runtime-library/reference/atexit.md)   
 [\_exec, \_wexec \(Funciones\)](../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [\_flushall](../c-runtime-library/reference/flushall.md)   
 [\_getmbcp](../c-runtime-library/reference/getmbcp.md)   
 [\_onexit, \_onexit\_m](../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_setmbcp](../c-runtime-library/reference/setmbcp.md)   
 [system, \_wsystem](../c-runtime-library/reference/system-wsystem.md)