---
title: clearerr
ms.date: 11/04/2016
api_name:
- clearerr
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
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: 9fd2f7e7dfcf272e806a887b356418b7555913f5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942946"
---
# <a name="clearerr"></a>clearerr

Restablece el indicador de error de una secuencia. Hay disponible una versión más segura de esta función; consulte [clearerr_s](clearerr-s.md).

## <a name="syntax"></a>Sintaxis

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*stream*<br/>
Puntero a la estructura **FILE**.

## <a name="remarks"></a>Comentarios

La función **clearerr** restablece el indicador de error y el indicador de fin de archivo para el *flujo*. Los indicadores de error no se borran automáticamente; una vez establecido el indicador de error para una secuencia especificada, las operaciones en esa secuencia seguirán devolviendo un valor de error hasta que se llame a **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**o [Rewind](rewind.md) .

Si *Stream* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve. Para obtener más información sobre **errno** y los códigos de error, vea [errno (constantes](../../c-runtime-library/errno-constants.md)).

Hay disponible una versión más segura de esta función; consulte [clearerr_s](clearerr-s.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_clearerr.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      clearerr( stdin );
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      clearerr( stdin );
   }
   else
      printf( "No read error\n" );
}
```

### <a name="input"></a>Entrada

```Input
n
```

### <a name="output"></a>Resultados

```Output
Write error: No error
Will input cause an error? n
No read error
```

## <a name="see-also"></a>Vea también

[Control de errores](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
