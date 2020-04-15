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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 57972a48336d8dd362b5da7513c854703134921b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338119"
---
# <a name="_recalloc"></a>_recalloc

Una combinación de **realloc** y **calloc**. Reasigna una matriz en la memoria e inicializa sus elementos a 0.

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

*number*<br/>
Número de elementos.

*Tamaño*<br/>
Longitud en bytes de cada elemento.

## <a name="return-value"></a>Valor devuelto

**_recalloc** devuelve un puntero **void** al bloque de memoria reasignado (y posiblemente movido).

Si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado, el bloque original se deja sin cambios y se devuelve **NULL.**

Si el tamaño solicitado es cero, el bloque al que apunta *memblock* se libera; el valor devuelto es **NULL**y *memblock* se deja apuntando a un bloque liberado.

El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto de **void**, utilice una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Observaciones

La función **_recalloc** cambia el tamaño de un bloque de memoria asignado. El argumento *memblock* apunta al principio del bloque de memoria. Si *memblock* es **NULL**, **_recalloc** se comporta de la misma manera que [calloc](calloc.md) y asigna un nuevo bloque de bytes de*tamaño* de *número.* *  Cada elemento se inicializa en 0. Si *memblock* no es **NULL**, debe ser un puntero devuelto por una llamada anterior a **calloc**, [malloc](malloc.md)o [realloc](realloc.md).

Dado que el nuevo bloque puede estar en una nueva ubicación de memoria, no se garantiza que el puntero devuelto por **_recalloc** sea el puntero pasado a través del argumento *memblock.*

**_recalloc** establece **errno** **en ENOMEM** si se produce un error en la asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** llama a **realloc** para utilizar la función [de _set_new_mode](set-new-mode.md) C++ para establecer el nuevo modo de controlador. El nuevo modo de controlador indica si, en caso de error, **realloc** debe llamar a la nueva rutina de controlador según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **realloc** no llama a la nueva rutina de controlador al no asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **_recalloc** no pueda asignar memoria, **realloc** llame a la nueva rutina de controlador de la misma manera que lo hace el operador **new** cuando se produce un error por el mismo motivo. Para invalidar el valor predeterminado, llame a

```C
_set_new_mode(1);
```

temprano en el programa o vincúlelo con NEWMODE.OBJ.

Cuando la aplicación está vinculada con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **_recalloc** se resuelve [en _recalloc_dbg](recalloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** está `__declspec(noalias)` `__declspec(restrict)`marcado y , lo que significa que se garantiza que la función no modifique las variables globales y que el puntero devuelto no tenga alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> y \<malloc.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[Gratis](free.md)<br/>
[Opciones de vínculo](../../c-runtime-library/link-options.md)<br/>
