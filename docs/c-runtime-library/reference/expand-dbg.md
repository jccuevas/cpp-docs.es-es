---
title: _expand_dbg
ms.date: 11/04/2016
apiname:
- _expand_dbg
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
apitype: DLLExport
f1_keywords:
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: cc3aa2b7e39b52eb71ac10a9b5c4a221ba6fb70c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288050"
---
# <a name="expanddbg"></a>_expand_dbg

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
Tipo solicitado para el bloque cuyo tamaño ha cambiado: **_CLIENT_BLOCK** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de expansión o **NULL**.

*linenumber*<br/>
Número de línea en el archivo de origen que se solicitó la operación de expansión o **NULL**.

El *filename* y *linenumber* parámetros solo están disponibles cuando **_expand_dbg** se ha llamado explícitamente o [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)se ha definido la constante de preprocesador.

## <a name="return-value"></a>Valor devuelto

Se completa correctamente, **_expand_dbg** devuelve un puntero al bloque de memoria cuyo tamaño ha cambiado. Dado que la memoria no se mueve, la dirección es la misma que la de userData. Si se produjo un error o no se pudo expandir el bloque al tamaño solicitado, devuelve **NULL**. Si se produce un error, **errno** es con la información del sistema operativo sobre la naturaleza del error. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_expand_dbg** función es una versión de depuración de la _[expanda](expand.md) función. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_expand_dbg** se reduce a una llamada a **_expand**. Ambos **_expand** y **_expand_dbg** cambiar el tamaño de un bloque de memoria del montón base, pero **_expand_dbg** admite varias características de depuración: búferes situados a cada lado del usuario parte del bloque para comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar un seguimiento de los tipos de asignación concretos, y *filename*/*linenumber* información para determinar el origen de solicitudes de asignación.

**_expand_dbg** cambia el tamaño de bloque de memoria especificado con un poco más de espacio solicitado *newSize*. *newSize* podría ser mayor o menor que el tamaño del bloque de memoria asignado originalmente. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. El cambio de tamaño es realiza expandiendo o contrayendo el bloque de memoria original. **_expand_dbg** no mueve el bloque de memoria, como hace el [_realloc_dbg](realloc-dbg.md) función.

Cuando *newSize* es mayor que el bloque original se expande en tamaño, el bloque de memoria. Durante una extensión, si el bloque de memoria no se puede expandir para adaptarse al tamaño solicitado, **NULL** se devuelve. Cuando *newSize* es menor que el bloque original se contrata tamaño, el bloque de memoria hasta que se obtenga el nuevo tamaño.

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Esta función valida sus parámetros. Si *memblock* es un puntero nulo, o si el tamaño es mayor que **_HEAP_MAXREQ**, esta función invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **NULL**.

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
