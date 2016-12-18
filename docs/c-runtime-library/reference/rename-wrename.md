---
title: "rename, _wrename | Microsoft Docs"
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
  - "rename"
  - "_wrename"
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
  - "_wrename"
  - "_trename"
  - "Rename"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_trename (función)"
  - "_wrename (función)"
  - "directorios [C++], cambiar nombre"
  - "archivos [C++], cambiar nombre"
  - "nombres [C++], de directorio (cambiar)"
  - "nombres [C++], de archivo (cambiar)"
  - "rename (función)"
  - "cambiar el nombre de directorios"
  - "cambiar el nombre de archivos"
  - "trename (función)"
  - "wrename (función)"
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rename, _wrename
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Nombre de un archivo o directorio.  
  
## Sintaxis  
  
```  
  
      int rename(  
   const char *oldname,  
   const char *newname   
);  
int _wrename(  
   const wchar_t *oldname,  
   const wchar_t *newname   
);  
```  
  
#### Parámetros  
 *oldname*  
 Puntero al nombre anterior.  
  
 *newname*  
 Puntero al nuevo nombre.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve 0 si es correcto.  En un error, la función devuelve un valor distinto de cero y establece `errno` en uno de los siguientes valores:  
  
 `EACCES`  
 El archivo o el directorio especificado por *newname* existe o no puede estar ya creado \(ruta no válida\); o *el oldname* es un directorio y *newname* especifica una ruta de acceso diferente.  
  
 `ENOENT`  
 Archivo o ruta de acceso especificada por *el oldname* no encontrado.  
  
 `EINVAL`  
 El nombre contiene caracteres no válidos.  
  
 Para otros valores devueltos posibles, vea [\_doserrno, \_errno, syserrlist, y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de **rename** cambia el nombre del archivo o el directorio especificado por *el oldname* al nombre especificado en *newname*.  El nombre anterior debe ser la ruta de acceso de un archivo existente o un directorio.  El nuevo nombre no debe ser el nombre de un archivo existente o un directorio.  Puede utilizar **rename** para mover un archivo a partir de un directorio o el dispositivo a otro dando una ruta de acceso diferente en el argumento *de newname* .  Sin embargo, no puede utilizar **rename** para mover un directorio.  Los directorios se puede cambiar, pero no mover.  
  
 `_wrename` es una versión con caracteres anchos de **\_rename**; los argumentos de `_wrename` son cadenas de caracteres.  `_wrename` y **\_rename** se comportan exactamente igual de otra manera.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_trename`|**cambie**|**cambie**|`_wrename`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**cambie**|\<io.h o\> stdio.h \<\>|  
|`_wrename`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_renamer.c  
/* This program attempts to rename a file named  
 * CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation  
 * to succeed, a file named CRT_RENAMER.OBJ must exist and  
 * a file named CRT_RENAMER.JBO must not exist.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   int  result;  
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";  
  
   /* Attempt to rename file: */  
   result = rename( old, new );  
   if( result != 0 )  
      printf( "Could not rename '%s'\n", old );  
   else  
      printf( "File '%s' renamed to '%s'\n", old, new );  
}  
```  
  
## Resultados  
  
```  
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'  
```  
  
## Equivalente en .NET Framework  
 [System::IO::File::Move](https://msdn.microsoft.com/en-us/library/system.io.file.move.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)