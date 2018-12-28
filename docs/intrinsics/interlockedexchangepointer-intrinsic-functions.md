---
title: Funciones intrínsecas _InterlockedExchangePointer
ms.date: 12/17/2018
f1_keywords:
- _InterlockedExchangePointer_cpp
- _InterlockedExchangePointer_rel
- _InterlockedExchangePointer_nf
- _InterlockedExchangePointer_HLERelease
- _InterlockedExchangePointer_acq
- _InterlockedExchangePointer
- _InterlockedExchangePointer_acq_cpp
- _InterlockedExchangePointer_HLEAcquire
helpviewer_keywords:
- _InterlockedExchangePointer_rel intrinsic
- _InterlockedExchangePointer_HLERelease intrinsic
- _InterlockedExchangePointer intrinsic
- _InterlockedExchangePointer_nf intrinsic
- _InterlockedExchangePointer_acq intrinsic
- _InterlockedExchangePointer_HLEAcquire intrinsic
- InterlockedExchangePointer_acq intrinsic
- InterlockedExchangePointer intrinsic
ms.assetid: 0eaca0b0-d79e-406b-892d-b3b462c50bbb
ms.openlocfilehash: 021c754436d6abe877e6b7dd372ba235869d8975
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627498"
---
# <a name="interlockedexchangepointer-intrinsic-functions"></a>Funciones intrínsecas _InterlockedExchangePointer

**Específicos de Microsoft**

Realizar una operación de intercambio atómico, que copia la dirección que se pasa como segundo argumento al primero y devuelve la dirección original del primero.

## <a name="syntax"></a>Sintaxis

```
void * _InterlockedExchangePointer(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_acq(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_rel(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_nf(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_HLEAcquire(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_HLERelease(
   void * volatile * Target,
   void * Value
);
```

#### <a name="parameters"></a>Parámetros

*Target*<br/>
[in, out] Puntero al puntero al valor que se intercambian. La función establece el valor en `Value` y devuelve su valor anterior.

*Valor*<br/>
[in] Valor van a intercambiar con el valor señalado por `Target`.

## <a name="return-value"></a>Valor devuelto

La función devuelve el valor inicial al que apunta `Target`.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Header|
|---------------|------------------|------------|
|`_InterlockedExchangePointer`|x86, ARM, x64|\<INTRIN.h >|
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM|\<INTRIN.h >|
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|x64 con compatibilidad HLE|\<immintrin.h >|

En la arquitectura x86, `_InterlockedExchangePointer` es una macro que llama a `_InterlockedExchange`.

## <a name="remarks"></a>Comentarios

En un sistema de 64 bits, los parámetros son de 64 bits y deben estar alineados en límites de 64 bits; de lo contrario, se produce un error en la función. En un sistema de 32 bits, los parámetros son de 32 bits y deben estar alineados en límites de 32 bits. Para obtener más información, consulte [alinear](../cpp/align-cpp.md).

En plataformas ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` si necesita adquirir y liberar semántica, como al principio y al final de una sección crítica. Los intrínsecos con un sufijo `_nf` ("sin límite") no actúan como una barrera de memoria.

En las plataformas de Intel que admiten instrucciones de Elisión de bloqueo de Hardware (HLE), los intrínsecos con sufijos `_HLEAcquire` y `_HLERelease` incluyen una sugerencia para el procesador que puede acelerar el rendimiento mediante la eliminación de un paso de escritura de bloqueo en el hardware. Si se llama a estos intrínsecos en plataformas que no son compatibles con HLE, se omite la sugerencia.

Estas rutinas solo están disponibles como intrínsecos.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Conflictos con el compilador de x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)