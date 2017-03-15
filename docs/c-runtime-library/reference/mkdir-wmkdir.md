---
title: "_mkdir, _wmkdir | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wmkdir"
  - "_mkdir"
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
  - "_mkdir"
  - "tmkdir"
  - "_tmkdir"
  - "wmkdir"
  - "_wmkdir"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mkdir (función)"
  - "_tmkdir (función)"
  - "_wmkdir (función)"
  - "directorios [C++], crear"
  - "carpetas [C++], crear"
  - "mkdir (función)"
  - "tmkdir (función)"
  - "wmkdir (función)"
ms.assetid: 7f22d01d-63a5-4712-a6e7-d34878b2d840
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _mkdir, _wmkdir
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un nuevo directorio.  
  
## Sintaxis  
  
```  
  
      int _mkdir(  
   const char *dirname   
);  
int _wmkdir(  
   const wchar_t *dirname   
);  
```  
  
#### Parámetros  
 `dirname`  
 Ruta de acceso para un nuevo directorio.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el valor 0 si el nuevo directorio se creó.  En un error, la función devuelve – 1 y establece `errno` como sigue.  
  
 `EEXIST`  
 El directorio no se creó porque `dirname` es el nombre de un archivo existente, un directorio, o de un dispositivo.  
  
 `ENOENT`  
 La ruta no se encontró.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `_mkdir` crea un nuevo directorio con el *dirname especificado .*`_mkdir` sólo puede crear un nuevo directorio por llamada, tan sólo el componente último de `dirname` puede llamar a un nuevo directorio.  `_mkdir` no traduce los delimitadores de la ruta.  En windows NT, la barra diagonal inversa \(\\\) y la barra diagonal \(\/\) son delimitadores de ruta válidos en cadenas de caracteres en rutinas de servicio.  
  
 `_wmkdir` es una versión con caracteres anchos de `_mkdir`; el argumento `dirname` para `_wmkdir` es una cadena de caracteres anchos.  Por lo demás, `_wmkdir` y `_mkdir` se comportan de forma idéntica.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tmkdir`|`_mkdir`|`_mkdir`|`_wmkdir`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mkdir`|\<direct.h\>|  
|`_wmkdir`|\<direct.h\> o \<wchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_makedir.c  
  
#include <direct.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   if( _mkdir( "\\testtmp" ) == 0 )  
   {  
      printf( "Directory '\\testtmp' was successfully created\n" );  
      system( "dir \\testtmp" );  
      if( _rmdir( "\\testtmp" ) == 0 )  
        printf( "Directory '\\testtmp' was successfully removed\n"  );  
      else  
         printf( "Problem removing directory '\\testtmp'\n" );  
   }  
   else  
      printf( "Problem creating directory '\\testtmp'\n" );  
}  
```  
  
## Resultados del ejemplo  
  
```  
Directory '\testtmp' was successfully created  
 Volume in drive C has no label.  
 Volume Serial Number is E078-087A  
  
 Directory of C:\testtmp  
  
02/12/2002  09:56a      <DIR>          .  
02/12/2002  09:56a      <DIR>          ..  
               0 File(s)              0 bytes  
               2 Dir(s)  15,498,690,560 bytes free  
Directory '\testtmp' was successfully removed  
```  
  
## Equivalente en .NET Framework  
  
-   [System::IO::Directory::CreateDirectory](https://msdn.microsoft.com/en-us/library/system.io.directory.createdirectory.aspx)  
  
-   [System::IO::DirectoryInfo::CreateSubdirectory](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.createsubdirectory.aspx)  
  
## Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [\_chdir, \_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_rmdir, \_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)