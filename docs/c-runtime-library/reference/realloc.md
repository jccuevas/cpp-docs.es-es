---
title: realloc
ms.date: 4/2/2020
api_name:
- realloc
- _o_realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
ms.openlocfilehash: 15c818ee6f70d02fb9b63f12deef6b1bf3698322
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917939"
---
# <a name="realloc"></a>realloc

Reasigna bloques de memoria.

## <a name="syntax"></a>Sintaxis

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria asignado previamente.

*size*<br/>
Nuevo tamaño en bytes.

## <a name="return-value"></a>Valor devuelto

**realloc** devuelve un puntero **void** al bloque de memoria reasignado (y que posiblemente se ha cambiado).

Si no hay suficiente memoria disponible para expandir el bloque hasta el tamaño especificado, el bloque original permanece inalterado y se devuelve **null** .

Si el *tamaño* es cero, se libera el bloque señalado por *memblock* ; el valor devuelto es **null**y *memblock* está apuntando a un bloque liberado.

El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto de **void**, use una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Observaciones

La función **realloc** cambia el tamaño de un bloque de memoria asignado. El argumento *memblock* apunta al principio del bloque de memoria. Si *memblock* es **null**, **realloc** se comporta de la misma manera que **malloc** y asigna un nuevo bloque de bytes de *tamaño* . Si *memblock* no es **null**, debe ser un puntero devuelto por una llamada anterior a **calloc**, **malloc**o **realloc**.

El argumento *size* proporciona el nuevo tamaño del bloque, en bytes. El contenido del bloque es igual hasta el más pequeño de los tamaños nuevo y antiguo, aunque el bloque nuevo puede estar en otra ubicación. Dado que el nuevo bloque puede estar en una nueva ubicación de memoria, no se garantiza que el puntero devuelto por **realloc** sea el puntero que se pasa a través del argumento *memblock* . **realloc** no tiene ninguna memoria recién asignada en el caso del crecimiento del búfer.

**realloc** establece **errno** en **ENOMEM** si se produce un error en la asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** llama a **malloc** para usar la función de [_set_new_mode](set-new-mode.md) de C++ con el fin de establecer el nuevo modo de controlador. El nuevo modo de controlador indica si, en caso de error, **malloc** es llamar a la rutina del nuevo controlador tal y como se establece en [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del nuevo controlador en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **realloc** no pueda asignar memoria, **malloc** llame a la rutina del nuevo controlador de la misma manera que el operador **New** cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a

```C
_set_new_mode(1);
```

temprano en un programa o vincúlelo con NEWMODE.OBJ (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)).

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **realloc** se resuelve como [_realloc_dbg](realloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**realloc** está marcado `__declspec(noalias)` como `__declspec(restrict)`y, lo que significa que se garantiza que la función no modifica las variables globales y que el puntero devuelto no tiene alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**realloc**|\<stdlib.h> y \<malloc.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_realloc.c
// This program allocates a block of memory for
// buffer and then uses _msize to display the size of that
// block. Next, it uses realloc to expand the amount of
// memory used by buffer and then calls _msize again to
// display the new amount of memory allocated to buffer.

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   long *buffer, *oldbuffer;
   size_t size;

   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )
      exit( 1 );

   size = _msize( buffer );
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );

   // Reallocate and show new size:
   oldbuffer = buffer;     // save pointer in case realloc fails
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))
        ==  NULL )
   {
      free( oldbuffer );  // free original block
      exit( 1 );
   }
   size = _msize( buffer );
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",
            size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after malloc of 1000 longs: 4000
Size of block after realloc of 1000 more longs: 8000
```

## <a name="see-also"></a>Consulte también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[ningún](free.md)<br/>
[malloc](malloc.md)<br/>
