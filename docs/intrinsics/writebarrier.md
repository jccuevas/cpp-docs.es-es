---
title: _WriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _WriteBarrier
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
ms.openlocfilehash: a41f4c6c5cdd6b72e76a596622912e88fbd03f34
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219313"
---
# <a name="_writebarrier"></a>_WriteBarrier

**Específicos de Microsoft**

Limita las optimizaciones del compilador que pueden reordenar las operaciones de acceso a memoria en el punto de la llamada.

> [!CAUTION]
> Los objetos `_ReadBarrier`, `_WriteBarrier` y `_ReadWriteBarrier` intrínsecos del compilador y la macro `MemoryBarrier` están desusados y no deben utilizarse. Para la comunicación entre subprocesos, use mecanismos como [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) y [STD::\<Atomic T >](../standard-library/atomic.md), que se definen en la [ C++ biblioteca estándar](../standard-library/cpp-standard-library-reference.md). Para el acceso de hardware, utilice la opción de compilador [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) junto con la palabra clave [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Sintaxis

```C
void _WriteBarrier(void);
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_WriteBarrier`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El objeto `_WriteBarrier` intrínseco limita las optimizaciones del compilador que pueden quitar o reordenar las operaciones de acceso a memoria en el punto de la llamada.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[Palabras clave](../cpp/keywords-cpp.md)
