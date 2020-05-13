---
title: feof
ms.date: 4/2/2020
api_name:
- feof
- _o_feof
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
- feof
helpviewer_keywords:
- end of file, testing for
- feof function
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
ms.openlocfilehash: 2b3a8d35491272409ecf911fe2f98ca60b2b2b38
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920165"
---
# <a name="feof"></a>feof

Pruebas de fin de archivo en una secuencia.

## <a name="syntax"></a>Sintaxis

```C
int feof(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*misiones*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

La función **feof** devuelve un valor distinto de cero si una operación de lectura ha intentado leer más allá del final del archivo; devuelve 0 en caso contrario. Si el puntero de secuencia es **null**, la función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y **feof** devuelve 0.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Observaciones

La rutina **feof** (implementada como una función y como una macro) determina si se ha pasado el final de la *secuencia* . Cuando se pasa el final del archivo, las operaciones de lectura devuelven un indicador de fin de archivo hasta que se cierra la secuencia o hasta que se llama a [rebobinar](rewind.md), **fsetpos**, [fseek](fseek-fseeki64.md)o **clearerr** .

Por ejemplo, si un archivo contiene 10 bytes y Lee 10 bytes del archivo, **feof** devolverá 0 porque, aunque el puntero de archivo está al final del archivo, no ha intentado leer más allá del final. Solo después de intentar leer un undécimo byte, **feof** devolverá un valor distinto de cero.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**feof**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_feof.c
// This program uses feof to indicate when
// it reaches the end of the file CRT_FEOF.TXT. It also
// checks for errors with ferror.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int  count, total = 0;
   char buffer[100];
   FILE *stream;

   fopen_s( &stream, "crt_feof.txt", "r" );
   if( stream == NULL )
      exit( 1 );

   // Cycle until end of file reached:
   while( !feof( stream ) )
   {
      // Attempt to read in 100 bytes:
      count = fread( buffer, sizeof( char ), 100, stream );
      if( ferror( stream ) )      {
         perror( "Read error" );
         break;
      }

      // Total up actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   fclose( stream );
}
```

## <a name="input-crt_feoftxt"></a>Entrada: crt_feof.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Salida

```Output
Number of bytes read = 19
```

## <a name="see-also"></a>Vea también

[Tratamiento de errores](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
