---
title: Funciones intrínsecas de _InterlockedCompareExchange128
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
- _InterlockedCompareExchange128_acq
- _InterlockedCompareExchange128_nf
- _InterlockedCompareExchange128_np
- _InterlockedCompareExchange128_rel
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: 6f6b36b238945f7d46e9817cdc85977d666e1e9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077627"
---
# <a name="_interlockedcompareexchange128-intrinsic-functions"></a>Funciones intrínsecas de _InterlockedCompareExchange128

**Específicos de Microsoft**

Realiza una comparación e intercambio interbloqueados de 128 bits.

## <a name="syntax"></a>Sintaxis

```C
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_acq(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_nf(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_np(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_rel(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

### <a name="parameters"></a>Parámetros

\ de *destino*
[in, out] Puntero al destino, que es una matriz de enteros de 2 64 bits considerados como un campo de 128 bits. Los datos de destino deben estar alineados en 16 bytes para evitar un error de protección general.

\ *ExchangeHigh*
de Entero de 64 bits que se puede intercambiar con la parte alta del destino.

\ *ExchangeLow*
de Entero de 64 bits que se puede intercambiar con la parte baja del destino.

\ *ComparandResult*
[in, out] Puntero a una matriz de enteros de 2 64 bits (considerados como un campo de 128 bits) que se va a comparar con el destino.  En la salida, esta matriz se sobrescribe con el valor original del destino.

## <a name="return-value"></a>Valor devuelto

1 si el valor de comparand de 128 bits es igual al valor original del destino. `ExchangeHigh` y `ExchangeLow` sobrescribir el destino de 128 bits.

0 si el valor de comparand no es igual al valor original del destino. El valor del destino no se modifica y el valor de el valor de comparand se sobrescribe con el valor del destino.

## <a name="requirements"></a>Requisitos

|Intrinsic|Architecture|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64, ARM64|
|`_InterlockedCompareExchange128_acq`, `_InterlockedCompareExchange128_nf`, `_InterlockedCompareExchange128_rel`|ARM64|
|`_InterlockedCompareExchange128_np`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Observaciones

El `_InterlockedCompareExchange128` intrínseco genera la instrucción `cmpxchg16b` (con el prefijo `lock`) para realizar una comparación y un intercambio bloqueados de 128 bits. Las primeras versiones del hardware AMD 64-bit no admiten esta instrucción. Para comprobar la compatibilidad de hardware con la instrucción `cmpxchg16b`, llame al `__cpuid` intrínseco con `InfoType=0x00000001 (standard function 1)`. El bit 13 de `CPUInfo[2]` (ECX) es 1 si se admite la instrucción.

> [!NOTE]
> Siempre se sobrescribe el valor de `ComparandResult`. Después de la instrucción `lock`, este intrínseco copia inmediatamente el valor inicial de `Destination` en `ComparandResult`. Por esta razón, `ComparandResult` y `Destination` deben apuntar a ubicaciones de memoria independientes para evitar un comportamiento inesperado.

Aunque puede usar `_InterlockedCompareExchange128` para la sincronización de subprocesos de bajo nivel, no es necesario sincronizar más de 128 bits si se pueden usar funciones de sincronización más pequeñas (como las demás `_InterlockedCompareExchange` intrínsecos) en su lugar. Use `_InterlockedCompareExchange128` si desea tener acceso atómico a un valor de 128 bits en memoria.

Si ejecuta código que usa el intrínseco en hardware que no admite la instrucción `cmpxchg16b`, los resultados son imprevisibles.

En plataformas ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` para adquirir y liberar semántica, como al principio y al final de una sección crítica. Los intrínsecos ARM con un sufijo `_nf` ("sin barrera") no actúan como una barrera de memoria.

Los intrínsecos con un sufijo `_np` ("sin captura previa") impiden que el compilador inserte una posible operación de captura previa.

Esta rutina solo está disponible como intrínseco.

## <a name="example"></a>Ejemplo

En este ejemplo se usa `_InterlockedCompareExchange128` para reemplazar la palabra alta de una matriz de enteros de 2 64 bits por la suma de sus palabras altas y bajas y para incrementar la palabra baja. El acceso a la matriz de `BigInt.Int` es atómico, pero en este ejemplo se usa un único subproceso y se omite el bloqueo por simplicidad.

```cpp
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

## <a name="see-also"></a>Consulte también

[Intrínsecos del Compilador](../intrinsics/compiler-intrinsics.md)\
[_InterlockedCompareExchange funciones intrínsecas](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)\
[Conflictos con el compilador de x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
