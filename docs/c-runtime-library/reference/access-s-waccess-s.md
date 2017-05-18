---
title: _access_s, _waccess_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _access_s
- _waccess_s
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- waccess_s
- access_s
- _waccess_s
- _access_s
dev_langs:
- C++
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
caps.latest.revision: 28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 051c2e6a6b0315e2ca4ab3192f28a370d969ec5b
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="accesss-waccesss"></a>_access_s, _waccess_s
Determina los permisos de lectura y escritura del archivo. Se trata de una versión de [_access, _waccess](../../c-runtime-library/reference/access-waccess.md) con mejoras de seguridad, tal y como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `path`  
 Ruta de acceso del directorio o archivo.  
  
 `mode`  
 Configuración de permisos.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada función devuelve 0 si el archivo tiene el modo especificado. La función devuelve un código de error si el archivo especificado no existe o no está accesible en el modo especificado. En este caso, la función devuelve un código de error del conjunto de la manera siguiente y también establece `errno` en el mismo valor.  
  
 `EACCES`  
 Acceso denegado. La configuración de permisos del archivo no permite el acceso especificado.  
  
 `ENOENT`  
 No se encuentra el nombre o la ruta de acceso del archivo.  
  
 `EINVAL`  
 Parámetro no válido.  
  
 Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 Cuando se usa con archivos, la función `_access_s` determina si el archivo especificado existe y si se puede acceder a él tal y como lo especifica el valor de `mode`. Cuando se usa con directorios, la función `_access_s` solo determina si existe el directorio especificado. En [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] y en los sistemas operativos posteriores, todos los directorios tienen acceso de lectura y escritura.  
  
|valor del modo|Comprueba el archivo para|  
|----------------|---------------------|  
|00|Solo existencia.|  
|02|Permiso de escritura.|  
|04|Permiso de lectura.|  
|06|Permisos de lectura y escritura.|  
  
 Los permisos para leer o escribir en el archivo no bastan para garantizar la posibilidad de abrir un archivo. Por ejemplo, si un archivo está bloqueado por otro proceso, puede que no sea accesible aunque `_access_s` devuelva 0.  
  
 `_waccess_s` es una versión con caracteres anchos de `_access_s`; donde el argumento `path` para `_waccess_s` es una cadena de caracteres anchos. De lo contrario, los objetos `_waccess_s` y `_access_s` se comportan de forma idéntica.  
  
 Estas funciones validan sus parámetros. Si `path` es `NULL` o `mode` no especifica un modo válido, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_taccess_s`|`_access_s`|`_access_s`|`_waccess_s`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_access_s`|\<io.h>|\<errno.h>|  
|`_waccess_s`|\<wchar.h> o \<io.h>|\<errno.h>|  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se usa `_access_s` para comprobar el archivo denominado crt_access_s.c, para ver si existe y si se permite la escritura.  
  
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
  
```Output  
File crt_access_s.c exists.  
File crt_access_s.c does not have write permission.  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_access, _waccess](../../c-runtime-library/reference/access-waccess.md)   
 [_chmod, _wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_stat, _wstat (Funciones)](../../c-runtime-library/reference/stat-functions.md)
