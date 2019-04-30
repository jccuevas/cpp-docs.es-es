---
title: Error del compilador C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 8238dcec821256dad8101cd7ad59b2d85882c218
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345519"
---
# <a name="compiler-error-c3149"></a>Error del compilador C3149

'type': no se puede usar este tipo aquí sin un nivel superior 'char'

Una declaración no se especificó correctamente.

Por ejemplo, es posible que tiene definido un tipo CLR en el ámbito global y ha intentado crear una variable del tipo como parte de la definición. Dado que no se permiten variables globales de tipos CLR, el compilador genera el error C3149.

Para resolver este error, declare las variables de tipos CLR dentro de una definición de función o tipo.

El ejemplo siguiente genera el error C3149:

```
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

El ejemplo siguiente genera el error C3149:

```
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
