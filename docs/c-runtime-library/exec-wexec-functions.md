---
title: Funciones _exec y _wexec | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _texecve
- texecl
- _texeclpe
- texecve
- texecv
- texeclp
- texecle
- exec
- texeclpe
- _texecvp
- _texecl
- _texecle
- wexec
- _exec
- _texeclp
- _texecvpe
- texecvpe
- _texecv
- _wexec
dev_langs:
- C++
helpviewer_keywords:
- _texecle function
- _texecv function
- texeclpe function
- texecle function
- _texecl function
- texecv function
- _texeclp function
- _texecve function
- texecl function
- texecve function
- exec function
- texeclp function
- texecvp function
- texecvpe function
- processes, executing new
- _texecvp function
- _texeclpe function
- _wexec functions
- wexec functions
- _exec function
- _texecvpe function
ms.assetid: a261df93-206a-4fdc-b8ac-66aa7db83bc6
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: e0c4b4aaf9088fa9fcf6b59c348a54f618e4be62
ms.lasthandoff: 03/29/2017

---
# <a name="exec-wexec-functions"></a>_exec, _wexec (Funciones)
Cada función de esta familia carga y ejecuta un proceso nuevo:  
  
|||  
|-|-|  
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|  
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|  
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|  
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|  
  
 La última letra del nombre de función determina la variación.  
  
|Sufijo de la función _exec|Descripción|  
|----------------------------|-----------------|  
|`e`|`envp`, una matriz de punteros a la configuración de entorno, se pasa al nuevo proceso.|  
|`l`|Los argumentos de la línea de comandos se pasan individualmente a la función `_exec`. Se suele usar cuando el número de parámetros para el nuevo proceso se conoce de antemano.|  
|`p`|La variable de entorno `PATH` se usa para buscar el archivo que se va a ejecutar.|  
|`v`|`argv`, una matriz de punteros a los argumentos de la línea de comandos, se pasa a `_exec`. Se suele usar cuando el número de parámetros del proceso nuevo es variable.|  
  
