---
title: Error del compilador C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: 0d6c1467575e7fae7d5e4862f36e733a68210f8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743099"
---
# <a name="compiler-error-c3483"></a>Error del compilador C3483

'var' ya forma parte de la lista de capturas lambda

Pasó la misma variable a la lista de capturas de una expresión lambda más de una vez.

### <a name="to-correct-this-error"></a>Para corregir este error

- Quite todas las instancias adicionales de la variable de la lista de capturas.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3483 porque la variable `n` aparece más de una vez en la lista de capturas de la expresión lambda:

```cpp
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
