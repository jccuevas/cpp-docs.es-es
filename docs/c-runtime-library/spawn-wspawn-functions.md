---
title: _spawn, _wspawn (Funciones) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _spawn
- _tspawnlp
- _tspawnlpe
- _tspawnve
- _tspawnvp
- _tspawnvpe
- _tspawnl
- spawn
- _tspawnv
- _tspawnle
- wspawn
dev_langs:
- C++
helpviewer_keywords:
- _tspawnve function
- _spawn functions
- _tspawnlpe function
- tspawnvpe function
- processes, creating
- tspawnve function
- _tspawnvp function
- spawn functions
- tspawnl function
- tspawnlp function
- _tspawnvpe function
- _tspawnl function
- tspawnvp function
- tspawnv function
- processes, executing new
- _tspawnv function
- tspawnle function
- process creation
- _tspawnlp function
- tspawnlpe function
- _tspawnle function
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0634aeb37d0374f5e6e1dfae0ac004792c279fc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="spawn-wspawn-functions"></a>Funciones _spawn y _wspawn
Cada una de las funciones `_spawn` crea y ejecuta un nuevo proceso:  
  
|||  
|-|-|  
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|  
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|  
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|  
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|  
  
 Las últimas letras del nombre de función determinan la variación.  
  
 `e`  
 `envp`, una matriz de punteros a la configuración de entorno, se pasa al nuevo proceso.  
  
 `l`  
 Los argumentos de la línea de comandos se pasan individualmente a la función `_spawn`. Este sufijo suele usarse cuando el número de parámetros para el nuevo proceso se conoce de antemano.  
  
 `p`  
 La variable de entorno `PATH` se usa para buscar el archivo que se va a ejecutar.  
  
 `v`  
 `argv`, una matriz de punteros a los argumentos de la línea de comandos, se pasa a la función `_spawn`. Este sufijo suele usarse cuando el número de parámetros para el nuevo proceso es variable.  
  
## <a name="remarks"></a>Comentarios  
 Cada una de las funciones `_spawn` crea y ejecuta un nuevo proceso. Controlan automáticamente argumentos de cadenas de caracteres multibyte según corresponda, reconociendo secuencias de caracteres multibyte en función de la página de códigos multibyte actualmente en uso. Las funciones `_wspawn` son versiones de caracteres anchos de las funciones `_spawn`; no controlan cadenas de caracteres multibyte. De lo contrario, las funciones `_wspawn` se comportan de forma idéntica a sus `_spawn` equivalentes.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|  
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|  
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|  
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|  
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|  
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|  
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|  
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|  
  
 Debe haber suficiente memoria disponible para cargar y ejecutar el nuevo proceso. El argumento `mode` determina la acción que realiza el proceso de llamada antes y durante `_spawn`. Los siguientes valores de `mode` se definen en Process.h:  
  
 `_P_OVERLAY`  
 Superpone un nuevo proceso al proceso de llamada, lo que destruye el proceso de llamada (mismo efecto que las llamadas `_exec`).  
  
 `_P_WAIT`  
 Suspende un subproceso de llamada hasta que se complete la ejecución del proceso nuevo (`_spawn` sincrónica).  
  
 `_P_NOWAIT` o `_P_NOWAITO`  
 Continúa ejecutando un proceso de llamada al mismo tiempo que el nuevo proceso (`_spawn` asincrónica).  
  
 `_P_DETACH`  
 Continúa ejecutando el proceso de llamada; el nuevo proceso se ejecuta en segundo plano sin acceso a la consola ni al teclado. No se realizan llamadas a `_cwait` en el nuevo proceso (`_spawn` asincrónica).  
  
 El argumento `cmdname` especifica el archivo que se ejecuta como el nuevo proceso y se puede especificar una ruta de acceso completa (desde la raíz), una ruta de acceso parcial (desde el directorio de trabajo actual) o tan solo un nombre de archivo. Si `cmdname` no tiene una extensión de nombre de archivo o no termina con un punto (.), la función `_spawn` prueba primero la extensión de nombre de archivo .com y luego la extensión de nombre de archivo .exe, la extensión de nombre de archivo .bat y finalmente la extensión de archivo .cmd.  
  
 Si `cmdname` tiene una extensión de nombre de archivo, solo se usa esa extensión. Si `cmdname` termina con un punto, la llamada a `_spawn` busca `cmdname` sin extensión de nombre de archivo. Las funciones `_spawnlp`, `_spawnlpe`, `_spawnvp` y `_spawnvpe` buscan `cmdname` (usando los mismos procedimientos) en los directorios especificados por la variable de entorno `PATH`.  
  
 Si `cmdname` contiene un especificador de unidad o barras diagonales (es decir, si es una ruta de acceso relativa), la llamada a `_spawn` busca únicamente el archivo especificado; no se realiza ninguna búsqueda de ruta.  
  
 En el pasado, algunas de estas funciones establecían `errno` en cero si se realizaba correctamente; el comportamiento actual es dejar `errno` sin modificar si se realiza correctamente, tal y como especifica el estándar de C. Si necesita emular el comportamiento antiguo, establezca `errno` en cero inmediatamente antes de llamar a estas funciones.  
  