## <a name="remarks"></a>Comentarios  
 Cada función `_exec` carga y ejecuta un proceso nuevo. Todas las funciones `_exec` usan la misma función del sistema operativo ([CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425.aspx)). Las funciones `_exec` controlan automáticamente argumentos de cadena de caracteres multibyte como sea necesario, reconociendo las secuencias de caracteres multibyte en función de la página de códigos multibyte actualmente en uso. Las funciones `_wexec` son versiones con caracteres anchos de las funciones `_exec`. Las funciones `_wexec` se comportan de forma idéntica a las funciones correspondientes de la familia de `_exec`, salvo que no controlan cadenas de caracteres multibyte.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_texecl`|`_execl`|`_execl`|`_wexecl`|  
|`_texecle`|`_execle`|`_execle`|`_wexecle`|  
|`_texeclp`|`_execlp`|`_execlp`|`_wexeclp`|  
|`_texeclpe`|`_execlpe`|`_execlpe`|`_wexeclpe`|  
|`_texecv`|`_execv`|`_execv`|`_wexecv`|  
|`_texecve`|`_execve`|`_execve`|`_wexecve`|  
|`_texecvp`|`_execvp`|`_execvp`|`_wexecvp`|  
|`_texecvpe`|`_execvpe`|`_execvpe`|`_wexecvpe`|  
  
 El parámetro de `cmdname` especifica el archivo que se va a ejecutar como nuevo proceso. Puede especificar una ruta de acceso completa (desde la raíz), una ruta de acceso parcial (desde el directorio de trabajo actual) o un nombre de archivo. Si `cmdname` no tiene una extensión de nombre de archivo o no termina con un punto (.), la función `_exec` busca el archivo con nombre. Si la búsqueda no obtiene resultado, intenta el mismo nombre base con la extensión de nombre de archivo .com y, después, con las extensiones de nombre de archivo .exe, .bat y .cmd. Si `cmdname` tiene una extensión de nombre de archivo, solo se usa esa extensión en la búsqueda. Si `cmdname` termina con un punto, la función `_exec` busca `cmdname` sin extensión de nombre de archivo. `_execlp`, `_execlpe`, `_execvp` y `_execvpe` buscan `cmdname` (usando los mismos procedimientos) en los directorios especificados por la variable de entorno `PATH`. Si `cmdname` contiene un especificador de unidad o barras diagonales (es decir, si es una ruta de acceso relativa), la llamada a `_exec` busca únicamente el archivo especificado y la ruta no se busca.  
  
 Los parámetros se pasan al proceso nuevo con uno o varios punteros a cadenas de caracteres como parámetros en la llamada a `_exec`. Estas cadenas de caracteres forman la lista de parámetros para el nuevo proceso. La longitud total de la configuración de entorno heredada y las cadenas que forman la lista de parámetros del nuevo proceso no debe ser mayor de 32 kilobytes. El carácter de terminación nulo (“\0”) de cada cadena no se incluye en el recuento, pero los caracteres de espacio (que se insertan automáticamente para separar los parámetros) sí se cuentan.  
  
> [!NOTE]
>  Los espacios insertados en cadenas pueden generar un comportamiento inesperado; por ejemplo, si se pasa a `_exec` la cadena `"hi there"`, el nuevo proceso obtendrá dos argumentos, `"hi"` y `"there"`. Si se deseaba que el nuevo proceso abriera un archivo denominado “hi there”, el proceso produciría un error. Para evitarlo, escriba la cadena entre comillas: `"\"hi there\""`.  
  
> [!IMPORTANT]
>  No pase datos proporcionados por el usuario a `_exec` sin comprobar expresamente su contenido. `_exec` dará lugar a una llamada a [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425.aspx), por lo que debe tener presente que los nombres de ruta de acceso incompletos podrían dar lugar a vulnerabilidades de seguridad.  
  
 Las funciones `_exec` validan sus parámetros. Si los parámetros esperados son punteros nulos, cadenas vacías o se omiten, las funciones `_exec` invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven -1. No se ejecuta ningún proceso nuevo.  
  
 Los punteros de argumento se pueden pasar como parámetros separados (`_execl`, `_execle`, `_execlp` y `_execlpe`) o como matriz de punteros (en `_execv`, `_execve`, `_execvp` y `_execvpe`). Se debe pasar al menos un parámetro, `arg0`, al nuevo proceso. Este parámetro es `argv`[0] del nuevo proceso. Normalmente, este parámetro es una copia de `cmdname`. (Un valor diferente no genera un error).  
  
 Las llamadas a `_execl`, `_execle`, `_execlp` y `_execlpe` se suelen usar cuando el número de parámetros se conoce de antemano. El parámetro `arg0` suele ser un puntero a `cmdname`. Los parámetros de `arg1` a `argn` señalan a las cadenas de caracteres que forman la nueva lista de parámetros. Un puntero nulo debe ir detrás de `argn` para marcar el final de la lista de parámetros.  
  
 Las llamadas a `_execv`, `_execve`, `_execvp` y `_execvpe` son útiles cuando el número de parámetros para el nuevo proceso es variable. Los punteros a los parámetros se pasan como matriz, `argv`. El parámetro `argv`[0] suele ser un puntero a `cmdname`. Los parámetros de `argv`[1] a `argv`[`n`] señalan a las cadenas de caracteres que forman la nueva lista de parámetros. El parámetro `argv`[`n`+1] debe ser un puntero `NULL` para marcar el final de la lista de parámetros.  
  
 Los archivos que están abiertos cuando se realiza una llamada a `_exec` permanecen abiertos en el nuevo proceso. En llamadas a `_execl`, `_execlp`, `_execv` y `_execvp`, el nuevo proceso hereda el entorno del proceso de llamada. Las llamadas a `_execle`, `_execlpe`, `_execve` y `_execvpe` modifican el entorno del nuevo proceso pasando una lista de configuración de entorno con el parámetro `envp`. `envp` es una matriz de punteros de caracteres, en la que cada elemento (salvo el elemento final) señala a una cadena terminada en NULL que define una variable de entorno. Esta cadena suele tener el formato `NAME`=`value`, donde `NAME` es el nombre de una variable de entorno y `value` es el valor de cadena en el que se establece la variable. (Observe que `value` no está entre comillas). El último elemento de la matriz de `envp` debe ser `NULL`. Cuando `envp` es `NULL`, el nuevo proceso hereda la configuración de entorno del proceso de llamada.  
  
 Un programa que se ejecuta con una de las funciones `_exec` se carga siempre en la memoria como si el campo de asignación máxima del encabezado del archivo .exe del programa estuviera establecido en el valor predeterminado 0xFFFFH.  
  
 Las llamadas a `_exec` no conservan los modos de traducción de los archivos abiertos. Si el nuevo proceso debe usar archivos heredados del proceso de llamada, use la rutina [_setmode](../c-runtime-library/reference/setmode.md) para establecer el modo de traducción de estos archivos en el modo deseado. Debe vaciar explícitamente (mediante `fflush` o `_flushall`) o cerrar todos los flujos antes de la llamada de la función `_exec`. Las configuraciones de las señales no se conservan en los nuevos procesos creados mediante llamadas a rutinas de `_exec`. Las configuraciones de las señales se restablecen a los valores predeterminados en el proceso nuevo.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_args.c  
// Illustrates the following variables used for accessing  
// command-line arguments and environment variables:  
// argc  argv  envp  
// This program will be executed by crt_exec which follows.  
  
#include <stdio.h>  
  
int main( int argc,  // Number of strings in array argv  
 char *argv[],       // Array of command-line argument strings  
 char **envp )       // Array of environment variable strings  
{  
    int count;  
  
    // Display each command-line argument.  
    printf( "\nCommand-line arguments:\n" );  
    for( count = 0; count < argc; count++ )  
        printf( "  argv[%d]   %s\n", count, argv[count] );  
  
    // Display each environment variable.   
    printf( "\nEnvironment variables:\n" );  
    while( *envp != NULL )  
        printf( "  %s\n", *(envp++) );  
  
    return;  
}  
```  
  
 Ejecute el programa siguiente para ejecutar Crt_args.exe:  
  
