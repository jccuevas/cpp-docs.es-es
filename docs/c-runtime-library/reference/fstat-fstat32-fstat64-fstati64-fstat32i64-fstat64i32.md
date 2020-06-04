---
title: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
ms.date: 4/2/2020
api_name:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
- _o__fstat32
- _o__fstat32i64
- _o__fstat64
- _o__fstat64i32
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 81c272187c681010e7b8560d43f2fad87e1e0fdc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910122"
---
# <a name="_fstat-_fstat32-_fstat64-_fstati64-_fstat32i64-_fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32

Obtiene información sobre un archivo abierto.

## <a name="syntax"></a>Sintaxis

```C
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

### <a name="parameters"></a>Parámetros

*FD*<br/>
Descriptor del archivo abierto.

*búfer*<br/>
Puntero a la estructura en que se van a almacenar los resultados.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si se obtiene la información de estado de archivo. Un valor devuelto de-1 indica un error. Si el descriptor de archivo no es válido o el *búfer* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EBADF**, en el caso de un descriptor de archivo no válido o en **EINVAL**, si *buffer* es **null**.

## <a name="remarks"></a>Observaciones

La función **_fstat** obtiene información sobre el archivo abierto asociado a *FD* y lo almacena en la estructura a la que apunta el *búfer*. La estructura de **_stat** , definida en SYS\Stat.h, contiene los siguientes campos.

|Campo|Significado|
|-|-|
| **st_atime** | Hora del último acceso al archivo. |
| **st_ctime** | Hora de creación del archivo. |
| **st_dev** | Si es un dispositivo, *FD*; de lo contrario, es 0. |
| **st_mode** | Máscara de bits para información de modo de archivo. El bit de **_S_IFCHR** se establece si *FD* hace referencia a un dispositivo. El bit de **_S_IFREG** se establece si *FD* hace referencia a un archivo normal. Los bits de lectura y escritura se establecen según el modo de permiso del archivo. **_S_IFCHR** y otras constantes se definen en SYS\Stat.h. |
| **st_mtime** | Hora de la última modificación del archivo. |
| **st_nlink** | Siempre 1 en sistemas de archivos que no son NTFS. |
| **st_rdev** | Si es un dispositivo, *FD*; de lo contrario, es 0. |
| **st_size** | Tamaño del archivo en bytes. |

Si *FD* hace referencia a un dispositivo, los campos **st_atime**, **st_ctime**, **st_mtime**y **st_size** no son significativos.

Dado que Stat.h usa el tipo [_dev_t](../../c-runtime-library/standard-types.md), que se define en Types.h, debe incluirse Types.h antes de Stat.h en el código.

**_fstat64**, que usa la estructura de **__stat64** , permite expresar fechas de creación de archivos hasta 23:59:59, 31 de diciembre de 3000, UTC; mientras que las demás funciones solo representan fechas hasta el 23:59:59 de enero de 2038, UTC. La medianoche del 1 de enero de 1970 es el límite inferior del intervalo de fechas para todas estas funciones.

Las variaciones de estas funciones admiten tipos de tiempo de 32 o 64 bits y longitudes de archivos de 32 o 64 bits. El primer sufijo numérico (**32** o **64**) indica el tamaño del tipo de tiempo utilizado. el segundo sufijo es **I32** o **i64**, que indica si el tamaño del archivo se representa como un entero de 32 bits o 64 bits.

**_fstat** es equivalente a **_fstat64i32**y **struct** **_stat** contiene una hora de 64 bits. Esto es así a menos que se defina **_USE_32BIT_TIME_T** , en cuyo caso el comportamiento anterior está en vigor; **_fstat** usa una hora de 32 bits y una **estructura** **_stat** contiene un tiempo de 32 bits. Lo mismo se aplica a **_fstati64**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Tipo de tiempo y variaciones de tipo de longitud de archivo de _stat

|Functions|¿_USE_32BIT_TIME_T definida?|Tipo de tiempo|Tipo de longitud de archivo|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|No definida|64 bits|32 bits|
|**_fstat**|Definido|32 bits|32 bits|
|**_fstat32**|No se ve afectada por la definición de macro|32 bits|32 bits|
|**_fstat64**|No se ve afectada por la definición de macro|64 bits|64 bits|
|**_fstati64**|No definida|64 bits|64 bits|
|**_fstati64**|Definido|32 bits|64 bits|
|**_fstat32i64**|No se ve afectada por la definición de macro|32 bits|64 bits|
|**_fstat64i32**|No se ve afectada por la definición de macro|64 bits|32 bits|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fstat**|\<sys/stat.h> y \<sys/types.h>|
|**_fstat32**|\<sys/stat.h> y \<sys/types.h>|
|**_fstat64**|\<sys/stat.h> y \<sys/types.h>|
|**_fstati64**|\<sys/stat.h> y \<sys/types.h>|
|**_fstat32i64**|\<sys/stat.h> y \<sys/types.h>|
|**_fstat64i32**|\<sys/stat.h> y \<sys/types.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
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

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[_stat, _wstat (Funciones)](stat-functions.md)<br/>
