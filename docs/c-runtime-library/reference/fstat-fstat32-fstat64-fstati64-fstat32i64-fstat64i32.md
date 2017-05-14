---
title: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
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
- _fstat32i64
- fstat
- fstat64i32
- _fstat64
- _fstati64
- fstat64
- _fstat32
- fstat32i64
- fstati64
- _fstat
- fstat32
- _fstat64i32
dev_langs:
- C++
helpviewer_keywords:
- _fstat64 function
- fstati64 function
- _fstat64i32 function
- _fstat32i64 function
- _fstat32 function
- file information
- fstat64i32 function
- fstat32 function
- fstat function
- fstat64 function
- _fstat function
- _fstati64 function
- fstat32i64 function
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 4bf1e3ad35fb03891f9c861255919752d0403d70
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
Obtiene información sobre un archivo abierto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _fstat(   
   int fd,  
   struct _stat *buffer   
);  
int _fstat32(   
   int fd,  
   struct __stat32 *buffer   
);  
int _fstat64(   
   int fd,  
   struct __stat64 *buffer   
);  
int _fstati64(   
   int fd,  
   struct _stati64 *buffer   
);  
int _fstat32i64(   
   int fd,  
   struct _stat32i64 *buffer   
);  
int _fstat64i32(   
   int fd,  
   struct _stat64i32 *buffer   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fd`  
 Descriptor del archivo abierto.  
  
 `buffer`  
 Puntero a la estructura en que se van a almacenar los resultados.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve 0 si se obtiene la información de estado de archivo. Un valor devuelto de -1 indica un error. Si el descriptor de archivo no es válido o `buffer` es `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EBADF` en caso de un descriptor de archivo no válido o en `EINVAL` si `buffer` es `NULL`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_fstat` obtiene información sobre el archivo abierto asociado a `fd` y la almacena en la estructura a la que apunta `buffer`. La estructura `_stat`, que se define en SYS\Stat.h, contiene los siguientes campos.  
  
 `st_atime`  
 Hora del último acceso al archivo.  
  
 `st_ctime`  
 Hora de creación del archivo.  
  
 `st_dev`  
 Si se trata de un dispositivo, `fd`; de lo contrario, 0.  
  
 `st_mode`  
 Máscara de bits para información de modo de archivo. Se establece el bit `_S_IFCHR` si `fd` hace referencia a un dispositivo. Se establece el bit `_S_IFREG` si `fd` hace referencia a un archivo normal. Los bits de lectura y escritura se establecen según el modo de permiso del archivo. `_S_IFCHR` y otras constantes se definen en SYS\Stat.h.  
  
 `st_mtime`  
 Hora de la última modificación del archivo.  
  
 `st_nlink`  
 Siempre 1 en sistemas de archivos que no son NTFS.  
  
 `st_rdev`  
 Si se trata de un dispositivo, `fd`; de lo contrario, 0.  
  
 `st_size`  
 Tamaño del archivo en bytes.  
  
 Si `fd` hace referencia a un dispositivo, los campos `st_atime`, `st_ctime`, `st_mtime` y `st_size` no son significativos.  
  
 Dado que Stat.h usa el tipo [_dev_t](../../c-runtime-library/standard-types.md), que se define en Types.h, debe incluirse Types.h antes de Stat.h en el código.  
  
 `_fstat64`, que usa la estructura `__stat64`, permite expresar fechas de creación de archivo hasta las 23:59:59 del 31 de diciembre de 3000, hora UTC; mientras que las demás funciones solo representan fechas hasta las 23:59:59 del 18 de enero de 2038, hora UTC. La medianoche del 1 de enero de 1970 es el límite inferior del intervalo de fechas para todas estas funciones.  
  
 Las variaciones de estas funciones admiten tipos de tiempo de 32 o 64 bits y longitudes de archivos de 32 o 64 bits. El primer sufijo numérico (`32` o `64`) indica el tamaño del tipo de tiempo usado; el segundo sufijo es `i32` o `i64`, lo que indica si el tamaño del archivo se representa como un entero de 32 o 64 bits.  
  
 `_fstat` equivale a `_fstat64i32` y `struct _stat` contiene una hora de 64 bits. Esto es así a menos que se defina `_USE_32BIT_TIME_T` , en cuyo caso el comportamiento anterior está en vigor; `_fstat` usa un tiempo de 32 bits y `struct _stat` contiene un tiempo de 32 bits. Lo mismo ocurre para `_fstati64`.  
  
### <a name="time-type-and-file-length-type-variations-of-stat"></a>Tipo de tiempo y variaciones de tipo de longitud de archivo de _stat  
  
|Funciones|¿_USE_32BIT_TIME_T definida?|Tipo de tiempo|Tipo de longitud de archivo|  
|---------------|------------------------------------|---------------|----------------------|  
|`_fstat`|No definida|64 bits|32 bits|  
|`_fstat`|Definido|32 bits|32 bits|  
|`_fstat32`|No se ve afectada por la definición de macro|32 bits|32 bits|  
|`_fstat64`|No se ve afectada por la definición de macro|64 bits|64 bits|  
|`_fstati64`|No definida|64 bits|64 bits|  
|`_fstati64`|Definido|32 bits|64 bits|  
|`_fstat32i64`|No se ve afectada por la definición de macro|32 bits|64 bits|  
|`_fstat64i32`|No se ve afectada por la definición de macro|64 bits|32 bits|  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_fstat`|\<sys/stat.h> y \<sys/types.h>|  
|`_fstat32`|\<sys/stat.h> y \<sys/types.h>|  
|`_fstat64`|\<sys/stat.h> y \<sys/types.h>|  
|`_fstati64`|\<sys/stat.h> y \<sys/types.h>|  
|`_fstat32i64`|\<sys/stat.h> y \<sys/types.h>|  
|`_fstat64i32`|\<sys/stat.h> y \<sys/types.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_fstat.c  
// This program uses _fstat to report  
// the size of a file named F_STAT.OUT.  
  
#include <io.h>  
#include <fcntl.h>  
#include <time.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <errno.h>  
#include <share.h>  
  
int main( void )  
{  
   struct _stat buf;  
   int fd, result;  
   char buffer[] = "A line to output";  
   char timebuf[26];  
   errno_t err;  
  
   _sopen_s( &fd,  
             "f_stat.out",  
             _O_CREAT | _O_WRONLY | _O_TRUNC,  
             _SH_DENYNO,  
             _S_IREAD | _S_IWRITE );  
   if( fd != -1 )  
      _write( fd, buffer, strlen( buffer ) );  
  
   // Get data associated with "fd":   
   result = _fstat( fd, &buf );  
  
   // Check if statistics are valid:   
   if( result != 0 )  
   {  
      if (errno == EBADF)  
        printf( "Bad file descriptor.\n" );  
      else if (errno == EINVAL)  
        printf( "Invalid argument to _fstat.\n" );  
   }  
   else  
   {  
      printf( "File size     : %ld\n", buf.st_size );  
      err = ctime_s(timebuf, 26, &buf.st_mtime);  
      if (err)  
      {  
         printf("Invalid argument to ctime_s.");  
         exit(1);  
      }  
      printf( "Time modified : %s", timebuf );  
   }  
   _close( fd );  
}  
```  
  
```Output  
File size     : 16  
Time modified : Wed May 07 15:25:11 2003  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_access, _waccess](../../c-runtime-library/reference/access-waccess.md)   
 [_chmod, _wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_filelength, _filelengthi64](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [_stat, _wstat (Funciones)](../../c-runtime-library/reference/stat-functions.md)
