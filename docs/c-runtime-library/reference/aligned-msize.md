---
title: _aligned_msize | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_msize
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
- _aligned_msize
- aligned_msize
dev_langs:
- C++
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2375ec8f61a95ec018ea55cc1f891ad8049748c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393110"
---
# <a name="alignedmsize"></a>_aligned_msize

Devuelve el tamaño de un bloque de memoria asignado en el montón.

## <a name="syntax"></a>Sintaxis

```C
size_t _msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria.

*Alineación*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

## <a name="return-value"></a>Valor devuelto

Devuelve el tamaño (en bytes) de un entero sin signo.

## <a name="remarks"></a>Comentarios

El **_aligned_msize** función devuelve el tamaño, en bytes, del bloque de memoria asignada por una llamada a [_aligned_malloc](aligned-malloc.md) o [_aligned_realloc](aligned-realloc.md). El *alineación* y *desplazamiento* valores deben ser el mismo que los valores pasados a la función que asignó el bloque.

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas de tiempo de ejecución de C, **_aligned_msize** se resuelve como [_aligned_msize_dbg](aligned-msize-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

Esta función valida su parámetro. Si *memblock* es un puntero nulo o *alineación* no es una potencia de 2, **_msize** invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros ](../../c-runtime-library/parameter-validation.md). Si se controla el error, la función establece **errno** a **EINVAL** y devuelve -1.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
