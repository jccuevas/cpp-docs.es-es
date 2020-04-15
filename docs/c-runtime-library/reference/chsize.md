---
title: _chsize
ms.date: 4/2/2020
api_name:
- _chsize
- _o__chsize
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _chsize
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
ms.openlocfilehash: bb2d72e40796a1dd2253361626042486490c77d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350069"
---
# <a name="_chsize"></a>_chsize

Cambia el tamaño de un archivo. Hay disponible una versión más segura; consulte [_chsize_s](chsize-s.md).

## <a name="syntax"></a>Sintaxis

```C
int _chsize(
   int fd,
   long size
);
```

### <a name="parameters"></a>Parámetros

*Fd*<br/>
Descriptor de archivo que hace referencia a un archivo abierto.

*Tamaño*<br/>
Nueva longitud del archivo en bytes.

## <a name="return-value"></a>Valor devuelto

**_chsize** devuelve el valor 0 si el tamaño del archivo se ha cambiado correctamente. Un valor devuelto de -1 indica un error: **errno** se establece en **EACCES** si el archivo especificado es de solo lectura o el archivo especificado está bloqueado contra el acceso, a **EBADF** si el descriptor no es válido, **ENOSPC** si no queda espacio en el dispositivo, o **EINVAL** si el *tamaño* es menor que cero.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Observaciones

La función **_chsize** extiende o trunca el archivo asociado a *fd* a la longitud especificada por *size*. El archivo debe estar abierto en un modo que permita escritura. Si el archivo se amplía, se anexan caracteres nulos ("\0"). Si el archivo se trunca, se pierden todos los datos desde el final del archivo abreviado hasta la longitud original del archivo.

Esta función valida sus parámetros. Si *size* es menor que cero o *fd* es un descriptor de archivo incorrecto, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_chsize**|\<io.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_chsize.c
// This program uses _filelength to report the size
// of a file before and after modifying it with _chsize.

#include <io.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh, result;
   unsigned int nbytes = BUFSIZ;

   // Open a file
   if( _sopen_s( &fh, "data", _O_RDWR | _O_CREAT, _SH_DENYNO,
                 _S_IREAD | _S_IWRITE ) == 0 )
   {
      printf( "File length before: %ld\n", _filelength( fh ) );
      if( ( result = _chsize( fh, 329678 ) ) == 0 )
         printf( "Size successfully changed\n" );
      else
         printf( "Problem in changing the size\n" );
      printf( "File length after:  %ld\n", _filelength( fh ) );
      _close( fh );
   }
}
```

```Output
File length before: 0
Size successfully changed
File length after:  329678
```

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
