---
title: "remove, _wremove | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wremove"
  - "remove"
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
  - "remove"
  - "_wremove"
  - "_tremove"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tremove (función)"
  - "_wremove (función)"
  - "archivos [C++], eliminar"
  - "archivos [C++], quitar"
  - "remove (función)"
  - "tremove (función)"
  - "wremove (función)"
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# remove, _wremove
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Eliminar un archivo.  
  
## Sintaxis  
  
```  
  
      int remove(  
   const char *path   
);  
int _wremove(  
   const wchar_t *path   
);  
```  
  
#### Parámetros  
 *ruta de acceso*  
 Ruta de acceso del archivo que se va a quitar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve 0 si se elimina correctamente.  De lo contrario, devuelve \-1 y establece `errno` cualquier a `EACCES` para indicar que la ruta especifica un archivo de sólo lectura o el archivo abierto, o a **ENOENT** para indicar que el nombre de archivo o ruta no se encontró o que la ruta especifica un directorio.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## Comentarios  
 La función de **quitar** elimina el archivo especificado por la *ruta.* `_wremove` es una versión con caracteres anchos de **\_remove**; el argumento *de la ruta* de acceso a `_wremove` es una cadena de caracteres.  `_wremove` y **\_remove** se comportan exactamente igual de otra manera.  Todos los identificadores en un archivo deben cerrarse antes de poder eliminar.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tremove`|**remove**|**remove**|`_wremove`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**remove**|\<stdio.h o\> io.h \<\>|  
|`_wremove`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_remove.c  
/* This program uses remove to delete crt_remove.txt */  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( remove( "crt_remove.txt" ) == -1 )  
      perror( "Could not delete 'CRT_REMOVE.TXT'" );  
   else  
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );  
}  
```  
  
## Entrada: crt\_remove.txt  
  
```  
This file will be deleted.  
```  
  
## Resultados del ejemplo  
  
```  
Deleted 'CRT_REMOVE.TXT'  
```  
  
## Equivalente en .NET Framework  
 [System::IO::File::Delete](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_unlink, \_wunlink](../../c-runtime-library/reference/unlink-wunlink.md)