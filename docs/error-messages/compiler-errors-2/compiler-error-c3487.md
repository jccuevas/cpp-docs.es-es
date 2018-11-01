---
title: Error del compilador C3487
ms.date: 11/04/2016
f1_keywords:
- C3487
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
ms.openlocfilehash: a1c4b667e23ff167b28b9f22f93b0930545c915c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492619"
---
# <a name="compiler-error-c3487"></a>Error del compilador C3487

'return type': todas las expresiones return deben deducirse como el mismo tipo: antes era 'return type'

Una expresión lambda debe especificar su tipo de valor devuelto a menos que contenga una sola instrucción return. Si una expresión lambda contiene varias instrucciones return, todas deben tener el mismo tipo.

### <a name="to-correct-this-error"></a>Para corregir este error

- Especifique un tipo de valor devuelto final para la expresión lambda. Compruebe que todos los valores devueltos de la expresión lambda son del mismo tipo o pueden convertirse implícitamente al tipo de valor devuelto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera el error C3487 porque los tipos de valor devueltos de la expresión lambda no coinciden:

```
// C3487.cpp
// Compile by using: cl /c /W4 C3487.cpp

int* test(int* pi) {
   // To fix the error, uncomment the trailing return type below
   auto odd_pointer = [=]() /* -> int* */ {
      if (*pi % 2)
         return pi;
      return nullptr; // C3487 - nullptr is not an int* type
   };
   return odd_pointer();
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)