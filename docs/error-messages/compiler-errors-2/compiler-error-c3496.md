---
title: Error del compilador C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: c0075bf0e3749966a5e5b9fcd775b5d73171bf17
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599425"
---
# <a name="compiler-error-c3496"></a>Error del compilador C3496

'this' siempre se captura por valor: se ha omitido '&'

No se puede capturar el `this` puntero por referencia.

### <a name="to-correct-this-error"></a>Para corregir este error

- Capture el puntero `this` por valor.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3496 porque una referencia al puntero `this` aparece en la lista de captura de una expresión lambda:

```
// C3496.cpp
// compile with: /c

class C
{
   void f()
   {
      [&this] {}(); // C3496
   }
};
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)