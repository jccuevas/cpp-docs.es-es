---
title: _aligned_offset_recalloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_recalloc
- _o__aligned_offset_recalloc
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
- aligned_offset_recalloc
- _aligned_offset_recalloc
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
ms.openlocfilehash: 4c710712138d07191468cdc7ef02fc75e2f46dad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350550"
---
# <a name="_aligned_offset_recalloc"></a>_aligned_offset_recalloc

Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) e inicializa la memoria a 0.

## <a name="syntax"></a>Sintaxis

```C
void * _aligned_offset_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero de bloque de memoria actual.

*number*<br/>
Número de elementos.

*Tamaño*<br/>
Longitud en bytes de cada elemento.

*Alineación*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

## <a name="return-value"></a>Valor devuelto

**_aligned_offset_recalloc** devuelve un puntero void al bloque de memoria reasignado (y posiblemente movido). El valor devuelto es **NULL** si el tamaño es cero y el argumento de búfer no es **NULL**o si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.

**_aligned_offset_recalloc** está `__declspec(noalias)` `__declspec(restrict)`marcado y , lo que significa que se garantiza que la función no modifique las variables globales y que el puntero devuelto no tenga alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

## <a name="remarks"></a>Observaciones

Al igual que [_aligned_offset_malloc](aligned-offset-malloc.md), **_aligned_offset_recalloc** permite que una estructura se alinee en un desfase dentro de la estructura.

**_aligned_offset_recalloc** se basa en **malloc**. Para obtener más información sobre el uso de **_aligned_offset_malloc**, consulte [malloc](malloc.md). Si *memblock* es **NULL**, la función llama **a _aligned_offset_malloc** internamente.

Esta función establece **errno en** **ENOMEM** si la asignación de memoria ha fallado o si el tamaño solicitado *(tamaño*del*número* * ) fue mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_offset_recalloc** valida sus parámetros. Si *la alineación* no es una potencia de 2 o si *el desplazamiento* es mayor o igual que el tamaño solicitado y distinto de cero, esta función invoca el controlador de parámetros no válidos, como se describe en [Validación de](../../c-runtime-library/parameter-validation.md)parámetros . Si la ejecución puede continuar, esta función devuelve **NULL** y establece **errno** en **EINVAL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_offset_recalloc**|\<malloc.h>|

## <a name="see-also"></a>Consulte también

[Alineación de datos](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
