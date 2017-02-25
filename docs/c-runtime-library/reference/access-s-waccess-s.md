---
title: "_access_s, _waccess_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_access_s"
  - "_waccess_s"
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
  - "waccess_s"
  - "access_s"
  - "_waccess_s"
  - "_access_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_access_s (función)"
  - "_taccess_s (función)"
  - "_waccess_s (función)"
  - "access_s (función)"
  - "taccess_s (función)"
  - "waccess_s (función)"
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# _access_s, _waccess_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina los permisos de lectura y escritura del archivo.  Ésta es una versión de [\_access, \_waccess](../../c-runtime-library/reference/access-waccess.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _access_s(   
   const char *path,   
   int mode   
);  
errno_t _waccess_s(   
   const wchar_t *path,   
   int mode   
);  
```  
  
#### Parámetros  
 `path`  
 Archivo o ruta de acceso del directorio.  
  
 `mode`  
 Configuración de permisos.  
  
## Valor devuelto  
 Cada función devuelve 0 si el archivo tiene el modo especificado.  La función devuelve un código de error si no existe el archivo con nombre o no está disponible en el modo especificado.  En este caso, la función devuelve un código de error de conjunto como sigue y también establece `errno` al mismo valor.  
  
 `EACCES`  
 Acceso denegado.  La configuración de permisos del archivo no permite el acceso especificado.  
  
 `ENOENT`  
 Nombre de archivo o ruta no encontrada.  
  
 `EINVAL`  
 Parámetro no válido.  
  
 Para obtener más información, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Cuando se utiliza con archivos, la función de `_access_s` determina si el archivo especificado existe y se puede lograr según lo especificado por el valor de `mode`.  Cuando se utiliza con los directorios, `_access_s` únicamente determina si existe el directorio especificado.  En [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] y sistemas operativos posteriores, todos los directorios tienen acceso de lectura y escritura.  
  
|valor mode|Comprueba el archivo para|  
|----------------|-------------------------------|  
|00|Existencia únicamente.|  
|02|Permiso de escritura.|  
|04|Permiso de Lectura.|  
|06|Permiso de lectura y escritura.|  
  
 El permiso para leer o escribir el archivo no es suficiente para garantizar la capacidad de abrir un archivo.  Por ejemplo, si un archivo está bloqueado por otro proceso, no es accesible aunque `_access_s` devuelve 0.  
  
 `_waccess_s` es una versión con caracteres anchos de `_access_s`, donde es una cadena de caracteres el argumento de `path` a `_waccess_s` de.  De lo contrario, los objetos `_waccess_s` y `_access_s` se comportan de forma idéntica.  
  
 Estas funciones validan sus parámetros.  Si `path` es `NULL` o `mode` no especifica un modo válido, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_taccess_s`|`_access_s`|`_access_s`|`_waccess_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_access_s`|\<io.h\>|\<errno.h\>|  
|`_waccess_s`|\<wchar.h o\> io.h \<\>|\<errno.h\>|  
  
## Ejemplo  
 Este ejemplo utiliza `_access_s` para comprobar el archivo denominado crt\_access\_s.c para ver si existe y si la escritura está permitida.  
  
```  
// crt_access_s.c  
  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    errno_t err = 0;  
  
    // Check for existence.   
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )  
    {  
        printf_s( "File crt_access_s.c exists.\n" );  
  
        // Check for write permission.   
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )  
        {  
            printf_s( "File crt_access_s.c does have "  
                      "write permission.\n" );  
        }  
        else  
        {  
            printf_s( "File crt_access_s.c does not have "  
                      "write permission.\n" );  
        }  
    }  
    else  
    {  
        printf_s( "File crt_access_s.c does not exist.\n" );  
    }  
}  
```  
  
  **El archivo crt\_access\_s.c existe.**  
**El archivo crt\_access\_s.c no tiene permiso de escritura.**   
## Equivalente en .NET Framework  
 <xref:System.IO.FileAccess?displayProperty=fullName>  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_access, \_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_chmod, \_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_fstat, \_fstat32, \_fstat64, \_fstati64, \_fstat32i64, \_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_stat, \_wstat \(Funciones\)](../../c-runtime-library/reference/stat-functions.md)