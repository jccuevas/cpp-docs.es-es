---
title: Error del compilador C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: b9542f1904c6797a77c88c88a37aff9348364268
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738185"
---
# <a name="compiler-error-c3496"></a>Error del compilador C3496

'this' siempre se captura por valor: se ha omitido '&'

No se puede capturar el `this` puntero por referencia.

### <a name="to-correct-this-error"></a>Para corregir este error

- Capture el puntero `this` por valor.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3496 porque una referencia al puntero `this` aparece en la lista de captura de una expresión lambda:

```cpp
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
