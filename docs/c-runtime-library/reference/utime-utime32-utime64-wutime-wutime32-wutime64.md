---
title: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
ms.date: 11/04/2016
apiname:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
ms.openlocfilehash: 8e52845a828e272ff3b8458b299c3757b8def748
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524643"
---
# <a name="utime-utime32-utime64-wutime-wutime32-wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64

Establece la hora de modificación de un archivo.

## <a name="syntax"></a>Sintaxis

```C
int _utime(
   const char *filename,
   struct _utimbuf *times
);
int _utime32(
   const char *filename,
   struct __utimbuf32 *times
);
int _utime64(
   const char *filename,
   struct __utimbuf64 *times
);
int _wutime(
   const wchar_t *filename,
   struct _utimbuf *times
);
int _wutime32(
   const wchar_t *filename,
   struct __utimbuf32 *times
);
int _wutime64(
   const wchar_t *filename,
   struct __utimbuf64 *times
);
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
Puntero a una cadena que contiene la ruta de acceso o el nombre de archivo.

*Veces*<br/>
Puntero a los valores de hora almacenados.

## <a name="return-value"></a>Valor devuelto

Si se ha cambiado la hora de modificación de archivo, cada una de estas funciones devuelve 0. Un valor devuelto de -1 indica un error. Si se pasa un parámetro no válido, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y **errno** se establece en uno de los siguientes valores:

|valor de errno|Condición|
|-|-|
| **EACCES** | La ruta de acceso especifica un directorio o un archivo de solo lectura |
| **EINVAL** | No válido *veces* argumento |
| **EMFILE** | Demasiados archivos abiertos (se debe abrir el archivo para cambiar su hora de modificación) |
| **ENOENT** | Ruta de acceso o nombre de archivo no encontrado |

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

La fecha de un archivo se puede cambiar si la fecha de modificación es posterior a la medianoche del 1 de enero de 1970 y anterior a la fecha de finalización de la función empleada. **_utime** y **_wutime** usar un valor de tiempo de 64 bits, por lo que la fecha de finalización es 23:59:59 del 31 de diciembre de 3000, UTC. Si **_USE_32BIT_TIME_T** se define para forzar el comportamiento anterior, la fecha de finalización es 23:59:59 del 18 de enero de 2038, UTC. **_utime32** o **_wutime32** usar un tipo en tiempo de 32 bits independientemente de si **_USE_32BIT_TIME_T** está definido, y siempre tienen la fecha de finalización anterior. **_utime64** o **_wutime64** usar siempre el tipo en tiempo de 64 bits, por lo que siempre, estas funciones admiten la fecha de finalización posterior.

## <a name="remarks"></a>Comentarios

El **_utime** función establece la hora de modificación para el archivo especificado por *filename*. El proceso debe tener acceso de escritura al archivo para cambiar la hora. En el sistema operativo Windows, puede cambiar la hora de acceso y la hora de modificación en el **_utimbuf** estructura. Si *veces* es un **NULL** puntero, la hora de modificación se establece en la hora local actual. En caso contrario, *veces* debe apuntar a una estructura de tipo **_utimbuf**, definida en SYS\UTIME. H.

El **_utimbuf** estructura almacena los tiempos de acceso y de modificación de archivos utilizados por **_utime** para cambiar las fechas de modificación del archivo. La estructura tiene los siguientes campos, que son de tipo **time_t**:

| Campo |   |
|-------|---|
| **actime** | Hora de acceso a archivos |
| **modtime** | Hora de modificación de archivos |

Las versiones específicas de la **_utimbuf** estructura (**_utimebuf32** y **__utimbuf64**) se definen mediante las versiones de 32 bits y 64 bits del tipo de hora. Se usan en las versiones específicas de 32 y 64 bits de esta función. **_utimbuf** forma predeterminada usa un tipo en tiempo de 64 bits, a menos que **_USE_32BIT_TIME_T** está definido.

**_utime** es idéntico al **_futime** , salvo que el *filename* argumento de **_utime** es un nombre de archivo o una ruta de acceso a un archivo, en lugar de un descriptor de archivo de un Abra el archivo.

**_wutime** es una versión con caracteres anchos de **_utime**; el *filename* argumento **_wutime** es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezados obligatorios|Encabezados opcionales|
|-------------|----------------------|----------------------|
|**_utime**, **_utime32**, **_utime64**|\<sys/utime.h>|\<errno.h>|
|**_utime64**|\<sys/utime.h>|\<errno.h>|
|**_wutime**|\<utime.h> o \<wchar.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este programa usa **_utime** para establecer la hora de modificación del archivo a la hora actual.

```C
// crt_utime.c
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/utime.h>
#include <time.h>

int main( void )
{
   struct tm tma = {0}, tmm = {0};
   struct _utimbuf ut;

   // Fill out the accessed time structure
   tma.tm_hour = 12;
   tma.tm_isdst = 0;
   tma.tm_mday = 15;
   tma.tm_min = 0;
   tma.tm_mon = 0;
   tma.tm_sec = 0;
   tma.tm_year = 103;

   // Fill out the modified time structure
   tmm.tm_hour = 12;
   tmm.tm_isdst = 0;
   tmm.tm_mday = 15;
   tmm.tm_min = 0;
   tmm.tm_mon = 0;
   tmm.tm_sec = 0;
   tmm.tm_year = 102;

   // Convert tm to time_t
   ut.actime = mktime(&tma);
   ut.modtime = mktime(&tmm);

   // Show file time before and after
   system( "dir crt_utime.c" );
   if( _utime( "crt_utime.c", &ut ) == -1 )
      perror( "_utime failed\n" );
   else
      printf( "File time modified\n" );
   system( "dir crt_utime.c" );
}
```

### <a name="sample-output"></a>Resultados del ejemplo

```Output
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/09/2003  05:38 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
File time modified
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/15/2002  12:00 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
```

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime, _futime32, _futime64](futime-futime32-futime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat, _wstat (Funciones)](stat-functions.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
