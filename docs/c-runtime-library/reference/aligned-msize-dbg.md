---
title: _aligned_msize_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_msize_dbg
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
apitype: DLLExport
f1_keywords:
- _aligned_msize_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c16fd1292f78c8c3f6b3133050e27046fb003343
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392879"
---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg

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

*Alineación*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

## <a name="return-value"></a>Valor devuelto

Devuelve el tamaño (en bytes) de un entero sin signo.

## <a name="remarks"></a>Comentarios

El *alineación* y *desplazamiento* valores deben ser el mismo que los valores pasados a la función que asignó el bloque.

**_aligned_msize_dbg** es una versión de depuración de la [_aligned_msize](aligned-msize.md) (función). Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_aligned_msize_dbg** se reduce a una llamada a **_aligned_msize**. Ambos **_aligned_msize** y **_aligned_msize_dbg** calcular el tamaño de un bloque de memoria del montón base, pero **_aligned_msize_dbg** agrega una característica de depuración: incluye bloquear los búferes situados a cada lado de la parte del usuario de la memoria en el tamaño devuelto.

Esta función valida su parámetro. Si *memblock* es un puntero nulo o *alineación* no es una potencia de 2, **_msize** invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros ](../../c-runtime-library/parameter-validation.md). Si se controla el error, la función establece **errno** a **EINVAL** y devuelve -1.

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
