---
title: calloc
description: La función de biblioteca en tiempo de ejecución de C no asigna memoria inicializada en cero.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 76243342233ea895b947d4aa4a246b316aa8f405
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918725"
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

*número*<br/>
Número de elementos.

*size*<br/>
Longitud en bytes de cada elemento.

## <a name="return-value"></a>Valor devuelto

**calloc** devuelve un puntero al espacio asignado. Se garantiza que el espacio de almacenamiento al que apunta el valor devuelto esté alineado correctamente para el almacenamiento de todo tipo de objeto. Para obtener un puntero a un tipo distinto de **void**, use una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Observaciones

La función **calloc** asigna espacio de almacenamiento para una matriz de elementos *numéricos* , cada uno de los cuales tiene un *tamaño* de longitud de bytes. Cada elemento se inicializa en 0.

**calloc** establece **errno** en **ENOMEM** si se produce un error de asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

En la implementación de Microsoft, si el *número* o *el tamaño* es cero, **calloc** devuelve un puntero a un bloque asignado de tamaño distinto de cero. Un intento de leer o escribir a través del puntero devuelto conduce a un comportamiento indefinido.

**calloc** utiliza la función de [_set_new_mode](set-new-mode.md) de C++ para establecer el *nuevo modo de controlador*. El nuevo modo de controlador indica si, en caso de error, **calloc** es llamar a la rutina del nuevo controlador como se establece en [_set_new_handler](set-new-handler.md). De forma predeterminada, **calloc** no llama a la rutina del nuevo controlador en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **calloc** no pueda asignar memoria, llame a la rutina del nuevo controlador de la misma forma que el operador **New** cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a

```C
_set_new_mode(1);
```

temprano en el programa o vincular con *NEWMODE. OBJ* (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)).

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **calloc** se resuelve como [_calloc_dbg](calloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** está marcado `__declspec(noalias)` como `__declspec(restrict)`y, lo que significa que se garantiza que la función no modifica las variables globales y que el puntero devuelto no tiene alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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
[ningún](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
