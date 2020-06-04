---
title: _expand_dbg
ms.date: 11/04/2016
api_name:
- _expand_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: 836b9cffcf0367f248a14469b30c1a355e2bdec2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941577"
---
# <a name="_expand_dbg"></a>_expand_dbg

Cambia el tamaño de un bloque de memoria especificado en el montón, ya sea expandiendo o contrayendo el bloque (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void *_expand_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*userData*<br/>
Puntero al bloque de memoria asignado previamente.

*newSize*<br/>
Nuevo tamaño solicitado para el bloque (en bytes).

*blockType*<br/>
Tipo solicitado para el bloque cuyo tamaño se ha cambiado: _ **client_block** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de expansión o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente donde se solicitó la operación de expansión o **null**.

Los parámetros *filename* y *lineNumber* solo están disponibles cuando se ha llamado a **_expand_dbg** explícitamente o se ha definido la constante de preprocesador _ [crtdbg_map_alloc](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Valor devuelto

Cuando se completa correctamente, **_expand_dbg** devuelve un puntero al bloque de memoria cuyo tamaño se ha cambiado. Dado que la memoria no se mueve, la dirección es la misma que la de userData. Si se produjo un error o el bloque no se puede expandir al tamaño solicitado, devuelve **null**. Si se produce un error, **errno** es con información del sistema operativo sobre la naturaleza del error. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **_expand_dbg** es una versión de depuración de la función _[Expand](expand.md) . Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , cada llamada a **_expand_dbg** se reduce a una llamada a **_expand**. Tanto **_expand** como **_expand_dbg** cambiar el tamaño de un bloque de memoria en el montón base, pero **_expand_dbg** admite varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque para comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento. tipos de asignación específicos e información de *nombre de archivo*/*lineNumber* para determinar el origen de las solicitudes de asignación.

**_expand_dbg** cambia el tamaño del bloque de memoria especificado con un poco más de espacio que el de la *NewSize*solicitada. *NewSize* puede ser mayor o menor que el tamaño del bloque de memoria asignado originalmente. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. El cambio de tamaño es realiza expandiendo o contrayendo el bloque de memoria original. **_expand_dbg** no mueve el bloque de memoria, al igual que la función [_realloc_dbg](realloc-dbg.md) .

Cuando *NewSize* es mayor que el tamaño de bloque original, el bloque de memoria se expande. Durante una expansión, si el bloque de memoria no se puede expandir para acomodar el tamaño solicitado, se devuelve **null** . Cuando *NewSize* es menor que el tamaño de bloque original, el bloque de memoria se contrata hasta que se obtiene el nuevo tamaño.

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Esta función valida sus parámetros. Si *memblock* es un puntero nulo, o si el tamaño es mayor que **_HEAP_MAXREQ**, esta función invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **null**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_expand_dbg.c
//
// This program allocates a block of memory using _malloc_dbg
// and then calls _msize_dbg to display the size of that block.
// Next, it uses _expand_dbg to expand the amount of
// memory used by the buffer and then calls _msize_dbg again to
// display the new amount of memory allocated to the buffer.
//

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   long *buffer;
   size_t size;

   // Call _malloc_dbg to include the filename and line number
   // of our allocation request in the header
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );
   if( buffer == NULL )
      exit( 1 );

   // Get the size of the buffer by calling _msize_dbg
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

   // Expand the buffer using _expand_dbg and show the new size
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );

   if( buffer == NULL )
      exit( 1 );
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",
           size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _expand_dbg of 1 more long: 164
```

## <a name="comment"></a>Comentario

El resultado de este programa depende de la capacidad del equipo de expandir todas las secciones. Si se expanden todas las secciones, el resultado se refleja en la sección de salida.

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
