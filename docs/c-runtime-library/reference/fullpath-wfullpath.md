---
title: "_fullpath, _wfullpath | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fullpath"
  - "_wfullpath"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wfullpath"
  - "fullpath"
  - "_wfullpath"
  - "_fullpath"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fullpath (función)"
  - "_wfullpath (función)"
  - "rutas de acceso absolutas"
  - "fullpath (función)"
  - "rutas de acceso de archivo relativas"
  - "wfullpath (función)"
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fullpath, _wfullpath
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un valor absoluto o un nombre de ruta de acceso completa para el nombre de ruta de acceso relativa especificado.  
  
## Sintaxis  
  
```  
char *_fullpath(   
   char *absPath,  
   const char *relPath,  
   size_t maxLength   
);  
wchar_t *_wfullpath(   
   wchar_t *absPath,  
   const wchar_t *relPath,  
   size_t maxLength   
);  
```  
  
#### Parámetros  
 `absPath`  
 Puntero a un búfer que contiene el valor absoluto o la ruta de acceso completa, o NULL.  
  
 `relPath`  
 Nombre de la ruta de acceso relativa.  
  
 `maxLength`  
 Longitud máxima del búfer del nombre de ruta de acceso absoluta \(`absPath`\).  Esta longitud está en bytes para `_fullpath` pero en caracteres anchos \(`wchar_t`\) para `_wfullpath`.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero a un búfer que contiene el nombre de ruta de acceso absoluta \(`absPath`\).  Si hay un error \(por ejemplo, si el último valor de `relPath` incluye una letra de unidad no válida o no puede encontrar, o si la longitud del nombre de ruta de acceso absoluta creado \(`absPath`\) es mayor que `maxLength`\), la función devuelve `NULL`.  
  
## Comentarios  
 La función de `_fullpath` expanda el nombre de ruta de acceso relativa en `relPath` al completo o ruta de acceso absoluta y almacena este nombre en *`absPath`.* Si `absPath` es NULL, `malloc` se utiliza para asignar un búfer de la longitud suficiente para contener el nombre de ruta.  Es responsabilidad del llamador liberar este búfer.  Un nombre de ruta de acceso relativa especifica una ruta a otra ubicación de la ubicación actual \(como el directorio de trabajo actual: “."\).  Un nombre de ruta de acceso absoluta es la extensión de un nombre de ruta de acceso relativa que indica la ruta completa necesaria para lograr la ubicación deseada de la raíz del sistema de archivos.  A diferencia de `_makepath`, `_fullpath` se puede utilizar para obtener el nombre de ruta de acceso absoluta para las rutas de acceso relativas \(`relPath`\) que incluyen “. \/” o “. \/” en su nombre.  
  
 Por ejemplo, para utilizar las rutinas de c, la aplicación debe incluir los archivos de encabezado que contienen las declaraciones de las rutinas.  Cada instrucción include del archivo de encabezado hace referencia a la ubicación del archivo de forma relativa \(del directorio de trabajo de la aplicación\):  
  
```  
#include <stdlib.h>  
```  
  
 cuando la ruta de acceso absoluta \(ubicación real del sistema de archivos\) del archivo puede ser:  
  
```  
\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h  
```  
  
 `_fullpath` controla automáticamente argumentos de cadena de multibyte\- carácter según corresponda, reconociendo secuencias de multibyte\- carácter según la página de códigos multibyte actualmente en uso.  `_wfullpath` es una versión con caracteres anchos de `_fullpath`; los argumentos de cadena para `_wfullpath` son cadenas de caracteres.  `_wfullpath` y `_fullpath` se comportan exactamente igual excepto que `_wfullpath` no controla las cadenas de multibyte\- carácter.  
  
 Si se definen `_DEBUG` y `_CRTDBG_MAP_ALLOC` ambos, las llamadas a `_fullpath` y `_wfullpath` son reemplazados por llamadas a `_fullpath_dbg` y a `_wfullpath_dbg` para permitir la depuración asignaciones de memoria.  Para obtener más información, vea [\_fullpath\_dbg, \_wfullpath\_dbg](../../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md).  
  
 Esta función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md), si `maxlen` es menor o igual que 0.  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `NULL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tfullpath`|`_fullpath`|`_fullpath`|`_wfullpath`|  
  
 Si el búfer de `absPath` es `NULL`, `_fullpath` llama [malloc](../../c-runtime-library/reference/malloc.md) para asignar un búfer y omite el argumento de `maxLength` .  Es responsabilidad del llamador desasignar este búfer \(mediante [libre](../../c-runtime-library/reference/free.md)\) según corresponda.  Si el argumento de `relPath` especifica una unidad de disco, el directorio actual de esta unidad se combina con la ruta.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fullpath`|\<stdlib.h\>|  
|`_wfullpath`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fullpath.c  
// This program demonstrates how _fullpath  
// creates a full path from a partial path.  
  
#include <stdio.h>  
#include <conio.h>  
#include <stdlib.h>  
#include <direct.h>  
  
void PrintFullPath( char * partialPath )  
{  
   char full[_MAX_PATH];  
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )  
      printf( "Full path is: %s\n", full );  
   else  
      printf( "Invalid path\n" );  
}  
  
int main( void )  
{  
   PrintFullPath( "test" );  
   PrintFullPath( "\\test" );  
   PrintFullPath( "..\\test" );  
}  
```  
  
  **La ruta de acceso completa es: C:\\Documents y Settings\\user\\My Documents\\test**  
**La ruta de acceso completa es: C:\\test**  
**La ruta de acceso completa es: C:\\Documents y Settings\\user\\test**   
## Equivalente en .NET Framework  
 [System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_getcwd, \_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdcwd, \_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [\_makepath, \_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [\_splitpath, \_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)