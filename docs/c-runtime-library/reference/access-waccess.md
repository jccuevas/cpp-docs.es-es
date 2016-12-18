---
title: "_access, _waccess | Microsoft Docs"
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
  - "_access"
  - "_waccess"
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
  - "_waccess"
  - "_access"
  - "taccess"
  - "waccess"
  - "_taccess"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_access (función)"
  - "_taccess (función)"
  - "_waccess (función)"
  - "función de acceso"
  - "taccess (función)"
  - "waccess (función)"
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
caps.latest.revision: 27
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _access, _waccess
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un archivo es de sólo lectura o no.  Versiones más seguras están disponibles; vea [\_access\_s, \_waccess\_s](../../c-runtime-library/reference/access-s-waccess-s.md).  
  
## Sintaxis  
  
```  
int _access(   
   const char *path,   
   int mode   
);  
int _waccess(   
   const wchar_t *path,   
   int mode   
);  
```  
  
#### Parámetros  
 `path`  
 Archivo o ruta de acceso del directorio.  
  
 `mode`  
 Atributo de lectura y escritura.  
  
## Valor devuelto  
 Cada función devuelve 0 si el archivo tiene el modo especificado.  La función devuelve – 1 si no existe el archivo con nombre o no tiene un modo determinado; en este caso, `errno` se establecen como se muestra en la tabla siguiente.  
  
 `EACCES`  
 Acceso denegado: la configuración de permisos del archivo no permite el acceso especificado.  
  
 `ENOENT`  
 Nombre de archivo o ruta no encontrada.  
  
 `EINVAL`  
 Parámetro no válido.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Cuando se utiliza con archivos, la función de `_access` determina si el archivo o el directorio especificado existe y tiene los atributos especificados por el valor de `mode`.  Cuando se utiliza con los directorios, `_access` únicamente determina si existe el directorio especificado; en [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] y sistemas operativos posteriores, todos los directorios tienen acceso de lectura y escritura.  
  
|Valor de `mode`|Comprueba el archivo para|  
|---------------------|-------------------------------|  
|00|Existencia sólo|  
|02|Solo escritura|  
|04|De sólo lectura|  
|06|Lectura y escritura|  
  
 Esta función sólo comprueba si el archivo y el directorio son de sólo lectura o no, no comprueba la configuración de seguridad del sistema de archivos.  Para que se necesita un token de acceso.  Para obtener más información sobre la seguridad del sistema de archivos, vea [Símbolos de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909).  Una clase ATL existe para proporcionar esta funcionalidad; vea [CAccessToken Class](../../atl/reference/caccesstoken-class.md).  
  
 `_waccess` es una versión con caracteres anchos de `_access`; el argumento `path` para `_waccess` es una cadena de caracteres anchos.  Por lo demás, `_waccess` y `_access` se comportan de forma idéntica.  
  
 Esta función valida sus parámetros.  Si `path` es `NULL` o `mode` no especifica un modo válido, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` a `EINVAL` y devuelve \-1.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_taccess`|`_access`|`_access`|`_waccess`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|------------|--------------------------|----------------------------|  
|`_access`|\<io.h\>|\<errno.h\>|  
|`_waccess`|\<wchar.h o\> io.h \<\>|\<errno.h\>|  
  
## Ejemplo  
 El ejemplo siguiente utiliza `_access` para comprobar el archivo denominado crt\_ACCESS.C para ver si existe y si la escritura está permitida.  
  
```  
// crt_access.c  
// compile with: /W1  
// This example uses _access to check the file named  
// crt_ACCESS.C to see if it exists and if writing is allowed.  
  
#include  <io.h>  
#include  <stdio.h>  
#include  <stdlib.h>  
  
int main( void )  
{  
    // Check for existence.  
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )  
    {  
        printf_s( "File crt_ACCESS.C exists.\n" );  
  
        // Check for write permission.  
        // Assume file is read-only.  
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )  
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );  
    }  
}  
```  
  
  **El archivo crt\_ACCESS.C existe.**  
**El archivo crt\_ACCESS.C no tiene permiso de escritura.**   
## Equivalente en .NET Framework  
 <xref:System.IO.FileAccess?displayProperty=fullName>  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_chmod, \_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_fstat, \_fstat32, \_fstat64, \_fstati64, \_fstat32i64, \_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_stat, \_wstat \(Funciones\)](../../c-runtime-library/reference/stat-functions.md)