---
title: _aligned_recalloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_recalloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- aligned_recalloc
- _aligned_recalloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2792cff3c401d7710f3844bfe65640e194189586
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="alignedrecalloc"></a>_aligned_recalloc

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

*Número*<br/>
Número de elementos.

*size*<br/>
Tamaño en bytes de cada elemento.

*Alineación*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

## <a name="return-value"></a>Valor devuelto

**_aligned_recalloc** devuelve un puntero void al bloque de memoria reasignado (y, probablemente, trasladado). El valor devuelto es **NULL** si el tamaño es cero y el argumento de búfer no es **NULL**, o si no hay memoria suficiente para expandir el bloque al tamaño especificado. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.

Es un error reasignar memoria y cambiar la alineación del bloque.

## <a name="remarks"></a>Comentarios

**_aligned_recalloc** se basa en **malloc**. Para obtener más información sobre el uso de **_aligned_offset_malloc**, consulte [malloc](malloc.md).

Esta función establece **errno** a **ENOMEM** si produce un error en la asignación de memoria o si el tamaño solicitado es mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_recalloc** valida sus parámetros. Si *alineación* no es una potencia de 2, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **NULL** y establece **errno** a **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_recalloc**|\<malloc.h>|

## <a name="see-also"></a>Vea también

[Alineación de datos](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
