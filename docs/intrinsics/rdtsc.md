---
title: __rdtsc
ms.date: 09/02/2019
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 837b68ca6ac63587cd43a7e8828777221c677e3c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217151"
---
# <a name="__rdtsc"></a>__rdtsc

**Específicos de Microsoft**

Genera la `rdtsc` instrucción, que devuelve la marca de tiempo del procesador. La marca de tiempo del procesador registra el número de ciclos de reloj desde el último restablecimiento.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>Valor devuelto

Entero de 64 bits sin signo que representa un recuento de pasos.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__rdtsc`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como intrínseco.

La interpretación del valor de TSC en generaciones posteriores de hardware difiere de la de versiones anteriores de x64. Para obtener más información, consulte los manuales de hardware.

## <a name="example"></a>Ejemplo

```cpp
// rdtsc.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__rdtsc)

int main()
{
    unsigned __int64 i;
    i = __rdtsc();
    printf_s("%I64d ticks\n", i);
}
```

```Output
3363423610155519 ticks
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
