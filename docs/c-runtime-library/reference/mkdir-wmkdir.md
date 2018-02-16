---
title: _mkdir, _wmkdir | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wmkdir
- _mkdir
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
- _mkdir
- tmkdir
- _tmkdir
- wmkdir
- _wmkdir
dev_langs:
- C++
helpviewer_keywords:
- _wmkdir function
- folders [C++], creating
- wmkdir function
- directories [C++], creating
- mkdir function
- tmkdir function
- _mkdir function
- _tmkdir function
ms.assetid: 7f22d01d-63a5-4712-a6e7-d34878b2d840
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7ca09b2ae9e9428647cbc0dc8778be0c58616fc
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="mkdir-wmkdir"></a>_mkdir, _wmkdir
Crea un directorio nuevo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
int _mkdir(
   const char *dirname   
);  
int _wmkdir(  
   const wchar_t *dirname   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dirname`  
 Ruta de acceso de un directorio nuevo.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve el valor 0 si se ha creado el directorio nuevo. En un error, la función devuelve -1 y establece `errno` como se indica a continuación.  
  
 `EEXIST`  
 No se creó el directorio porque `dirname` es el nombre de un archivo, directorio o dispositivo existente.  
  
 `ENOENT`  
 No se encontró la ruta de acceso.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_mkdir` crea un nuevo directorio con el *dirname* especificado. `_mkdir` puede crear únicamente un directorio nuevo por llamada, por lo que solo el último componente de `dirname` puede asignar un nombre a un directorio nuevo. `_mkdir` no traduce los delimitadores de ruta de acceso. En Windows NT, la barra diagonal inversa (\\) y la barra diagonal (/) son delimitadores de ruta de acceso válidos para las cadenas de caracteres de las rutinas en tiempo de ejecución.  
  
 `_wmkdir` es una versión con caracteres anchos de `_mkdir`; el argumento `dirname` para `_wmkdir` es una cadena de caracteres anchos. Por lo demás, `_wmkdir` y `_mkdir` se comportan de forma idéntica.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmkdir`|`_mkdir`|`_mkdir`|`_wmkdir`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_mkdir`|\<direct.h>|  
|`_wmkdir`|\<direct.h> o \<wchar.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
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
  
## <a name="see-also"></a>Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [_chdir, _wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_rmdir, _wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)