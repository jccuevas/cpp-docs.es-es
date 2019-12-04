---
title: Error del compilador C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 7da9da2daedc79db619f82848dc864d1cb7bd1f1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750096"
---
# <a name="compiler-error-c3531"></a>Error del compilador C3531

' Symbol ': un símbolo cuyo tipo contiene ' auto ' debe tener un inicializador

La variable especificada no tiene una expresión de inicializador.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Especifique una expresión de inicializador, como una asignación simple que use la sintaxis de signo igual, al declarar la variable.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3531 porque las variables `x1`, `y1, y2, y3`y `z2` no se inicializan.

```cpp
// C3531.cpp
// Compile with /Zc:auto
int main()
{
   auto x1;                  // C3531
   auto y1, y2, y3;          // C3531
   auto z1 = 1, z2, z3 = -1; // C3531
   return 0;
}
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)
