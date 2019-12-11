---
title: Advertencia del compilador (nivel 3) C4738
ms.date: 11/04/2016
f1_keywords:
- C4738
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
ms.openlocfilehash: c1989518c3965f8faa54a05b2925d0e37455625e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991705"
---
# <a name="compiler-warning-level-3-c4738"></a>Advertencia del compilador (nivel 3) C4738

almacenando el resultado flotante de 32 bits en memoria; posible pérdida de rendimiento

C4738 advierte de que es posible que sea necesario redondear el resultado de una asignación, conversión, argumento pasado u otra operación o que la operación se haya quedado sin registros y necesite usar memoria (derrame). Esto puede dar lugar a una pérdida de rendimiento.

Para resolver esta advertencia y evitar el redondeo, compile con [/FP: Fast](../../build/reference/fp-specify-floating-point-behavior.md) o use `double` en lugar de `float`.

Para resolver esta advertencia y evitar quedarse sin registros, cambie el orden de los cálculos y modifique el uso de la inserción.

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4738:

```cpp
// C4738.cpp
// compile with: /c /fp:precise /O2 /W3
// processor: x86
#include <stdio.h>

#pragma warning(default : 4738)

float func(float f)
{
    return f;
}

int main()
{
    extern float f, f1, f2;
    double d = 0.0;

    f1 = func(d);
    f2 = (float) d;
    f = f1 + f2;   // C4738
    printf_s("%f\n", f);
}
```
