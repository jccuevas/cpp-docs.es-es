---
title: clearerr
ms.date: 11/04/2016
apiname:
- clearerr
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: c282a577bb7496f899f18abeac857c08388d12f6
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328258"
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

*secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="remarks"></a>Comentarios

El **clearerr** función restablece el indicador de error y el indicador de fin de archivo para *secuencia*. Los indicadores de error no se borran automáticamente; una vez establecido el indicador de error para una secuencia especificada, las operaciones en esa secuencia seguirán devolviendo un valor de error hasta que **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**, o [rebobinar](rewind.md) se llama.

Si *secuencia* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve. Para obtener más información sobre **errno** y códigos de error, vea [errno (constantes)](../../c-runtime-library/errno-constants.md).

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

### <a name="output"></a>Salida

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
