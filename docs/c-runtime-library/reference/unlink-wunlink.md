---
title: "_unlink, _wunlink | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_unlink"
  - "_wunlink"
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
  - "_tunlink"
  - "_unlink"
  - "wunlink"
  - "_wunlink"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tunlink (función)"
  - "_unlink (función)"
  - "_wunlink (función)"
  - "archivos [C++], eliminar"
  - "archivos [C++], quitar"
  - "tunlink (función)"
  - "unlink (función)"
  - "wunlink (función)"
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _unlink, _wunlink
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Eliminar un archivo.  
  
## Sintaxis  
  
```  
int _unlink(  
   const char *filename   
);  
int _wunlink(  
   const wchar_t *filename   
);  
```  
  
#### Parámetros  
 `filename`  
 Nombre del archivo que se va a quitar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve 0 si correctamente.  Si no, la función devuelve – 1 y establece `errno` a `EACCES`, que significa que la ruta especifica un archivo de sólo lectura, o a `ENOENT`, lo que significa que el archivo o la ruta no se encuentra o la ruta de acceso especificada un directorio.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## Comentarios  
 La función de `_unlink` elimina el archivo especificado por `filename`.  `_wunlink` es una versión con caracteres anchos de `_unlink`; el argumento `filename` para `_wunlink` es una cadena de caracteres anchos.  Por lo demás, estas funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tunlink`|`_unlink`|`_unlink`|`_wunlink`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_unlink`|\<io.h y\> stdio.h \<\>|  
|`_wunlink`|\<io.h o\> wchar.h \<\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo de código  
 Este programa utiliza el \_unlink para eliminar CRT\_UNLINK.TXT.  
  
```  
// crt_unlink.c  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( _unlink( "crt_unlink.txt" ) == -1 )  
      perror( "Could not delete 'CRT_UNLINK.TXT'" );  
   else  
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );  
}  
```  
  
### Entrada: crt\_unlink.txt  
  
```  
This file will be deleted.  
```  
  
### Resultados del ejemplo  
  
```  
Deleted 'CRT_UNLINK.TXT'  
```  
  
## Equivalente en .NET Framework  
 [System::IO::File::Delete](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [remove, \_wremove](../../c-runtime-library/reference/remove-wremove.md)