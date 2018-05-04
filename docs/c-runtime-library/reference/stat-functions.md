---
title: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wstat64
- _stati64
- _stat32
- _stat32i64
- _stat
- _wstati64
- _wstat32
- _wstat64i32
- _wstat
- _stat64
- _stat64i32
- _wstat32i64
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
- tstat32
- tstat
- _tstat64i32
- tstati64
- _wstat64
- _wstat32
- wstati64
- tstat64
- _stati64
- _wstat
- wstat64i32
- stat32i64
- tstat32i64
- _tstat
- _wstati64
- _tstati64
- _wstat32i64
- wstat32
- _wstat64i32
- _stat
- _tstat32
- stat64i32
- wstat64
- stat
- _stat32i64
- _stat32
- stati64
- wstat
- _stat64i32
- stat32
- _tstat32i64
- tstat64i32
- _tstat64
- _stat64
- stat/_stat
- stat/_stat32
- stat/_stat64
- stat/_stati64
- stat/_stat32i64
- stat/_stat64i32
- stat/_wstat
- stat/_wstat32
- stat/_wstat64
- stat/_wstati64
- stat/_wstat32i64
- stat/_wstat64i32
dev_langs:
- C++
helpviewer_keywords:
- files [C++], status information
- _stat function
- _wstat function
- _stat64i32 function
- tstat function
- _tstat64i32 function
- _stati64 function
- _stat64 function
- tstati64 function
- wstati64 function
- wstat64 function
- _wstat64i32 function
- _tstat32i64 function
- _stat32i64 function
- stat function
- status of files
- _tstat32 function
- tstat64 function
- _wstat64 function
- _tstat function
- _stat32 function
- wstat function
- _wstat32i64 function
- _tstati64 function
- _wstat32 function
- stat64 function
- stati64 function
- _wstati64 function
- _tstat64 function
- files [C++], getting status information
ms.assetid: 99a75ae6-ff26-47ad-af70-5ea7e17226a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ce367bdee78be1610a36c887a04f2130375114
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="stat-stat32-stat64-stati64-stat32i64-stat64i32-wstat-wstat32-wstat64-wstati64-wstat32i64-wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

Obtenga información de estado sobre un archivo.

## <a name="syntax"></a>Sintaxis

```C
int _stat(
   const char *path,
   struct _stat *buffer
);
int _stat32(
   const char *path,
   struct __stat32 *buffer
);
int _stat64(
   const char *path,
   struct __stat64 *buffer
);
int _stati64(
   const char *path,
   struct _stati64 *buffer
);
int _stat32i64(
   const char *path,
   struct _stat32i64 *buffer
);
int _stat64i32(
   const char *path,
   struct _stat64i32 *buffer
);
int _wstat(
   const wchar_t *path,
   struct _stat *buffer
);
int _wstat32(
   const wchar_t *path,
   struct __stat32 *buffer
);
int _wstat64(
   const wchar_t *path,
   struct __stat64 *buffer
);
int _wstati64(
   const wchar_t *path,
   struct _stati64 *buffer
);
int _wstat32i64(
   const wchar_t *path,
   struct _stat32i64 *buffer
);
int _wstat64i32(
   const wchar_t *path,
   struct _stat64i32 *buffer
);
```

### <a name="parameters"></a>Parámetros

*path*<br/>
Puntero a una cadena que contiene la ruta de acceso del directorio o el archivo existente.

*buffer*<br/>
Puntero a la estructura que almacena los resultados.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve 0 si se obtiene la información de estado de archivo. Un valor devuelto de -1 indica un error, en cuyo caso **errno** está establecido en **ENOENT**, que indica que el nombre de archivo o ruta de acceso no se encontró. Un valor devuelto de **EINVAL** indica un parámetro no válido; **errno** también se establece en **EINVAL** en este caso.

Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.

Si es posterior a la medianoche del 1 de enero de 1970 y antes de 23:59:59, 31 de diciembre de 3000, UTC, a menos que use la marca de fecha en un archivo que se puede representar **_stat32** o **_wstat32**, o que haya definido **_ USE_32BIT_TIME_T**, en cuyo caso se puede representar la fecha hasta las 23:59:59 del 18 de enero de 2038, UTC.

## <a name="remarks"></a>Comentarios

El **_stat** función obtiene información sobre el archivo o directorio especificado por *ruta de acceso* y lo almacena en la estructura que señala *búfer*. **_stat** controla automáticamente argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso.

**_wstat** es una versión con caracteres anchos de **_stat**; el *ruta de acceso* argumento pasado a **_wstat** es una cadena de caracteres anchos. **_wstat** y **_stat** se comportan exactamente igual, salvo que **_wstat** no controla las cadenas de caracteres multibyte.

Variaciones de estas funciones admiten tipos de tiempo de 32 o 64 bits, y longitudes de archivos de 32 o 64 bits. El primer sufijo numérico (**32** o **64**) indica el tamaño de la hora de utiliza el tipo; el segundo sufijo es **i32** o **i64**, que indica si el tamaño del archivo se representa como un entero de 32 bits o 64 bits.

**_stat** es equivalente a **_stat64i32**, y **struct** **_stat** contiene una hora de 64 bits. Esto es así a menos que **_USE_32BIT_TIME_T** se define, en cuyo caso el comportamiento anterior está en vigor; **_stat** usa uno de 32 bits, y **struct** **_stat** contiene un tiempo de 32 bits. Lo mismo puede decirse de **_stati64**.

