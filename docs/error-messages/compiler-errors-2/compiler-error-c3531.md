---
title: Error del compilador C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 0f6094daddf40b0899dc7f341f50a31daf7a999b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435456"
---
# <a name="compiler-error-c3531"></a>Error del compilador C3531

'símbolo': un símbolo cuyo tipo contiene 'auto' debe tener un inicializador

La variable especificada no tiene una expresión de inicializador.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Especifique una expresión de inicializador, como una asignación simple que usa la sintaxis de signo igual, al declarar la variable.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3531 porque las variables `x1`, `y1, y2, y3`, y `z2` no se ha inicializado.

```
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