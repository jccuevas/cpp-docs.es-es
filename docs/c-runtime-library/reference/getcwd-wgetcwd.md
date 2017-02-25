---
title: "_getcwd, _wgetcwd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wgetcwd"
  - "_getcwd"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-environment-l1-1-0.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_getcwd"
  - "wgetcwd"
  - "_wgetcwd"
  - "tgetcwd"
  - "_tgetcwd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "getcwd (función)"
  - "directorio de trabajo"
  - "_wgetcwd (función)"
  - "_getcwd (función)"
  - "directorio de trabajo actual"
  - "wgetcwd (función)"
  - "trabajo actuales directorios [C++]"
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _getcwd, _wgetcwd
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene el directorio de trabajo actual.  
  
## Sintaxis  
  
```  
char *_getcwd(   
   char *buffer,  
   int maxlen   
);  
wchar_t *_wgetcwd(   
   wchar_t *buffer,  
   int maxlen   
);  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento de la ruta de acceso.  
  
 `maxlen`  
 Longitud máxima de la ruta de acceso en caracteres: `char` para `_getcwd` y `wchar_t` para `_wgetcwd`.  
  
## Valor devuelto  
 Devuelve un puntero a `buffer`. Un valor devuelto de `NULL` indica un error, y `errno` se establece en `ENOMEM`, que indica que no hay memoria suficiente para asignar los bytes de `maxlen` \(cuando un argumento de `NULL` se proporciona como `buffer`\), o en `ERANGE`, que indica que la ruta de acceso es más larga que los caracteres de `maxlen`. Si `maxlen` es inferior o igual a cero, esta función invoca un controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `_getcwd` obtiene la ruta de acceso completa del directorio de trabajo actual para la unidad predeterminada y la almacena en `buffer`. El argumento de entero `maxlen` especifica la longitud máxima de la ruta de acceso. Se produce un error si la longitud de la ruta de acceso \(incluido el carácter nulo final\) es mayor que `maxlen`*.* El argumento de `buffer` puede ser `NULL`; se asigna automáticamente un búfer con un tamaño mínimo de `maxlen` \(más solo en caso necesario\) mediante `malloc`, para almacenar la ruta de acceso. Este búfer se puede liberar más adelante llamando a `free` y pasando el valor devuelto de `_getcwd` \(un puntero al búfer asignado\).  
  
 `_getcwd` devuelve una cadena que representa la ruta de acceso del directorio de trabajo actual. Si el directorio de trabajo actual es la raíz, la cadena finaliza con una barra diagonal inversa \(`\`\). Si el directorio de trabajo actual es un directorio distinto de la raíz, la cadena finaliza con el nombre de directorio y no con una barra diagonal inversa.  
  
 `_wgetcwd` es una versión con caracteres anchos de `_getcwd`; el argumento de `buffer` y el valor devuelto de `_wgetcwd` son cadenas de caracteres anchos. Por lo demás, `_wgetcwd` y `_getcwd` se comportan de forma idéntica.  
  
 Cuando se definen `_DEBUG` y `_CRTDBG_MAP_ALLOC`, las llamadas a `_getcwd` y `_wgetcwd` se reemplazan por llamadas a `_getcwd_dbg` y `_wgetcwd_dbg` para admitir asignaciones de memoria de depuración. Para obtener más información, vea [\_getcwd\_dbg, \_wgetcwd\_dbg](../../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tgetcwd`|`_getcwd`|`_getcwd`|`_wgetcwd`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_getcwd`|\<direct.h\>|  
|`_wgetcwd`|\<direct.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_getcwd.c  
// This program places the name of the current directory in the   
// buffer array, then displays the name of the current directory   
// on the screen. Passing NULL as the buffer forces getcwd to allocate  
// memory for the path, which allows the code to support file paths  
// longer than _MAX_PATH, which are supported by NTFS.  
  
#include <direct.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* buffer;  
  
   // Get the current working directory:   
   if( (buffer = _getcwd( NULL, 0 )) == NULL )  
      perror( "_getcwd error" );  
   else  
   {  
      printf( "%s \nLength: %d\n", buffer, strnlen(buffer) );  
      free(buffer);  
   }  
}  
```  
  
```Output  
C:\Code  
```  
  
## Equivalente en .NET Framework  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [\_chdir, \_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_mkdir, \_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir, \_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)