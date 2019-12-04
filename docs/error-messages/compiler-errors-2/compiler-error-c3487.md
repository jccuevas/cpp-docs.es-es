---
title: Error del compilador C3487
ms.date: 11/04/2016
f1_keywords:
- C3487
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
ms.openlocfilehash: 7b38755470e3746066711382b2ed471badc8e197
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738445"
---
# <a name="compiler-error-c3487"></a>Error del compilador C3487

'return type': todas las expresiones return deben deducirse como el mismo tipo: antes era 'return type'

Una expresión lambda debe especificar su tipo de valor devuelto a menos que contenga una sola instrucción return. Si una expresión lambda contiene varias instrucciones return, todas deben tener el mismo tipo.

### <a name="to-correct-this-error"></a>Para corregir este error

- Especifique un tipo de valor devuelto final para la expresión lambda. Compruebe que todos los valores devueltos de la expresión lambda son del mismo tipo o pueden convertirse implícitamente al tipo de valor devuelto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera el error C3487 porque los tipos de valor devueltos de la expresión lambda no coinciden:

```cpp
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
