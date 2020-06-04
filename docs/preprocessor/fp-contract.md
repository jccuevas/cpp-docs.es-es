---
title: fp_contract (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
ms.openlocfilehash: 833d8e7f4b8c9da18901610e52afed619468c5c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218567"
---
# <a name="fp_contract-pragma"></a>fp_contract (Pragma)

Determina si tiene lugar la contracción de punto flotante. Una contracción de punto flotante es una instrucción como FMA (fusionado por comas-sumar) que combina dos operaciones de punto flotante independientes en una única instrucción. El uso de estas instrucciones puede afectar a la precisión de punto flotante, porque en lugar de redondear después de cada operación, el procesador puede redondear una sola vez después de ambas operaciones.

## <a name="syntax"></a>Sintaxis

> **#pragma fp_contract (** { **on** | **OFF** } **)**

## <a name="remarks"></a>Comentarios

De forma predeterminada, **fp_contract** está **activado**. Esto indica al compilador que utilice las instrucciones de contratación de punto flotante siempre que sea posible. Establezca **fp_contract** en **OFF** para conservar las instrucciones de punto flotante individuales.

Para obtener más información sobre el comportamiento de punto flotante, consulte [/FP (especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md).

Las directivas pragma de punto flotante incluyen:

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Ejemplo

El código generado a partir de este ejemplo no usa una instrucción fusionada-Multiply-Add aunque esté disponible en el procesador de destino. Si se marca `#pragma fp_contract (off)`como comentario, el código generado puede utilizar una instrucción fusionada-multiplicate-Add si está disponible.

```cpp
// pragma_directive_fp_contract.cpp
// on x86 and x64 compile with: /O2 /fp:fast /arch:AVX2
// other platforms compile with: /O2

#include <stdio.h>

// remove the following line to enable FP contractions
#pragma fp_contract (off)

int main() {
   double z, b, t;

   for (int i = 0; i < 10; i++) {
      b = i * 5.5;
      t = i * 56.025;

      z = t * i + b;
      printf("out = %.15e\n", z);
   }
}
```

```Output
out = 0.000000000000000e+00
out = 6.152500000000000e+01
out = 2.351000000000000e+02
out = 5.207249999999999e+02
out = 9.184000000000000e+02
out = 1.428125000000000e+03
out = 2.049900000000000e+03
out = 2.783725000000000e+03
out = 3.629600000000000e+03
out = 4.587525000000000e+03
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
