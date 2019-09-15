---
title: calloc
ms.date: 11/04/2016
api_name:
- calloc
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
ms.openlocfilehash: ba498b35106f9ff1636bb1bc0764088a434b5b01
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939336"
---
# <a name="calloc"></a>calloc

Asigna una matriz en la memoria con elementos que se inicializan en 0.

## <a name="syntax"></a>Sintaxis

```C
void *calloc(
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*number*<br/>
Número de elementos.

*size*<br/>
Longitud en bytes de cada elemento.

## <a name="return-value"></a>Valor devuelto

**calloc** devuelve un puntero al espacio asignado. Se garantiza que el espacio de almacenamiento al que apunta el valor devuelto esté alineado correctamente para el almacenamiento de todo tipo de objeto. Para obtener un puntero a un tipo distinto de **void**, use una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Comentarios

La función **calloc** asigna espacio de almacenamiento para una matriz de elementos *numéricos* , cada uno de los cuales tiene un *tamaño* de longitud de bytes. Cada elemento se inicializa en 0.

**calloc** establece **errno** en **ENOMEM** si se produce un error en una asignación de memoria o si la cantidad de memoria solicitada supera el valor de **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**calloc** llama a **malloc** para usar C++ la función [_set_new_mode](set-new-mode.md) para establecer el nuevo modo de controlador. El nuevo modo de controlador indica si, en caso de error, **malloc** es llamar a la rutina del nuevo controlador tal y como se establece en [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del nuevo controlador en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **calloc** no pueda asignar memoria, **malloc** llame a la rutina del nuevo controlador de la misma manera que el operador **New** cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a

```C
_set_new_mode(1);
```

temprano en el programa o vincúlelo con NEWMODE.OBJ (consulte [Opciones de vínculo](../../c-runtime-library/link-options.md)).

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **calloc** se resuelve como [_calloc_dbg](calloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** está marcado `__declspec(noalias)` como `__declspec(restrict)`y, lo que significa que se garantiza que la función no modifica las variables globales y que el puntero devuelto no tiene alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**calloc**|\<stdlib.h> y \<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
