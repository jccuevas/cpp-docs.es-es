---
title: _lseek, _lseeki64
ms.date: 11/04/2016
api_name:
- _lseeki64
- _lseek
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lseeki64
- _lseek
- lseeki64
helpviewer_keywords:
- lseek function
- _lseek function
- _lseeki64 function
- lseeki64 function
- file pointers [C++], moving
- seek file pointers
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
ms.openlocfilehash: 67bcce2a9936cd09973e8ddf1828704944866439
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952983"
---
# <a name="_lseek-_lseeki64"></a>_lseek, _lseeki64

Mueve un puntero de archivo a la ubicación especificada.

## <a name="syntax"></a>Sintaxis

```C
long _lseek(
   int fd,
   long offset,
   int origin
);
__int64 _lseeki64(
   int fd,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parámetros

*fd*<br/>
Descriptor de archivo que hace referencia a un archivo abierto.

*offset*<br/>
Número de bytes de *origin*.

*origin*<br/>
Posición inicial.

## <a name="return-value"></a>Valor devuelto

**_lseek** devuelve el desplazamiento, en bytes, de la nueva posición desde el principio del archivo. **_lseeki64** devuelve el desplazamiento en un entero de 64 bits. La función devuelve-1L para indicar un error. Si se pasa un parámetro no válido (como un descriptor de archivo incorrecto), el valor de *origin* no es válido o la posición especificada por *offset* se encuentra antes del inicio del archivo, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** en **EBADF** y devuelven-1L. En los dispositivos que no pueden realizar búsquedas (como los terminales y las impresoras), el valor devuelto es indefinido.

Para obtener más información sobre estos y otros códigos error, vea [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **_lseek** mueve el puntero de archivo asociado a *FD* a una nueva ubicación que tiene *desplazamientos* de bytes desde el *origen*. Se produce la siguiente operación en el archivo en la nueva ubicación. El argumento *origin* debe ser una de las siguientes constantes, que se definen en Stdio.h.

|valor de *origen*||
|-|-|
| **SEEK_SET** | Inicio del archivo. |
| **SEEK_CUR** | Posición actual del puntero de archivo. |
| **SEEK_END** | Final de archivo. |

Puede usar **_lseek** para cambiar la posición del puntero en cualquier parte de un archivo o más allá del final del archivo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_lseek**|\<io.h>|
|**_lseeki64**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_lseek.c
/* This program first opens a file named lseek.txt.
* It then uses _lseek to find the beginning of the file,
* to find the current position in the file, and to find
* the end of the file.
*/

#include <io.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh;
   long pos;               /* Position of file pointer */
   char buffer[10];

   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );

   /* Seek the beginning of the file: */
   pos = _lseek( fh, 0L, SEEK_SET );
   if( pos == -1L )
      perror( "_lseek to beginning failed" );
   else
      printf( "Position for beginning of file seek = %ld\n", pos );

   /* Move file pointer a little */
    _read( fh, buffer, 10 );

   /* Find current position: */
   pos = _lseek( fh, 0L, SEEK_CUR );
   if( pos == -1L )
      perror( "_lseek to current position failed" );
   else
      printf( "Position for current position seek = %ld\n", pos );

   /* Set the end of the file: */
   pos = _lseek( fh, 0L, SEEK_END );
   if( pos == -1L )
      perror( "_lseek to end failed" );
   else
      printf( "Position for end of file seek = %ld\n", pos );

   _close( fh );
}
```

### <a name="input-crt_lseekc_input"></a>Entrada: crt_lseek.c_input

```Input
Line one.
Line two.
Line three.
Line four.
Line five.
```

### <a name="output"></a>Resultados

```Output
Position for beginning of file seek = 0
Position for current position seek = 10
Position for end of file seek = 57
```

## <a name="see-also"></a>Vea también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_tell, _telli64](tell-telli64.md)<br/>
