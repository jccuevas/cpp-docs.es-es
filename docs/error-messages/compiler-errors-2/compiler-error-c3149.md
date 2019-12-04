---
title: Error del compilador C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 263eb03b7a9f45458f8d8b586adc6f1cfc5805be
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745985"
---
# <a name="compiler-error-c3149"></a>Error del compilador C3149

' type ': no se puede usar este tipo aquí sin un ' char ' de nivel superior

No se especificó correctamente una declaración.

Por ejemplo, puede que haya definido un tipo CLR en el ámbito global e intente crear una variable del tipo como parte de la definición. Dado que no se permiten variables globales de tipos CLR, el compilador generará C3149.

Para resolver este error, declare variables de tipos CLR dentro de una función o una definición de tipo.

En el ejemplo siguiente se genera C3149:

```cpp
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

En el ejemplo siguiente se genera C3149:

```cpp
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
