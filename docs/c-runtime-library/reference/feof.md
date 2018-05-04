---
title: feof | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- feof
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
- feof
dev_langs:
- C++
helpviewer_keywords:
- end of file, testing for
- feof function
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3162fd72acdfedc198764a92deec043cd681a10
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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

*Secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

El **feof** función devuelve un valor distinto de cero si se ha intentado una operación de lectura leer más allá del final del archivo; en caso contrario, devuelve 0. Si el puntero de la secuencia es **NULL**, la función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y **feof** devuelve 0.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Comentarios

El **feof** rutina (se implementa como una función y como una macro) determina si el final de *flujo* se ha pasado. Cuando se pasa el final del archivo, leer las operaciones devuelven un indicador de fin de archivo hasta que la secuencia está cerrada o hasta que [rebobinar](rewind.md), **fsetpos**, [fseek](fseek-fseeki64.md), o  **clearerr** se llama con ella.

Por ejemplo, si un archivo contiene 10 bytes y leer 10 bytes desde el archivo **feof** devolverá 0 porque, aunque el puntero de archivo está al final del archivo, no ha intentado leer más allá del final. Solo una vez que vuelva a intenta leer un byte 11 hará **feof** devuelve un valor distinto de cero.

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

## <a name="input-crtfeoftxt"></a>Entrada: crt_feof.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Salida

```Output
Number of bytes read = 19
```

## <a name="see-also"></a>Vea también

[Control de errores](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