> [!NOTE]
> **_wstat** no funciona con vínculos simbólicos de Windows Vista. En estos casos, **_wstat** siempre notificará un tamaño de archivo de 0. **_stat** funcione correctamente con los vínculos simbólicos.

Esta función valida sus parámetros. Si el valor *ruta de acceso* o *búfer* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

### <a name="time-type-and-file-length-type-variations-of-stat"></a>Tipo de tiempo y variaciones de tipo de longitud de archivo de _stat

|Funciones|¿_USE_32BIT_TIME_T definida?|Tipo de tiempo|Tipo de longitud de archivo|
|---------------|------------------------------------|---------------|----------------------|
|**_stat**, **_wstat**|No definida|64 bits|32 bits|
|**_stat**, **_wstat**|Definido|32 bits|32 bits|
|**_stat32**, **_wstat32**|No se ve afectada por la definición de macro|32 bits|32 bits|
|**_stat64**, **_wstat64**|No se ve afectada por la definición de macro|64 bits|64 bits|
|**_stati64**, **_wstati64**|No definida|64 bits|64 bits|
|**_stati64**, **_wstati64**|Definido|32 bits|64 bits|
|**_stat32i64**, **_wstat32i64**|No se ve afectada por la definición de macro|32 bits|64 bits|
|**_stat64i32**, **_wstat64i32**|No se ve afectada por la definición de macro|64 bits|32 bits|

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat**|**_stat**|**_stat**|**_wstat**|
|**_tstat64**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

El **_stat** estructura, definida en SYS\STAT. H, incluye los siguientes campos.

|Campo||
|-|-|
**st_gid**|Identificador numérico del grupo que posee el archivo (específico de UNIX). Este campo siempre será cero en sistemas Windows. Un archivo redirigido se clasifica como archivo Windows.
**st_atime**|Hora del último acceso del archivo. Válido en NTFS, pero no en unidades de disco con formato FAT.
**st_ctime**|Hora de creación del archivo. Válido en NTFS, pero no en unidades de disco con formato FAT.
**st_dev**|Número de unidad del disco que contiene el archivo (igual que **st_rdev**).
**st_ino**|Número del nodo de información (la **inode**) para el archivo (específico de UNIX). En sistemas de archivos UNIX, la **inode** describe la fecha del archivo y marcas de tiempo, permisos y contenido. Cuando los archivos están vinculados entre sí, comparten el mismo **inode**. El **inode**y, por tanto, **st_ino**, no tiene ningún significado en los sistemas de archivos FAT, HPFS o NTFS.
**st_mode**|Máscara de bits para información de modo de archivo. El **_S_IFDIR** bit se establece si *ruta de acceso* especifica un directorio; el **_S_IFREG** bit se establece si *ruta de acceso* especifica un archivo normal o un dispositivo. Los bits de lectura y escritura de usuario se establecen según el modo de permiso del archivo; los bits de ejecución de usuario se establecen según la extensión del nombre de archivo.
**st_mtime**|Hora de la última modificación del archivo.
**st_nlink**|Siempre 1 en sistemas de archivos que no son NTFS.
**st_rdev**|Número de unidad del disco que contiene el archivo (igual que **st_dev**).
**st_size**|Tamaño del archivo en bytes; un entero de 64 bits para variaciones con la **i64** sufijo.
**st_uid**|Identificador numérico del usuario propietario del archivo (específico de UNIX). Este campo siempre será cero en los sistemas Windows. Un archivo redirigido se clasifica como archivo Windows.

Si *ruta de acceso* hace referencia a un dispositivo, el **st_size**, varios campos de tiempo, **st_dev**, y **st_rdev** campos en el **_stat**  estructura carecen de sentido. Dado que STAT. H usa el tipo [_dev_t](../../c-runtime-library/standard-types.md) que se define en TYPES.H, debe incluir TYPES.H antes de STAT.H en su código.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezados opcionales|
|-------------|---------------------|----------------------|
|**_stat**, **_stat32**, **_stat64**, **_stati64**, **_stat32i64**, **_stat64i32**|\<sys/types.h> seguido de \<sys/stat.h>|\<errno.h>|
|**_wstat**, **_wstat32**, **_wstat64**, **_wstati64**, **_wstat32i64**, **_wstat64i32**|\<sys/types.h> seguido de \<sys/stat.h> o \<wchar.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_stat.c
// This program uses the _stat function to
// report information about the file named crt_stat.c.

#include <time.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   struct _stat buf;
   int result;
   char timebuf[26];
   char* filename = "crt_stat.c";
   errno_t err;

   // Get data associated with "crt_stat.c":
   result = _stat( filename, &buf );

   // Check if statistics are valid:
   if( result != 0 )
   {
      perror( "Problem getting information" );
      switch (errno)
      {
         case ENOENT:
           printf("File %s not found.\n", filename);
           break;
         case EINVAL:
           printf("Invalid parameter to _stat.\n");
           break;
         default:
           /* Should never be reached. */
           printf("Unexpected error in _stat.\n");
      }
   }
   else
   {
      // Output some of the statistics:
      printf( "File size     : %ld\n", buf.st_size );
      printf( "Drive         : %c:\n", buf.st_dev + 'A' );
      err = ctime_s(timebuf, 26, &buf.st_mtime);
      if (err)
      {
         printf("Invalid arguments to ctime_s.");
         exit(1);
      }
      printf( "Time modified : %s", timebuf );
   }
}
```

```Output
File size     : 732
Drive         : C:
Time modified : Thu Feb 07 14:39:36 2002
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_setmbcp](setmbcp.md)<br/>
