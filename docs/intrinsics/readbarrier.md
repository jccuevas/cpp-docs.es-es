---
title: _ReadBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadBarrier
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
ms.openlocfilehash: 8bbcecf95daeef6ea2d40877d37e0eb6b7f3a0e8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217087"
---
# <a name="_readbarrier"></a>_ReadBarrier

**Específicos de Microsoft**

Limita las optimizaciones del compilador que pueden reordenar las operaciones de acceso a memoria en el punto de la llamada.

> [!CAUTION]
> Los objetos `_ReadBarrier`, `_WriteBarrier` y `_ReadWriteBarrier` intrínsecos del compilador y la macro `MemoryBarrier` están desusados y no deben utilizarse. Para la comunicación entre subprocesos, use mecanismos como [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) y [STD::\<Atomic T >](../standard-library/atomic.md) definidos en la [ C++ biblioteca estándar](../standard-library/cpp-standard-library-reference.md). Para el acceso de hardware, utilice la opción de compilador [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) junto con la palabra clave [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Sintaxis

```C
void _ReadBarrier(void);
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_ReadBarrier`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El objeto `_ReadBarrier` intrínseco limita las optimizaciones del compilador que pueden quitar o reordenar las operaciones de acceso a memoria en el punto de la llamada.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[Palabras clave](../cpp/keywords-cpp.md)