> [!NOTE]
>  Para asegurarse de la inicialización y finalización correctas de la superposición, no use las funciones `setjmp` ni `longjmp` para entrar o salir de una rutina de superposición.  
  
## <a name="arguments-for-the-spawned-process"></a>Argumentos para el proceso generado  
 Para pasar argumentos al nuevo proceso, asigne uno o varios punteros a cadenas de caracteres como argumentos en la llamada a `_spawn`. Estas cadenas de caracteres forman la lista de argumentos para el proceso generado. La longitud conjunta de las cadenas que forman la lista de argumentos para el nuevo proceso no debe superar los 1024 bytes. El carácter nulo final ("\0") de cada cadena no se incluye en el recuento, pero los caracteres de espacio (que se insertan automáticamente para separar los argumentos) sí se cuentan.  
  
> [!NOTE]
>  Los espacios insertados en cadenas pueden generar un comportamiento inesperado; por ejemplo, si se pasa a `_spawn` la cadena `"hi there"`, el nuevo proceso obtendrá dos argumentos, `"hi"` y `"there"`. Si se deseaba que el nuevo proceso abriera un archivo denominado “hi there”, el proceso produciría un error. Para evitarlo, escriba la cadena entre comillas: `"\"hi there\""`.  
  
> [!IMPORTANT]
>  No pase datos proporcionados por el usuario a `_spawn` sin comprobar expresamente su contenido. `_spawn` dará lugar a una llamada a [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425), por lo que debe tener presente que los nombres de ruta de acceso incompletos podrían dar lugar a vulnerabilidades de seguridad.  
  
 Puede pasar punteros de argumento como argumentos independientes (en `_spawnl`, `_spawnle`, `_spawnlp` y `_spawnlpe`) o como una matriz de punteros (en `_spawnv`, `_spawnve`, `_spawnvp` y `_spawnvpe`). Debe pasar al menos un argumento, `arg0` o `argv`[0], al proceso generado. Por convención, este argumento es el nombre del programa que se escribiría en la línea de comandos. Un valor diferente no genera un error.  
  
 Las llamadas a `_spawnl`, `_spawnle`, `_spawnlp` y `_spawnlpe` se suelen usar en aquellos casos en los que el número de argumentos se conoce de antemano. El argumento `arg0` suele ser un puntero a `cmdname`. Los argumentos `arg1` a `argn` son punteros a las cadenas de caracteres que forman la nueva lista de argumentos. Después de `argn`, debe haber un puntero `NULL` para marcar el final de la lista de argumentos.  
  
 Las llamadas a `_spawnv`, `_spawnve`, `_spawnvp` y `_spawnvpe` resultan útiles cuando existe un número variable de argumentos para el nuevo proceso. Los punteros a los argumentos se pasan como matriz, `argv`*.* El argumento `argv`[0] suele ser un puntero a una ruta de acceso en modo real o al nombre del programa en modo protegido; de `argv`[1] a `argv`[`n`] son punteros a las cadenas de caracteres que forman la nueva lista de argumentos. El argumento `argv`[`n` +1] debe ser un puntero `NULL` para marcar el final de la lista de argumentos.  
  
