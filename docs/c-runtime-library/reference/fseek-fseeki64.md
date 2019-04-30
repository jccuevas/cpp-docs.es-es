---
title: fseek, _fseeki64
ms.date: 11/04/2016
apiname:
- _fseeki64
- fseek
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
ms.openlocfilehash: e5f775eab370f8f4a3b6a5c1d7f0918ec7efa3ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287591"
---
# <a name="fseek-fseeki64"></a>fseek, _fseeki64

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

*stream*<br/>
Puntero a la estructura **FILE**.

*offset*<br/>
Número de bytes de *origin*.

*origin*<br/>
Posición inicial.

## <a name="return-value"></a>Valor devuelto

Si es correcto, **fseek** y **_fseeki64** devuelve 0. De lo contrario, devuelve un valor distinto de cero. En los dispositivos incapaces de efectuar búsquedas, el valor devuelto es indefinido. Si *secuencia* es un puntero nulo, o si *origen* no es uno de los valores permitidos que se describe a continuación, **fseek** y **_fseeki64** invocar el no válido controlador de parámetros, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devuelven -1.

## <a name="remarks"></a>Comentarios

El **fseek** y **_fseeki64** funciones mueve el puntero de archivo (si existe) asociado con *secuencia* a una nueva ubicación es *desplazamiento* bytes de *origen*. La siguiente operación de la secuencia se realiza en la nueva ubicación. En una secuencia abierta para actualización, la siguiente operación puede ser de lectura o de escritura. El argumento *origen* debe ser una de las siguientes constantes, definidas en STDIO. H:

|valor de origen|Significado|
|-|-|
| **SEEK_CUR** | Posición actual del puntero de archivo. |
| **SEEK_END** | Final de archivo. |
| **SEEK_SET** | Principio de archivo. |

Puede usar **fseek** y **_fseeki64** a colocar el puntero en cualquier lugar en un archivo. El puntero también puede colocarse más allá del final del archivo. **fseek** y **_fseeki64** borra el indicador de fin de archivo y anulan el efecto de las anteriores [ungetc](ungetc-ungetwc.md) llama contra *secuencia*.

Cuando un archivo se abre para anexar datos, la posición de archivo actual se determina con la última operación de E/S, no en función de dónde se produciría la siguiente escritura. Si todavía no se ha producido ninguna operación de E/S en un archivo abierto para anexar, la posición de archivo se sitúa al principio del archivo.

Para las secuencias que se abre en modo de texto, **fseek** y **_fseeki64** dispone de un uso limitado, ya que pueden hacer que las traducciones de avance de línea de retorno de carro **fseek** y **_ fseeki64** para producir resultados inesperados. La única **fseek** y **_fseeki64** garantizadas que funcionan con las secuencias abiertas en modo de texto de las operaciones son:

- Búsqueda con un desplazamiento de 0 en relación con cualquiera de los valores de origen.

- Búsqueda desde el principio del archivo con un valor de desplazamiento devuelto desde una llamada a [ftell](ftell-ftelli64.md) al usar **fseek** o [_ftelli64](ftell-ftelli64.md) al usar **_fseeki64**.

Además, en modo de texto, CTRL+Z se interpreta como un carácter de final de archivo en la entrada. En los archivos abiertos para lectura/escritura, [fopen](fopen-wfopen.md) y todas las rutinas relacionadas buscan un CTRL+Z al final del archivo y quitarlo si es posible. Esto se hace porque usa la combinación de **fseek** y [ftell](ftell-ftelli64.md) o **_fseeki64** y [_ftelli64](ftell-ftelli64.md)para desplazarse a un archivo que termina con puede provocar un CTRL+Z **fseek** o **_fseeki64** para que se comporte de forma incorrecta cerca del final del archivo.

Cuando CRT abre un archivo que comienza con una marca BOM (Byte Order Mark), el puntero de archivo se sitúa después de esta marca (es decir, al principio del contenido real del archivo). Si tiene que **fseek** al principio del archivo, use [ftell](ftell-ftelli64.md) para obtener la posición inicial y **fseek** a ella en lugar de a la posición 0.

Esta función bloquea otros subprocesos durante la ejecución y por lo tanto es segura para subprocesos. Para obtener una versión que no sea de bloqueo, consulte [_fseek_nolock, _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md).

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

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
