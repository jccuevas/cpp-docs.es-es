---
title: _WriteBarrier
ms.date: 11/04/2016
f1_keywords:
- _WriteBarrier
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
ms.openlocfilehash: b1b5ba2d70a8fc64eb47b3c6f3ff157214dcb94d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653029"
---
# <a name="writebarrier"></a>_WriteBarrier

**Específicos de Microsoft**

Limita las optimizaciones del compilador que pueden reordenar las operaciones de acceso a memoria en el punto de la llamada.

> [!CAUTION]
>  Los objetos `_ReadBarrier`, las funciones intrínsecas del compilador `_WriteBarrier` y `_ReadWriteBarrier` y la macro `MemoryBarrier` están en desuso y no se deben usar. Para la comunicación entre subprocesos, use mecanismos como [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) y [std:: atomic\<T >](../standard-library/atomic.md), que se definen en el [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md). Para tener acceso de hardware, utilice el [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) junto con la opción del compilador la [volátil](../cpp/volatile-cpp.md) palabra clave.

## <a name="syntax"></a>Sintaxis

```
void _WriteBarrier(void);
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_WriteBarrier`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

El objeto `_WriteBarrier` intrínseco limita las optimizaciones del compilador que pueden quitar o reordenar las operaciones de acceso a memoria en el punto de la llamada.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)