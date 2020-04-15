---
title: fread
ms.date: 4/2/2020
api_name:
- fread
- _o_fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 26ffd56072f1a5fddc3131a42cd47c145e437b60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346064"
---
# <a name="fread"></a>fread

Lee datos desde una secuencia.

## <a name="syntax"></a>Sintaxis

```C
size_t fread(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*Búfer*<br/>
Ubicación de almacenamiento de los datos.

*Tamaño*<br/>
Tamaño del elemento en bytes.

*count*<br/>
Número máximo de elementos que se va a leer.

*Corriente*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fread** devuelve el número de elementos completos realmente leídos, que puede ser menor que *el recuento* si se produce un error o si se encuentra el final del archivo antes de llegar al *recuento*. Utilice la función **feof** o **ferror** para distinguir un error de lectura de una condición de fin de archivo. Si *size* o *count* es 0, **fread** devuelve 0 y el contenido del búfer no cambia. Si *stream* o *buffer* es un puntero nulo, **fread** invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno en** **EINVAL** y devuelve 0.

Consulte [ \_ \_doserrno, errno,\_sys \_errlist\_y sys nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos códigos de error.

## <a name="remarks"></a>Observaciones

La función **fread** lee hasta para *contar* elementos de bytes de *tamaño* de la *secuencia* de entrada y los almacena en *el búfer.* El puntero de archivo asociado a *la secuencia* (si hay uno) se incrementa por el número de bytes realmente leídos. Si la secuencia dada se abre en [modo de texto,](../../c-runtime-library/text-and-binary-mode-file-i-o.md)las líneas nuevas de estilo de Windows se convierten en líneas nuevas de estilo Unix. Es decir, los pares de avance de línea de retorno de carro (CRLF) se reemplazan por caracteres de avance de línea única (LF). Este reemplazo no tiene ningún efecto en el puntero de archivo ni en el valor devuelto. Si se produce un error, la posición del puntero de archivo es indeterminada. No se puede determinar el valor de un elemento leído parcialmente.

Cuando se utiliza en una secuencia de modo de texto, si la cantidad de datos solicitados (es *decir,* \* *el recuento*de tamaños ) es mayor o igual que el tamaño de búfer de **archivo** \* interno (de forma predeterminada, se puede configurar mediante [setvbuf](../../c-runtime-library/reference/setvbuf.md)), los datos de la secuencia se copian directamente en el búfer proporcionado por el usuario y la conversión de nueva línea se realiza en ese búfer. Dado que los datos convertidos pueden ser más cortos que los datos de secuencia copiados en el búfer, los datos pasados *del búfer*\[*return_value* \* *tamaño*] (donde *return_value* es el valor devuelto de **fread**) pueden contener datos no convertidos del archivo. Por este motivo, se recomienda establecer datos de caracteres de terminación nula en el *búfer*\[*return_value* \* *tamaño*] si la intención del búfer es actuar como una cadena de estilo C. Consulte [fopen](fopen-wfopen.md) para obtener más información sobre los efectos del modo de texto y el modo binario.

Esta función bloquea otros subprocesos. Si necesita una versión sin bloqueo, utilice **_fread_nolock**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fread.c
// This program opens a file named FREAD.OUT and
// writes 25 characters to the file. It then tries to open
// FREAD.OUT and read in 25 characters. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   // Open file in text mode:
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )
   {
      for ( i = 0; i < 25; i++ )
         list[i] = (char)('z' - i);
      // Write 25 characters to stream
      numwritten = fwrite( list, sizeof( char ), 25, stream );
      printf( "Wrote %d items\n", numwritten );
      fclose( stream );

   }
   else
      printf( "Problem opening the file\n" );

   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )
   {
      // Attempt to read in 25 characters
      numread = fread( list, sizeof( char ), 25, stream );
      printf( "Number of items read = %d\n", numread );
      printf( "Contents of buffer = %.25s\n", list );
      fclose( stream );
   }
   else
      printf( "File could not be opened\n" );
}
```

```Output
Wrote 25 items
Number of items read = 25
Contents of buffer = zyxwvutsrqponmlkjihgfedcb
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[E/S de texto y archivos binarios](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
