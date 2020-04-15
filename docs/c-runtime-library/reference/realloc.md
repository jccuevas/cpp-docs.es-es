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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 964c465a95d44de9d8a4d399f23ec43f8a3a6692
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332929"
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

*Tamaño*<br/>
Nuevo tamaño en bytes.

## <a name="return-value"></a>Valor devuelto

**realloc** devuelve un puntero **void** al bloque de memoria reasignado (y posiblemente movido).

Si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado, el bloque original se deja sin cambios y se devuelve **NULL.**

Si *el tamaño* es cero, el bloque al que apunta *memblock* se libera; el valor devuelto es **NULL**y *memblock* se deja apuntando a un bloque liberado.

El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto de **void**, utilice una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Observaciones

La función **realloc** cambia el tamaño de un bloque de memoria asignado. El argumento *memblock* apunta al principio del bloque de memoria. Si *memblock* es **NULL**, **realloc** se comporta de la misma manera que **malloc** y asigna un nuevo bloque de bytes de *tamaño.* Si *memblock* no es **NULL**, debe ser un puntero devuelto por una llamada anterior a **calloc**, **malloc**o **realloc**.

El argumento *size* proporciona el nuevo tamaño del bloque, en bytes. El contenido del bloque es igual hasta el más pequeño de los tamaños nuevo y antiguo, aunque el bloque nuevo puede estar en otra ubicación. Dado que el nuevo bloque puede estar en una nueva ubicación de memoria, no se garantiza que el puntero devuelto por **realloc** sea el puntero pasado a través del argumento *memblock.* **realloc** no pone la memoria recién asignada en el caso de crecimiento del búfer.

**realloc** establece **errno** en **ENOMEM** si se produce un error en la asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ.** Para obtener información sobre este y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** llama a **malloc** para utilizar la función [de _set_new_mode](set-new-mode.md) C++ para establecer el nuevo modo de controlador. El nuevo modo de controlador indica si, en caso de error, **malloc** debe llamar a la nueva rutina de controlador según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la nueva rutina de controlador al no asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **realloc** no pueda asignar memoria, **malloc** llama a la nueva rutina de controlador de la misma manera que lo hace el operador **new** cuando se produce un error por el mismo motivo. Para invalidar el valor predeterminado, llame a

```C
_set_new_mode(1);
```

temprano en un programa o vincúlelo con NEWMODE.OBJ (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)).

Cuando la aplicación está vinculada con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **realloc** se resuelve en [_realloc_dbg](realloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**realloc** está `__declspec(noalias)` `__declspec(restrict)`marcado y , lo que significa que se garantiza que la función no modifique las variables globales y que el puntero devuelto no tenga alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

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
[Gratis](free.md)<br/>
[malloc](malloc.md)<br/>
