---
title: __rdtsc
ms.date: 11/04/2016
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 6f30be3340ae1be237bb2f8a008a8cb60c7351f0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036843"
---
# <a name="rdtsc"></a>__rdtsc

**Específicos de Microsoft**

Genera el `rdtsc` instrucción, que devuelve la marca de tiempo de procesador. La marca de tiempo de procesador registra el número de ciclos de reloj desde el último restablecimiento.

## <a name="syntax"></a>Sintaxis

```
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>Valor devuelto

Un entero de 64 bits sin signo que representa un recuento de pasos.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__rdtsc`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como intrínseco.

La interpretación del valor TSC en esta generación de hardware difiere en las versiones anteriores de x64. Consulte los manuales de hardware para obtener más información.

## <a name="example"></a>Ejemplo

```
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

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)