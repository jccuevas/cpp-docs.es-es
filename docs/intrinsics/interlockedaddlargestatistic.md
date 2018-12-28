---
title: _InterlockedAddLargeStatistic
ms.date: 11/04/2016
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: 88ada0a906b777ab8ac676ddfe0a5166e906999d
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627477"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Específicos de Microsoft**

Realiza una suma entrelazada en el que el primer operando es un valor de 64 bits.

## <a name="syntax"></a>Sintaxis

```
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

#### <a name="parameters"></a>Parámetros

*Sumando*<br/>
[in, out] Un puntero al primer operando a la operación de adición. El valor al que señala se reemplaza por el resultado de la suma.

*Valor*<br/>
[in] El segundo operando; valor que se va a agregar para el primer operando.

## <a name="return-value"></a>Valor devuelto

El valor del segundo operando.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta función intrínseca no es atómica porque se implementa como dos diferentes instrucciones bloqueadas. Una lectura atómica de 64 bits que se produce en otro subproceso durante la ejecución de este intrínseco podría dar lugar a un valor no es coherente que se va a leer.

Esta función se comporta como una barrera de lectura y escritura. Para obtener más información, consulte [_ReadWriteBarrier](../intrinsics/readwritebarrier.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Conflictos con el compilador de x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)