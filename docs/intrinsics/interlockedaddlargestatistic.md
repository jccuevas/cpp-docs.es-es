---
title: _InterlockedAddLargeStatistic
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: de8c5b7dfd2462dddcb98324ebacc44c8148d85e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222088"
---
# <a name="_interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Específicos de Microsoft**

Realiza una adición entrelazada en la que el primer operando es un valor de 64 bits.

## <a name="syntax"></a>Sintaxis

```C
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

### <a name="parameters"></a>Parámetros

*Addend*\
[in, out] Puntero al primer operando de la operación de adición. El valor al que apunta se reemplaza por el resultado de la suma.

*Valor*\
de Segundo operando; valor que se va a agregar al primer operando.

## <a name="return-value"></a>Valor devuelto

Valor del segundo operando.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El `_InterlockedAddLargeStatistic` intrínseco no es atómico, ya que se implementa como dos instrucciones bloqueadas independientes. Una lectura atómica de 64 bits que se produce en otro subproceso durante la ejecución de la función intrínseca podría producir una lectura de un valor incoherente.

`_InterlockedAddLargeStatistic`se comporta como una barrera de lectura y escritura. Para obtener más información, vea [_ReadWriteBarrier](../intrinsics/readwritebarrier.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[Conflictos con el compilador de x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
