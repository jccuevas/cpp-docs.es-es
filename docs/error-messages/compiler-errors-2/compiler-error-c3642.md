---
title: Error del compilador C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: 7c3f9f05bf04c9a1c20fff7910836e7b50468a8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742462"
---
# <a name="compiler-error-c3642"></a>Error del compilador C3642

' return_type/args ': no se puede llamar a una función con __clrcall Convención de llamada desde código nativo

No se puede llamar a una función marcada con la Convención de llamada [__clrcall](../../cpp/clrcall.md) desde código nativo (no administrado).

*return_type/args* es el nombre de la función o el tipo de la función de `__clrcall` a la que intenta llamar.  Se utiliza un tipo cuando se llama a través de un puntero a función.

Para llamar a una función administrada desde un contexto nativo, puede Agregar una función de "contenedor" que llamará a la función `__clrcall`. O bien, puede usar el mecanismo de serialización de CLR; vea [Cómo: calcular las referencias de punteros de función mediante PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) para obtener más información.

En el ejemplo siguiente se genera C3642:

```cpp
// C3642.cpp
// compile with: /clr
using namespace System;
struct S {
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall
      Console::WriteLine(s);
   }
   void Test2(char * s) {
      Test(gcnew String(s));
   }
};

#pragma unmanaged
int main() {
   S s;
   s.Test("abc");   // C3642
   s.Test2("abc");   // OK
}
```
