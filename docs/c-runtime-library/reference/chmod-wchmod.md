---
title: "_chmod, _wchmod | Microsoft Docs"
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
  - "_chmod"
  - "_wchmod"
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
  - "_chmod"
  - "_wchmod"
  - "wchmod"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_chmod (función)"
  - "_wchmod (función)"
  - "chmod (función)"
  - "permisos de archivo [C++]"
  - "archivos [C++], cambiar permisos"
  - "wchmod (función)"
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _chmod, _wchmod
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia los valores de los permisos de archivo.  
  
## Sintaxis  
  
```  
  
      int _chmod(   
   const char *filename,  
   int pmode   
);  
int _wchmod(   
   const wchar_t *filename,  
   int pmode   
);  
```  
  
#### Parámetros  
 `filename`  
 Nombre del archivo existente.  
  
 `pmode`  
 Configuración de permisos para el archivo.  
  
## Valor devuelto  
 Estas funciones devuelven 0 si la configuración de permisos se cambia correctamente.  Un valor devuelto de –1 indica error.  Si el archivo especificado no se encuentra, `errno` se establece en `ENOENT`; si un parámetro no es válido, `errno` se establece en `EINVAL`.  
  
## Comentarios  
 Los cambios de función de `_chmod` la configuración de permisos del archivo especificado por *`filename`.* La configuración de permisos controla el acceso de lectura y escritura al archivo.  La expresión de entero `pmode` contiene una o ambas de las constantes de manifiesto siguientes, definidos en SYS\\Stat.h.  
  
 `_S_IWRITE`  
 Escribir permitida.  
  
 `_S_IREAD`  
 Lectura permitida.  
  
 `_S_IREAD | _S_IWRITE`  
 Lectura y escritura permitidas.  
  
 Cuando se dan ambas constantes, se combinan con el operador bit a bit de `OR` \(          `|` \).  Si el permiso de escritura no se especifica, el archivo es de sólo lectura.  Observe que todos los archivos siempre son legibles; no es posible asignar el permiso de solo escritura.  Así, los modos `_S_IWRITE` y `_S_IREAD | _S_IWRITE` son equivalentes.  
  
 `_wchmod` es una versión con caracteres anchos de `_chmod`; el argumento `filename` para `_wchmod` es una cadena de caracteres anchos.  Por lo demás, `_wchmod` y `_chmod` se comportan de forma idéntica.  
  
 Esta función valida sus parámetros.  Si `pmode` no es una combinación de una de las constantes de manifiesto ni escribir un conjunto alternas de constantes, la función omite simplemente los.  Si `filename` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve \-1.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tchmod`|`_chmod`|`_chmod`|`_wchmod`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_chmod`|\<io.h\>|\<sistema\/types.h, sistema\>\<\/stat.h, errno.h\>\<\>|  
|`_wchmod`|\<io.h o\> wchar.h \<\>|\<sistema\/types.h, sistema\>\<\/stat.h, errno.h\>\<\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_chmod.c  
// This program uses _chmod to  
// change the mode of a file to read-only.  
// It then attempts to modify the file.  
//  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
// Change the mode and report error or success   
void set_mode_and_report(char * filename, int mask)  
{  
   // Check for failure   
   if( _chmod( filename, mask ) == -1 )  
   {  
      // Determine cause of failure and report.   
      switch (errno)  
      {  
         case EINVAL:  
            fprintf( stderr, "Invalid parameter to chmod.\n");  
            break;  
         case ENOENT:  
            fprintf( stderr, "File %s not found\n", filename );  
            break;  
         default:  
            // Should never be reached   
            fprintf( stderr, "Unexpected error in chmod.\n" );  
       }  
   }  
   else  
   {  
      if (mask == _S_IREAD)  
        printf( "Mode set to read-only\n" );  
      else if (mask & _S_IWRITE)  
        printf( "Mode set to read/write\n" );  
   }  
   fflush(stderr);  
}  
  
int main( void )  
{   
  
   // Create or append to a file.   
   system( "echo /* End of file */ >> crt_chmod.c_input" );  
  
   // Set file mode to read-only:   
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );  
  
   system( "echo /* End of file */ >> crt_chmod.c_input " );  
  
   // Change back to read/write:   
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );  
  
   system( "echo /* End of file */ >> crt_chmod.c_input " );   
}   
```  
  
  **`Una línea de texto.`  `Una línea de texto.` Modo establecido en readonly**  
**Se denegó el acceso.**  
**Modo establecido en la escritura**   
## Equivalente en .NET Framework  
  
-   [System::IO::File::SetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)  
  
-   [System::Security::Permissions::FileIOPermission](https://msdn.microsoft.com/en-us/library/system.security.permissions.fileiopermission.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_access, \_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_fstat, \_fstat32, \_fstat64, \_fstati64, \_fstat32i64, \_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_stat, \_wstat \(Funciones\)](../../c-runtime-library/reference/stat-functions.md)