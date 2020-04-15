---
title: calloc
description: La función calloc de la biblioteca en tiempo de ejecución de C asigna memoria inicializada sin capacidad.
ms.date: 4/2/2020
api_name:
- calloc
- _o_calloc
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
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: fb4f7d6dc059023d34cb0b811edf5dfb48cb7a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333647"
---
# <a name="calloc"></a>calloc

Asigna una matriz en la memoria con elementos que se inicializan en 0.

## <a name="syntax"></a>Sintaxis

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*number*<br/>
Número de elementos.

*Tamaño*<br/>
Longitud en bytes de cada elemento.

## <a name="return-value"></a>Valor devuelto

**calloc** devuelve un puntero al espacio asignado. Se garantiza que el espacio de almacenamiento al que apunta el valor devuelto esté alineado correctamente para el almacenamiento de todo tipo de objeto. Para obtener un puntero a un tipo distinto de **void**, utilice una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Observaciones

La función **calloc** asigna espacio de almacenamiento para una matriz de elementos *numéricos,* cada uno de bytes de *tamaño* de longitud. Cada elemento se inicializa en 0.

**calloc** establece **errno** en **ENOMEM** si se produce un error en una asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

En la implementación de Microsoft, si *el número* o el *tamaño* es cero, **calloc** devuelve un puntero a un bloque asignado de tamaño distinto de cero. Un intento de leer o escribir a través del puntero devuelto conduce a un comportamiento indefinido.

**calloc** utiliza la función [de _set_new_mode](set-new-mode.md) C++ para establecer el nuevo modo de *controlador.* El nuevo modo de controlador indica si, en caso de error, **calloc** debe llamar a la nueva rutina de controlador según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **calloc** no llama a la nueva rutina de controlador en caso de error para asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **calloc** no pueda asignar memoria, llame a la nueva rutina de controlador de la misma manera que lo hace el operador **new** cuando se produce un error por el mismo motivo. Para invalidar el valor predeterminado, llame a

```C
_set_new_mode(1);
```

al principio de su programa, o enlace con *NEWMODE. OBJ* (consulte [Opciones de enlace](../../c-runtime-library/link-options.md)).

Cuando la aplicación está vinculada con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **calloc** se resuelve en [_calloc_dbg](calloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** está `__declspec(noalias)` `__declspec(restrict)`marcado y , lo que significa que se garantiza que la función no modifique las variables globales y que el puntero devuelto no tiene alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**calloc**|\<stdlib.h> y \<malloc.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_calloc.c
// This program uses calloc to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>

int main( void )
{
   long *buffer;

   buffer = (long *)calloc( 40, sizeof( long ) );
   if( buffer != NULL )
      printf( "Allocated 40 long integers\n" );
   else
      printf( "Can't allocate memory\n" );
   free( buffer );
}
```

```Output
Allocated 40 long integers
```

## <a name="see-also"></a>Consulte también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[Gratis](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
