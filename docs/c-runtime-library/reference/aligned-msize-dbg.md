---
title: _aligned_msize_dbg
ms.date: 11/04/2016
api_name:
- _aligned_msize_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_msize_dbg
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
ms.openlocfilehash: f2a0ceab906dccacb2e1c78a8789d524b608a4ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939860"
---
# <a name="_aligned_msize_dbg"></a>_aligned_msize_dbg

Devuelve el tamaño de un bloque de memoria asignado en el montón (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
size_t _aligned_msize_dbg(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria.

*alignment*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

## <a name="return-value"></a>Valor devuelto

Devuelve el tamaño (en bytes) de un entero sin signo.

## <a name="remarks"></a>Comentarios

Los valores de *alineación* y *desplazamiento* deben ser los mismos que los valores pasados a la función que asignó el bloque.

**_aligned_msize_dbg** es una versión de depuración de la función [_aligned_msize](aligned-msize.md) . Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , cada llamada a **_aligned_msize_dbg** se reduce a una llamada a **_aligned_msize**. Tanto **_aligned_msize** como **_aligned_msize_dbg** calculan el tamaño de un bloque de memoria en el montón base, pero **_aligned_msize_dbg** agrega una característica de depuración: Incluye los búferes situados a cada lado de la parte del usuario del bloque de memoria en el tamaño devuelto.

Esta función valida su parámetro. Si *memblock* es un puntero nulo o la *alineación* no es una potencia de 2, **_msize** invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si se controla el error, la función establece **errno** en **EINVAL** y devuelve-1.

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_msize_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
