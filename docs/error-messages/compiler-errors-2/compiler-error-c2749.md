---
title: Error del compilador C2749
ms.date: 11/04/2016
f1_keywords:
- C2749
helpviewer_keywords:
- C2749
ms.assetid: a81aef36-cdca-4d78-89d5-b72eff2500b2
ms.openlocfilehash: 71c2f3d3a297d70501c675ac6a9f750cbdf0d421
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759625"
---
# <a name="compiler-error-c2749"></a>Error del compilador C2749

' type ': solo puede producir o detectar el identificador de una clase administrada con/CLR: Safe

Al usar **/clr: Safe**, solo puede producir o detectar un tipo de referencia.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2749:

```cpp
// C2749.cpp
// compile with: /clr:safe
ref struct MyStruct {
public:
   int i;
};

int main() {
   MyStruct ^x = gcnew MyStruct;

   // Delete the following 4 lines to resolve.
   try {
      throw (1);   // C2749
   }
   catch(int){}

   // OK
   try {
      throw (x);
   }
   catch(MyStruct ^){}
}
```
