---
title: clearerr_s
ms.date: 4/2/2020
api_name:
- clearerr_s
- _o_clearerr_s
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
- clearerr_s
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
ms.openlocfilehash: a8f8978b9d46d8d903f8256424d47c84bec649ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350056"
---
# <a name="clearerr_s"></a>clearerr_s

Restablece el indicador de error de una secuencia. Se trata de una versión de [clearerr](clearerr.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t clearerr_s(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*Corriente*<br/>
Puntero a la estructura **de archivo**

## <a name="return-value"></a>Valor devuelto

Cero si se realiza correctamente; **EINVAL** si *stream* es **NULL**.

## <a name="remarks"></a>Observaciones

La función **clearerr_s** restablece el indicador de error y el indicador de fin de archivo para *el flujo*. Los indicadores de error no se borran automáticamente; una vez establecido el indicador de error para una secuencia especificada, las operaciones de esa secuencia siguen devolviendo un valor de error hasta que se llama a **clearerr_s**, **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**o [rewind.](rewind.md)

Si *stream* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno en** **EINVAL** y devuelve **EINVAL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**clearerr_s**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_clearerr_s.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   errno_t err;

   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }
}
```

### <a name="input"></a>Entrada

```Input
n
```

### <a name="output"></a>Output

```Output
Write error: Bad file descriptor
Will input cause an error? n
```

## <a name="see-also"></a>Consulte también

[Manejo de errores](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
