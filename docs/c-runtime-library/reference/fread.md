---
title: fread
ms.date: 11/28/2018
apiname:
- fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 4f9cb6940d1708dffd5d5ca03fac28397f1db846
ms.sourcegitcommit: 53bfb772c43319d49686c167f492606348ad362b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52819701"
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

*buffer*<br/>
Ubicación de almacenamiento de los datos.

*size*<br/>
Tamaño del elemento en bytes.

*count*<br/>
Número máximo de elementos que se va a leer.

*secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fread** devuelve el número de elementos completos leído realmente, que puede ser menor que *recuento* si se produce un error o si se encuentra el final del archivo antes de llegar a *recuento*. Use la **feof** o **ferror** función para distinguir un error de lectura de una condición de final de archivo. Si *tamaño* o *recuento* es 0, **fread** devuelve 0 y el contenido del búfer es iguales. Si *secuencia* o *búfer* es un puntero nulo, **fread** invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve 0.

Consulte [ \_doserrno, errno, \_sys\_errlist, y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos códigos de error.

## <a name="remarks"></a>Comentarios

El **fread** función lee hasta *recuento* elementos de *tamaño* bytes en la entrada *secuencia* y los almacena en *búfer* . El puntero de archivo asociado *secuencia* (si existe) se aumenta el número de bytes leídos realmente. Si la secuencia dada se abre en [modo de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md), nuevas líneas de estilo de Windows se convierten en nuevas líneas de estilo Unix. Es decir, los pares de retorno-salto de línea (CRLF) de transporte se reemplazan por caracteres de avance de línea (LF). Este reemplazo no tiene ningún efecto en el puntero de archivo ni en el valor devuelto. Si se produce un error, la posición del puntero de archivo es indeterminada. No se puede determinar el valor de un elemento leído parcialmente.

Cuando se utiliza en una secuencia de modo de texto, si la cantidad de datos solicitada (es decir, *tamaño* \* *recuento*) es mayor o igual que la interna **archivo** \*tamaño del búfer (de forma predeterminada es 4096 bytes, puede configurables mediante el uso de [setvbuf](../../c-runtime-library/reference/setvbuf.md)), datos de la secuencia se copia directamente en el búfer proporcionado por el usuario, y se realiza la conversión de nueva línea en ese búfer. Dado que los datos convertidos pueden ser menos que los datos de secuencia copiados en el búfer de datos pasados *búfer*\[*return_value* \* *tamaño*] () donde *return_value* es el valor devuelto de **fread**) puede contener datos del archivo no convertidos. Por este motivo, se recomienda que termine en null los datos de caracteres en *búfer*\[*return_value* \* *tamaño*] si es la intención del búfer para que actúe como una cadena de estilo C. Consulte [fopen](fopen-wfopen.md) para obtener más información sobre los efectos del modo de texto y en modo binario.

Esta función bloquea otros subprocesos. Si tiene una versión que no sea de bloqueo, use **_fread_nolock**.

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

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[E/S de archivo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br />
[fopen](fopen-wfopen.md)<br />
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
