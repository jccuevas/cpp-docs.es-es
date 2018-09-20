---
title: _InterlockedCompareExchange128 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
dev_langs:
- C++
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dfcdb0c7c2f6315ea7560c236c36d1a1ba449b9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389283"
---
# <a name="interlockedcompareexchange128"></a>_InterlockedCompareExchange128

**Específicos de Microsoft**

Realiza una 128 bits comparación e intercambio entrelazados.

## <a name="syntax"></a>Sintaxis

```
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

#### <a name="parameters"></a>Parámetros

*Destino*<br/>
[in, out] Puntero al destino, que es una matriz de dos enteros de 64 bits se considera como un campo de 128 bits. Los datos de destino deben ser 16 bytes alineados para evitar un error de protección general.

*ExchangeHigh*<br/>
[in] Un entero de 64 bits que se puede intercambiar con la parte alta del destino.

*ExchangeLow*<br/>
[in] Un entero de 64 bits que se puede intercambiar con la parte baja del destino.

*ComparandResult*<br/>
[in, out] Puntero a una matriz de dos enteros de 64 bits (se considera como un campo de 128 bits) que se compara con el destino.  En la salida, se sobrescribe con el valor original del destino.

## <a name="return-value"></a>Valor devuelto

1 si el elemento de comparación de 128 bits es igual al valor original del destino. `ExchangeHigh` y `ExchangeLow` sobrescribir el destino de 128 bits.

0 si el elemento de comparación no es igual al valor original del destino. No se ha modificado el valor de destino y el valor del elemento de la comparación se sobrescribe con el valor de destino.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta función intrínseca genera el `cmpxchg16b` instrucción (con el `lock` prefijo) para realizar una comparación bloqueada de 128 bits y exchange. Las primeras versiones de hardware AMD de 64 bits no admiten esta instrucción. Para comprobar la compatibilidad de hardware para el `cmpxchg16b` instrucción, llamada la `__cpuid` intrínseca con `InfoType=0x00000001 (standard function 1)`. Bit 13 de `CPUInfo[2]` (ECX) es 1 si se admite la instrucción.

> [!NOTE]
>  El valor de `ComparandResult` siempre se sobrescribe. Después de la `lock` instrucción, esta función intrínseca copia inmediatamente el valor inicial de `Destination` a `ComparandResult`. Por este motivo, `ComparandResult` y `Destination` debe apuntar a ubicaciones de memoria independientes para evitar un comportamiento inesperado.

Aunque puede usar `_InterlockedCompareExchange128` para la sincronización de subprocesos de bajo nivel, no es necesario sincronizar más de 128 bits, si puede usar funciones de sincronización más pequeñas (por ejemplo, el otro `_InterlockedCompareExchange` intrínsecos) en su lugar. Use `_InterlockedCompareExchange128` si desea acceso atómico a un valor de 128 bits en memoria.

Si ejecuta el código que usa esta función intrínseca en hardware que no es compatible con la `cmpxchg16b` instrucciones, los resultados son impredecibles.

Esta rutina solo está disponible como intrínseco.

## <a name="example"></a>Ejemplo

Este ejemplo se utiliza `_InterlockedCompareExchange128` para reemplazar la palabra alta de una matriz de dos enteros de 64 bits con la suma de sus palabras altos y bajos y para incrementar los bytes menos significativos. El acceso a la matriz BigInt.Int es atómico, pero en este ejemplo utiliza un único subproceso y omite el bloqueo por motivos de simplicidad.

```
// cmpxchg16b.c
// processor: x64
// compile with: /EHsc /O2
#include <stdio.h>
#include <intrin.h>

typedef struct _LARGE_INTEGER_128 {
    __int64 Int[2];
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;

volatile LARGE_INTEGER_128 BigInt;

// This AtomicOp() function atomically performs:
//   BigInt.Int[1] += BigInt.Int[0]
//   BigInt.Int[0] += 1
void AtomicOp ()
{
    LARGE_INTEGER_128 Comparand;
    Comparand.Int[0] = BigInt.Int[0];
    Comparand.Int[1] = BigInt.Int[1];
    do {
        ; // nothing
    } while (_InterlockedCompareExchange128(BigInt.Int,
                                            Comparand.Int[0] + Comparand.Int[1],
                                            Comparand.Int[0] + 1,
                                            Comparand.Int) == 0);
}

// In a real application, several threads contend for the value
// of BigInt.
// Here we focus on the compare and exchange for simplicity.
int main(void)
{
   BigInt.Int[1] = 23;
   BigInt.Int[0] = 11;
   AtomicOp();
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",
      BigInt.Int[1],BigInt.Int[0]);
}
```

```Output
BigInt.Int[1] = 34, BigInt.Int[0] = 12
```

**FIN de Específicos de Microsoft**

Copyright 2007 por Advanced Micro Devices, Inc. Todos los derechos reservados. Reprodujo con permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Funciones intrínsecas de _InterlockedCompareExchange](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)<br/>
[Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)