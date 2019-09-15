---
title: _aligned_recalloc
ms.date: 11/04/2016
api_name:
- _aligned_recalloc
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
- aligned_recalloc
- _aligned_recalloc
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
ms.openlocfilehash: ef25769a04b27b02ccda16e86451a068ab0a0b84
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943777"
---
# <a name="_aligned_recalloc"></a>_aligned_recalloc

Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) e inicializa la memoria a 0.

## <a name="syntax"></a>Sintaxis

```C
void * _aligned_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero de bloque de memoria actual.

*number*<br/>
Número de elementos.

*size*<br/>
Tamaño en bytes de cada elemento.

*alignment*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

## <a name="return-value"></a>Valor devuelto

**_aligned_recalloc** devuelve un puntero void al bloque de memoria reasignado (y que posiblemente se ha cambiado). El valor devuelto es **null** si el tamaño es cero y el argumento de búfer no es **null**, o si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.

Es un error reasignar memoria y cambiar la alineación del bloque.

## <a name="remarks"></a>Comentarios

**_aligned_recalloc** se basa en **malloc**. Para obtener más información sobre el uso de **_aligned_offset_malloc**, consulte [malloc](malloc.md).

Esta función establece **errno** en **ENOMEM** si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_recalloc** valida sus parámetros. Si la *alineación* no es una potencia de 2, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **null** y establece **errno** en **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_recalloc**|\<malloc.h>|

## <a name="see-also"></a>Vea también

[Alineación de datos](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
