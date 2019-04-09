---
title: Error del compilador C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: acbe89b5183d0991fb8d4a571a9595d6f6bafc6c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026128"
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