## <a name="environment-of-the-spawned-process"></a>Entorno del proceso generado  
 Los archivos que están abiertos cuando se realiza una llamada a `_spawn` permanecen abiertos en el nuevo proceso. En las llamadas a `_spawnl`, `_spawnlp`, `_spawnv` y `_spawnvp`, el nuevo proceso hereda el entorno del proceso de llamada. Puede usar las llamadas a `_spawnle`, `_spawnlpe`, `_spawnve` y `_spawnvpe` para modificar el entorno del nuevo proceso pasando una lista de configuración de entorno con el argumento `envp`. El argumento `envp` es una matriz de punteros de caracteres, en la que cada elemento (salvo el elemento final) señala a una cadena finalizada en NULL que define una variable de entorno. Esta cadena suele tener el formato `NAME`=`value`, donde `NAME` es el nombre de una variable de entorno y `value` es el valor de cadena en el que se establece la variable. (Observe que `value` no está entre comillas). El último elemento de la matriz de `envp` debe ser `NULL`. Cuando `envp` es `NULL`, el proceso generado hereda la configuración de entorno del proceso primario.  
  
 Las funciones `_spawn` pueden pasar toda la información sobre los archivos abiertos, incluido el modo de traducción, al nuevo proceso. Esta información se pasa en modo real a través de la entrada `C_FILE_INFO` del entorno. El código de inicio normalmente procesa esta entrada y luego la elimina del entorno. En cambio, si una función `_spawn` genera un proceso que no sea de C, esta entrada permanece en el entorno. Al imprimir el entorno se muestran caracteres gráficos en la cadena de definición de esta entrada porque la información del entorno se pasa en formato binario en modo real. No debe tener ningún otro efecto en las operaciones normales. En modo protegido, la información del entorno se pasa en forma de texto y, por tanto, no contiene ningún carácter gráfico.  
  
 Debe vaciar (mediante `fflush` o `_flushall`) o cerrar explícitamente todas las secuencias antes de realizar la llamada a la función `_spawn`.  
  
 Los nuevos procesos creados mediante llamadas a rutinas de `_spawn` no conservan la configuración de la señal. En su lugar, el proceso generado restablece la configuración de la señal con el valor predeterminado.  
  
## <a name="redirecting-output"></a>Redirigir el resultado  
 Si va a llamar a `_spawn` desde un archivo DLL o una aplicación de interfaz gráfica de usuario y quiere redirigir el resultado a una canalización, tiene dos opciones:  
  
-   Usar la API de Win32 para crear una canalización, llamar a [AllocConsole](http://msdn.microsoft.com/library/windows/desktop/ms681944), establecer los valores de identificador en la estructura de inicio y llamar a [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425).  
  
-   Llamar a [_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md), lo que creará una canalización e invocará a la aplicación con **cmd.exe /c** (o **command.exe /c**).  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
child process output  
from SPAWN!  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../c-runtime-library/process-and-environment-control.md)   
 [abort](../c-runtime-library/reference/abort.md)   
 [atexit](../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec (Funciones)](../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall](../c-runtime-library/reference/flushall.md)   
 [_getmbcp](../c-runtime-library/reference/getmbcp.md)   
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp](../c-runtime-library/reference/setmbcp.md)   
 [system, _wsystem](../c-runtime-library/reference/system-wsystem.md)