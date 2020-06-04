---
title: _recalloc
ms.date: 4/2/2020
api_name:
- _recalloc
- _o__recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 342228635e69d49e0b51196aef03a296c1f0e652
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917867"
---
# <a name="_recalloc"></a>_recalloc

Combinación de **realloc** y **calloc**. Reasigna una matriz en la memoria e inicializa sus elementos a 0.

## <a name="syntax"></a>Sintaxis

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria asignado previamente.

*número*<br/>
Número de elementos.

*size*<br/>
Longitud en bytes de cada elemento.

## <a name="return-value"></a>Valor devuelto

**_recalloc** devuelve un puntero **void** al bloque de memoria reasignado (y, posiblemente, al que se ha cambiado).

Si no hay suficiente memoria disponible para expandir el bloque hasta el tamaño especificado, el bloque original permanece inalterado y se devuelve **null** .

Si el tamaño solicitado es cero, se libera el bloque señalado por *memblock* ; el valor devuelto es **null**y *memblock* está apuntando a un bloque liberado.

El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto de **void**, use una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Observaciones

La función **_recalloc** cambia el tamaño de un bloque de memoria asignado. El argumento *memblock* apunta al principio del bloque de memoria. Si *memblock* es **null**, **_recalloc** se comporta del mismo modo que [calloc](calloc.md) y asigna un nuevo bloque de bytes de *number* * *tamaño* numérico. Cada elemento se inicializa en 0. Si *memblock* no es **null**, debe ser un puntero devuelto por una llamada anterior a **calloc**, [malloc](malloc.md)o [realloc](realloc.md).

Dado que el nuevo bloque puede estar en una nueva ubicación de memoria, no se garantiza que el puntero devuelto por **_recalloc** sea el puntero que se pasa a través del argumento *memblock* .

**_recalloc** establece **errno** en **ENOMEM** si se produce un error en la asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** llama a **realloc** para usar la función de [_set_new_mode](set-new-mode.md) de C++ con el fin de establecer el nuevo modo de controlador. El nuevo modo de controlador indica si, en caso de error, **realloc** es llamar a la rutina del nuevo controlador como se establece en [_set_new_handler](set-new-handler.md). De forma predeterminada, **realloc** no llama a la rutina del nuevo controlador en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **_recalloc** no pueda asignar memoria, **realloc** llame a la rutina del nuevo controlador de la misma manera que el operador **New** cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a

```C
_set_new_mode(1);
```

temprano en el programa o vincúlelo con NEWMODE.OBJ.

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **_recalloc** se resuelve en [_recalloc_dbg](recalloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** está marcado `__declspec(noalias)` como `__declspec(restrict)`y, lo que significa que se garantiza que la función no modifica las variables globales y que el puntero devuelto no tiene alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> y \<malloc.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[ningún](free.md)<br/>
[Opciones de vínculo](../../c-runtime-library/link-options.md)<br/>
