---
title: _aligned_offset_malloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _aligned_offset_malloc
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
- _aligned_offset_malloc
- aligned_offset_malloc
dev_langs:
- C++
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62ddae2faf8139b58e43f889c46771647b254b10
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="alignedoffsetmalloc"></a>_aligned_offset_malloc

Asigna memoria en un límite de alineación especificado.

## <a name="syntax"></a>Sintaxis

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Tamaño de la asignación de memoria solicitada.

*Alineación*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

## <a name="return-value"></a>Valor devuelto

Un puntero al bloque de memoria que se asignó o **NULL** si la operación produce un error.

## <a name="remarks"></a>Comentarios

**_aligned_offset_malloc** es útil en situaciones donde la alineación se necesita en un elemento anidado, por ejemplo, si se necesitara la alineación en una clase anidada.

**_aligned_offset_malloc** se basa en **malloc**; para obtener más información, consulte [malloc](malloc.md).

**_aligned_offset_malloc** está marcado como `__declspec(noalias)` y `__declspec(restrict)`, lo que significa que se garantiza que la función no se puede modificar las variables globales y que el puntero devuelto no es un alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

Esta función establece **errno** a **ENOMEM** si produce un error en la asignación de memoria o si el tamaño solicitado es mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_offset_malloc** valida sus parámetros. Si *alineación* no es una potencia de 2 o si *desplazamiento* es mayor o igual que *tamaño* y distinto de cero, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **NULL** y establece **errno** a **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h>|

## <a name="example"></a>Ejemplo

Para obtener más información, consulte [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Vea también

[Alineación de datos](../../c-runtime-library/data-alignment.md)<br/>
