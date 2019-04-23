---
title: _ReadWriteBarrier
ms.date: 11/04/2016
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: 9da26b685be90bd349d6bfe56c4ad980541d09c0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026758"
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier

**Específicos de Microsoft**

Limita las optimizaciones del compilador que pueden reordenar las operaciones de acceso a memoria en el punto de la llamada.

> [!CAUTION]
>  Los objetos `_ReadBarrier`, `_WriteBarrier` y `_ReadWriteBarrier` intrínsecos del compilador y la macro `MemoryBarrier` están desusados y no deben utilizarse. Para la comunicación entre subprocesos, use mecanismos como [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) y [std:: atomic\<T >](../standard-library/atomic.md), que se definen en el [ C++ debibliotecaestándar](../standard-library/cpp-standard-library-reference.md). Para tener acceso de hardware, utilice el [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) junto con la opción del compilador la [volátil](../cpp/volatile-cpp.md) palabra clave.

## <a name="syntax"></a>Sintaxis

```
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_ReadWriteBarrier`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

El objeto `_ReadWriteBarrier` intrínseco limita las optimizaciones del compilador que pueden quitar o reordenar las operaciones de acceso a memoria en el punto de la llamada.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_WriteBarrier](../intrinsics/writebarrier.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)