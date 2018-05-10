---
title: fp_contract | Documentos de Microsoft
ms.custom: ''
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 514b4708129d625ea7880e4c61be22c4b1ac2db5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="fpcontract"></a>fp_contract

Determina si realiza contracción de punto flotante. Contracción de punto flotante es una instrucción como FMA (fundidos multiplicar-adición) que combina dos operaciones de punto flotante independientes en una sola instrucción. Uso de estas instrucciones puede afectar a precisión de punto flotante, ya que en lugar de redondeo después de cada operación, el procesador puede redondear solo una vez después de ambas operaciones.

## <a name="syntax"></a>Sintaxis

> **#pragma fp_contract (** { **en** | **desactivar** } **)**  

## <a name="remarks"></a>Comentarios  

De forma predeterminada, **fp_contract** es **en**. Esto indica al compilador que utilice instrucciones de contracción de punto flotante siempre que sea posible. Establecer **fp_contract** a **desactivar** para conservar las instrucciones individuales de coma flotante.

Para obtener más información sobre el comportamiento de punto flotante, consulte [/fp (Especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md).

Las directivas pragma de punto flotante incluyen:

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Ejemplo

El código generado a partir de este ejemplo no utiliza una instrucción multiplicar-fusionada incluso cuando esté disponible en el procesador de destino. Si marca como comentario `#pragma fp_contract (off)`, el código generado puede utilizar una instrucción multiplicar-fusionada si está disponible.  
  
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
