---
title: _chmod, _wchmod | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _chmod
- _wchmod
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
- _chmod
- _wchmod
- wchmod
dev_langs: C++
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5abc8e8952f19f3314608085af42ddfdfef87936
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="chmod-wchmod"></a>_chmod, _wchmod
Cambia la configuración de permisos de archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 Nombre del archivo existente.  
  
 `pmode`  
 Configuración de permisos del archivo.  
  
## <a name="return-value"></a>Valor devuelto  
 Estas funciones devuelven 0 si la configuración de permisos se ha modificado correctamente. Un valor devuelto de -1 indica un error. Si no se pudo encontrar el archivo especificado, `errno` se establece en `ENOENT`; si un parámetro no es válido, `errno` se establece en `EINVAL`.  
  
## <a name="remarks"></a>Comentarios  
 El `_chmod` función cambia la configuración de permisos del archivo especificado por `filename`. La configuración de permisos controla el acceso de lectura y escritura al archivo. La expresión de entero `pmode` contiene una o las dos constantes del manifiesto siguientes, que se definen en SYS\Stat.h.  
  
 `_S_IWRITE`  
 Escritura permitida.  
  
 `_S_IREAD`  
 Lectura permitida.  
  
 `_S_IREAD | _S_IWRITE`  
 Lectura y escritura permitidas.  
  
 Cuando ambas constantes se especifican, se unen con el operador `OR` bit a bit (`|`). Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. Tenga en cuenta que todos los archivos son siempre legibles; es decir, no es posible conceder permisos de solo escritura. Por consiguiente, los modos `_S_IWRITE` y `_S_IREAD | _S_IWRITE` son equivalentes.  
  
 `_wchmod` es una versión con caracteres anchos de `_chmod`; el argumento `filename` para `_wchmod` es una cadena de caracteres anchos. Por lo demás, `_wchmod` y `_chmod` se comportan de forma idéntica.  
  
 Esta función valida sus parámetros. Si `pmode` no es una combinación de una de las constantes del manifiesto o incorpora un conjunto alternativo de constantes, la función simplemente las omitirá. Si `filename` es `NULL`, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve -1.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tchmod`|`_chmod`|`_chmod`|`_wchmod`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_chmod`|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|  
|`_wchmod`|\<io.h> o \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
  
A line of text.  
  
```  
  
```Output  
  
      A line of text.Mode set to read-only  
Access is denied.  
Mode set to read/write  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_access, _waccess](../../c-runtime-library/reference/access-waccess.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_stat, _wstat (Funciones)](../../c-runtime-library/reference/stat-functions.md)