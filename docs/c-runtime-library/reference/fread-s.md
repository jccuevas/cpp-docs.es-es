---
title: fread_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fread_s
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
- fread_s
- stdio/fread_s
dev_langs:
- C++
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: febfab21889afab773dd9a8405b1e07dc7798f5c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="freads"></a>fread_s

Lee datos desde una secuencia. Esta versión de [fread](fread.md) incluye mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
size_t fread_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Ubicación de almacenamiento de los datos.

*BufferSize*<br/>
Tamaño del búfer de destino en bytes.

*elementSize*<br/>
Tamaño del elemento que se va a leer en bytes.

*count*<br/>
Número máximo de elementos que se va a leer.

*Secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fread_s** devuelve el número de (total) de elementos leídos en el búfer, que puede ser menor que *recuento* si se encuentra un error de lectura o el final del archivo antes de *recuento* se alcanza. Use la **feof** o **ferror** función para distinguir un error de una condición de final de archivo. Si *tamaño* o *recuento* es 0, **fread_s** devuelve 0 y el contenido del búfer no se modifican. Si *flujo* o *búfer* es un puntero nulo, **fread_s** invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve 0.

Para obtener más información sobre códigos de error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **fread_s** función lee hasta *recuento* elementos de *elementSize* bytes a partir de la entrada *flujo* y los almacena en *búfer*.  El puntero de archivo que está asociado a *flujo* (si existe) se incrementa el número de bytes leídos realmente. Si la secuencia especificada se abre en modo de texto, pares de avance de línea de retorno de carro se reemplazan por caracteres de avance de línea única. Este reemplazo no tiene ningún efecto en el puntero de archivo ni en el valor devuelto. Si se produce un error, la posición del puntero de archivo es indeterminada. No se puede determinar el valor de un elemento leído parcialmente.

Esta función bloquea otros subprocesos. Si necesita una versión no realiza el bloqueo, utilice **_fread_nolock**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fread_s**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```cpp
// crt_fread_s.c
// Command line: cl /EHsc /nologo /W4 crt_fread_s.c
//
// This program opens a file that's named FREAD.OUT and
// writes characters to the file. It then tries to open
// FREAD.OUT and read in characters by using fread_s. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

#define BUFFERSIZE 30
#define DATASIZE 22
#define ELEMENTCOUNT 2
#define ELEMENTSIZE (DATASIZE/ELEMENTCOUNT)
#define FILENAME "FREAD.OUT"

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   for ( i = 0; i < DATASIZE; i++ )
      list[i] = (char)('z' - i);
   list[DATASIZE] = '\0'; // terminal null so we can print it

   // Open file in text mode:
   if( fopen_s( &stream, FILENAME, "w+t" ) == 0 )
   {
      // Write DATASIZE characters to stream
      printf( "Contents of buffer before write/read:\n\t%s\n\n", list );
      numwritten = fwrite( list, sizeof( char ), DATASIZE, stream );
      printf( "Wrote %d items\n\n", numwritten );
      fclose( stream );
   } else {
      printf( "Problem opening the file\n" );
      return -1;
   }

   if( fopen_s( &stream, FILENAME, "r+t" ) == 0 )   {
      // Attempt to read in characters in 2 blocks of 11
      numread = fread_s( list, BUFFERSIZE, ELEMENTSIZE, ELEMENTCOUNT, stream );
      printf( "Number of %d-byte elements read = %d\n\n", ELEMENTSIZE, numread );
      printf( "Contents of buffer after write/read:\n\t%s\n", list );
      fclose( stream );
   } else {
      printf( "File could not be opened\n" );
      return -1;
   }
}
```

```Output
Contents of buffer before write/read:
        zyxwvutsrqponmlkjihgfe

Wrote 22 items

Number of 11-byte elements read = 2

Contents of buffer after write/read:
        zyxwvutsrqponmlkjihgfe
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
