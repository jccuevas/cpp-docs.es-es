---
title: fp_contract
ms.date: 03/12/2018
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
ms.openlocfilehash: 14c3ac60d4fc0f45fcf0ece6c3f73153e5de4271
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476510"
---
# <a name="fpcontract"></a>fp_contract

Determina si la contracción de punto flotante tiene lugar. Contracción de punto flotante es una instrucción como FMA (fundidos-multiplicar-sumar) que combina dos operaciones de punto flotante independiente en una sola instrucción. El uso de estas instrucciones puede afectar a precisión de punto flotante, ya que en lugar de después de cada operación de redondeo, el procesador puede redondear solo una vez después de ambas operaciones.

## <a name="syntax"></a>Sintaxis

> **#pragma fp_contract (** { **en** | **desactivar** } **)**

## <a name="remarks"></a>Comentarios

De forma predeterminada, **fp_contract** es **en**. Esto indica al compilador que use instrucciones de contracción de punto flotante siempre que sea posible. Establecer **fp_contract** a **desactivar** para conservar las instrucciones individuales de punto flotante.

Para obtener más información sobre el comportamiento de punto flotante, vea [/fp (Especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md).

Las directivas pragma de punto flotante incluyen:

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Ejemplo

El código generado a partir de este ejemplo no utiliza una instrucción-fusionada incluso cuando esté disponible en el procesador de destino. Si marque como comentario `#pragma fp_contract (off)`, el código generado puede utilizar una instrucción-fusionada si está disponible.

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

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
