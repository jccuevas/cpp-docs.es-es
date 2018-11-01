---
title: Error del compilador C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: c958eee234d25b008eb8cb03f40b45b8aaba81a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573464"
---
# <a name="compiler-error-c3483"></a>Error del compilador C3483

'var' ya forma parte de la lista de capturas lambda

Pasó la misma variable a la lista de capturas de una expresión lambda más de una vez.

### <a name="to-correct-this-error"></a>Para corregir este error

- Quite todas las instancias adicionales de la variable de la lista de capturas.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3483 porque la variable `n` aparece más de una vez en la lista de capturas de la expresión lambda:

```
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)