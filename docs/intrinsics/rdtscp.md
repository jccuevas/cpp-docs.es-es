---
title: __rdtscp
ms.date: 09/02/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: 4dcabd6ed0f7fb3f422927815cbdc91f2b4b9d43
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221323"
---
# <a name="__rdtscp"></a>__rdtscp

**Específicos de Microsoft**

Genera la `rdtscp` instrucción, escribe `TSC_AUX[31:0`] en la memoria y devuelve el contador de marca de tiempo de 64`TSC)` bits (result.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 __rdtscp(
   unsigned int * AUX
);
```

### <a name="parameters"></a>Parámetros

*AUX*\
enuncia Puntero a una ubicación que contendrá el contenido del registro `TSC_AUX[31:0]`específico del equipo.

## <a name="return-value"></a>Valor devuelto

Recuento de pasos de entero de 64 bits sin signo.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__rdtscp`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El `__rdtscp` intrínseco genera la `rdtscp` instrucción. Para determinar la compatibilidad de hardware para esta instrucción, `__cpuid` llame a `InfoType=0x80000001` la función intrínseca con y `CPUInfo[3] (EDX)`Compruebe el bit 27 de. Este bit es 1 si se admite la instrucción y 0 en caso contrario.  Si ejecuta código que usa el intrínseco en hardware que no admite la `rdtscp` instrucción, los resultados son imprevisibles.

Esta instrucción espera hasta que se hayan ejecutado todas las instrucciones anteriores y todas las cargas anteriores estén visibles globalmente. Sin embargo, no es una instrucción de serialización. Para obtener más información, consulte los manuales de Intel y AMD.

El significado del valor de `TSC_AUX[31:0]` depende del sistema operativo.

## <a name="example"></a>Ejemplo

```cpp
#include <intrin.h>
#include <stdio.h>
int main()
{
    unsigned __int64 i;
    unsigned int ui;
    i = __rdtscp(&ui);
    printf_s("%I64d ticks\n", i);
    printf_s("TSC_AUX was %x\n", ui);
}
```

```Output
3363423610155519 ticks
TSC_AUX was 0
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__rdtsc](../intrinsics/rdtsc.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
