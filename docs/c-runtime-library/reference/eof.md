---
title: _eof
ms.date: 4/2/2020
api_name:
- _eof
- _o__eof
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _eof
helpviewer_keywords:
- eof function
- end of file, testing for
- _eof function
- files [C++], end of
- testing, for end-of-file
- end of file
ms.assetid: 265703f4-d07e-4005-abf3-b1d0cdd9e0b0
ms.openlocfilehash: 5d00be1da0f329c43f1b6ea0f912ede74b307bbb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915053"
---
# <a name="_eof"></a>_eof

Pruebas de fin de archivo (EOF).

## <a name="syntax"></a>Sintaxis

```C
int _eof(
   int fd
);
```

### <a name="parameters"></a>Parámetros

*FD*<br/>
Descriptor de archivo que hace referencia al archivo abierto.

## <a name="return-value"></a>Valor devuelto

**_eof** devuelve 1 si la posición actual es el final del archivo, o 0 si no lo es. Un valor devuelto de-1 indica un error; en este caso, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EBADF**, lo que indica que el descriptor de archivo no es válido.

## <a name="remarks"></a>Observaciones

La función **_eof** determina si se ha alcanzado el final del archivo asociado a *FD* .

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezado opcional|
|--------------|---------------------|---------------------|
|**_eof**|\<io.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_eof.c
// This program reads data from a file
// ten bytes at a time until the end of the
// file is reached or an error is encountered.
//
#include <io.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   int  fh, count, total = 0;
   char buf[10];
   if( _sopen_s( &fh, "crt_eof.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
   {
        perror( "Open failed");
        exit( 1 );
   }
   // Cycle until end of file reached:
   while( !_eof( fh ) )
   {
      // Attempt to read in 10 bytes:
      if( (count = _read( fh, buf, 10 )) == -1 )
      {
         perror( "Read error" );
         break;
      }
      // Total actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   _close( fh );
}
```

### <a name="input-crt_eoftxt"></a>Entrada: crt_eof.txt

```Input
This file contains some text.
```

### <a name="output"></a>Salida

```Output
Number of bytes read = 29
```

## <a name="see-also"></a>Vea también

[Tratamiento de errores](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