```  
// crt_exec.c  
// Illustrates the different versions of exec, including  
//      _execl          _execle          _execlp          _execlpe  
//      _execv          _execve          _execvp          _execvpe  
//  
// Although CRT_EXEC.C can exec any program, you can verify how   
// different versions handle arguments and environment by   
// compiling and specifying the sample program CRT_ARGS.C. See   
// "_spawn, _wspawn Functions" for examples of the similar spawn   
// functions.  
  
#include <stdio.h>  
#include <conio.h>  
#include <process.h>  
  
char *my_env[] =     // Environment for exec?e  
{  
   "THIS=environment will be",  
   "PASSED=to new process by",  
   "the EXEC=functions",  
   NULL  
};  
  
int main( int ac, char* av[] )  
{  
   char *args[4];  
   int ch;  
   if( ac != 3 ){  
      fprintf( stderr, "Usage: %s <program> <number (1-8)>\n", av[0] );  
      return;  
   }  
  
   // Arguments for _execv?   
   args[0] = av[1];  
   args[1] = "exec??";  
   args[2] = "two";  
   args[3] = NULL;  
  
   switch( atoi( av[2] ) )  
   {  
   case 1:  
      _execl( av[1], av[1], "_execl", "two", NULL );  
      break;  
   case 2:  
      _execle( av[1], av[1], "_execle", "two", NULL, my_env );  
      break;  
   case 3:  
      _execlp( av[1], av[1], "_execlp", "two", NULL );  
      break;  
   case 4:  
      _execlpe( av[1], av[1], "_execlpe", "two", NULL, my_env );  
      break;  
   case 5:  
      _execv( av[1], args );  
      break;  
   case 6:  
      _execve( av[1], args, my_env );  
      break;  
   case 7:  
      _execvp( av[1], args );  
      break;  
   case 8:  
      _execvpe( av[1], args, my_env );  
      break;  
   default:  
      break;  
   }  
  
   // This point is reached only if exec fails.   
   printf( "\nProcess was not execed." );  
   exit( 0 );  
}  
```  
  
## <a name="requirements"></a>Requisitos  
  
 **Encabezado:** process.h  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../c-runtime-library/process-and-environment-control.md)   
 [abort](../c-runtime-library/reference/abort.md)   
 [atexit](../c-runtime-library/reference/atexit.md)   
 [exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn (Funciones)](../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
