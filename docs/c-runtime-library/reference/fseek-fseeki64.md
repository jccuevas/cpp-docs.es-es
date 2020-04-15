---
title: fseek, _fseeki64
ms.date: 4/2/2020
api_name:
- _fseeki64
- fseek
- _o__fseeki64
- _o_fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: e8f6021a0b770f6b435653c190d5968f9ac50a57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345765"
---
# <a name="fseek-_fseeki64"></a>fseek, _fseeki64

Mueve el puntero de archivo a una ubicación especificada.

## <a name="syntax"></a>Sintaxis

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parámetros

*Corriente*<br/>
Puntero a la estructura **FILE**.

*offset*<br/>
Número de bytes de *origin*.

*Origen*<br/>
Posición inicial.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **fseek** y **_fseeki64** devuelve 0. De lo contrario, devuelve un valor distinto de cero. En los dispositivos incapaces de efectuar búsquedas, el valor devuelto es indefinido. Si *stream* es un puntero nulo, o si *origin* no es uno de los valores permitidos que se describen a continuación, **fseek** y **_fseeki64** invocan el controlador de parámetros no válidos, como se describe en Validación de [parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno en** **EINVAL** y devuelven -1.

## <a name="remarks"></a>Observaciones

Las funciones **fseek** y **_fseeki64** mueven el puntero de archivo (si existe) asociado a la *secuencia* a una nueva ubicación que es bytes *de desplazamiento* desde *el origen.* La siguiente operación de la secuencia se realiza en la nueva ubicación. En una secuencia abierta para actualización, la siguiente operación puede ser de lectura o de escritura. El *origen* del argumento debe ser una de las siguientes constantes, definida en STDIO. H:

|valor de origen|Significado|
|-|-|
| **SEEK_CUR** | Posición actual del puntero de archivo. |
| **SEEK_END** | Final de archivo. |
| **SEEK_SET** | Principio de archivo. |

Puede utilizar **fseek** y **_fseeki64** para cambiar la posición del puntero en cualquier lugar de un archivo. El puntero también puede colocarse más allá del final del archivo. **fseek** y **_fseeki64** borra el indicador de fin de archivo y niega el efecto de cualquier llamada [ungetc](ungetc-ungetwc.md) anterior contra *la secuencia.*

Cuando un archivo se abre para anexar datos, la posición de archivo actual se determina con la última operación de E/S, no en función de dónde se produciría la siguiente escritura. Si todavía no se ha producido ninguna operación de E/S en un archivo abierto para anexar, la posición de archivo se sitúa al principio del archivo.

Para las secuencias abiertas en modo de texto, **fseek** y **_fseeki64** tienen un uso limitado, ya que las traducciones de avance de línea de retorno de carro pueden provocar que **fseek** y **_fseeki64** produzcan resultados inesperados. Las únicas operaciones **de fseek** y **_fseeki64** garantizadas para trabajar en secuencias abiertas en modo de texto son:

- Búsqueda con un desplazamiento de 0 en relación con cualquiera de los valores de origen.

- Búsqueda desde el principio del archivo con un valor de desplazamiento devuelto de una llamada a [ftell](ftell-ftelli64.md) cuando se usa **fseek** o [_ftelli64](ftell-ftelli64.md) cuando se usa **_fseeki64**.

Además, en modo de texto, CTRL+Z se interpreta como un carácter de final de archivo en la entrada. En los archivos abiertos para lectura/escritura, [fopen](fopen-wfopen.md) y todas las rutinas relacionadas comprueban si hay CTRL+Z al final del archivo y la quitan si es posible. Esto se hace porque el uso de la combinación de **fseek** y [ftell](ftell-ftelli64.md) o **_fseeki64** y [_ftelli64](ftell-ftelli64.md), para moverse dentro de un archivo que termina con CTRL+Z puede hacer que **fseek** o **_fseeki64** se comporten incorrectamente cerca del final del archivo.

Cuando CRT abre un archivo que comienza con una marca BOM (Byte Order Mark), el puntero de archivo se sitúa después de esta marca (es decir, al principio del contenido real del archivo). Si tiene que **fseek** al principio del archivo, utilice [ftell](ftell-ftelli64.md) para obtener la posición inicial y **fseek** a él en lugar de colocar 0.

Esta función bloquea otros subprocesos durante la ejecución y por lo tanto es segura para subprocesos. Para obtener una versión que no sea de bloqueo, consulte [_fseek_nolock, _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[Rebobinado](rewind.md)<br/>
