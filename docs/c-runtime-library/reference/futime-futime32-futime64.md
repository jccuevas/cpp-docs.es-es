---
title: _futime, _futime32, _futime64
ms.date: 11/04/2016
api_name:
- _futime64
- _futime32
- _futime
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
- api-ms-win-crt-time-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- futime
- _futime
- futime64
- _futime64
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
ms.openlocfilehash: 3de638f08882e2aae4743311730afcd888c43a60
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956233"
---
# <a name="_futime-_futime32-_futime64"></a>_futime, _futime32, _futime64

Define la hora de modificación de un archivo abierto.

## <a name="syntax"></a>Sintaxis

```C
int _futime(
   int fd,
   struct _utimbuf *filetime
);
int _futime32(
   int fd,
   struct __utimbuf32 *filetime
);
int _futime64(
   int fd,
   struct __utimbuf64 *filetime
);
```

### <a name="parameters"></a>Parámetros

*fd*<br/>
Descriptor de archivo para el archivo abierto.

*filetime*<br/>
Puntero a una estructura que contiene la nueva fecha de modificación.

## <a name="return-value"></a>Valor devuelto

Si la operación se realiza correctamente, devuelve 0. Si se produce un error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve-1 y **errno** se establece en **EBADF**, lo que indica un descriptor de archivo no válido o **EINVAL**, que indica un parámetro no válido.

## <a name="remarks"></a>Comentarios

La rutina **_futime** establece la fecha de modificación y la hora de acceso en el archivo abierto asociado a *FD*. **_futime** es idéntico a [_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md), salvo que su argumento es el descriptor de archivo de un archivo abierto, en lugar del nombre de un archivo o una ruta de acceso a un archivo. La estructura **_utimbuf** contiene campos para la nueva fecha de modificación y hora de acceso. Ambos campos deben contener valores válidos. **_utimbuf32** y **_utimbuf64** son idénticos a **_utimbuf** , salvo por el uso de los tipos de tiempo de 32 y 64 bits, respectivamente. **_futime** y **_utimbuf** usan un tipo de tiempo de 64 bits y **_futime** es idéntico en comportamiento a **_futime64**. Si necesita forzar el comportamiento anterior, defina **_USE_32BIT_TIME_T**. Esto hace que **_futime** sea idéntico en comportamiento a **_futime32** y hace que la estructura **_utimbuf** use el tipo de tiempo de 32, por lo que es equivalente a **__utimbuf32**.

**_futime64**, que usa la estructura **__utimbuf64** , puede leer y modificar fechas de archivo hasta 23:59:59, 31 de diciembre de 3000, UTC; mientras que una llamada a **_futime32** produce un error si la fecha del archivo es posterior al 23:59:59 de enero de 2038, UTC. La medianoche del 1 de enero de 1970 es el límite inferior del intervalo de fechas para estas funciones.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezado opcional|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_futime.c
// This program uses _futime to set the
// file-modification time to the current time.

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <io.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/utime.h>
#include <share.h>

int main( void )
{
   int hFile;

   // Show file time before and after.
   system( "dir crt_futime.c_input" );

   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );

   if( _futime( hFile, NULL ) == -1 )
      perror( "_futime failed\n" );
   else
      printf( "File time modified\n" );

   _close (hFile);

   system( "dir crt_futime.c_input" );
}
```

### <a name="input-crt_futimec_input"></a>Entrada: crt_futime.c_input

```Input
Arbitrary file contents.
```

### <a name="sample-output"></a>Resultados del ejemplo

```Output
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:40 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:41 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
File time modified
```

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
