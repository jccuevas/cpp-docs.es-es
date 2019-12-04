---
title: Error del compilador C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: d679ce0df0d43772a6c32aa8e00869ac1a4a082b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759651"
---
# <a name="compiler-error-c2743"></a>Error del compilador C2743

' type ': no se puede detectar un tipo nativo con __clrcall destructor o un constructor de copias

Un módulo compilado con **/CLR** intentó detectar una excepción de tipo nativo y donde el destructor o el constructor de copia del tipo utiliza `__clrcall` Convención de llamada.

Cuando se compila con **/CLR**, el control de excepciones espera que las funciones miembro de un tipo nativo se [__cdecl](../../cpp/cdecl.md) y no [__clrcall](../../cpp/clrcall.md). Los tipos nativos con funciones miembro que utilicen `__clrcall` Convención de llamada no se pueden capturar en un módulo compilado con **/CLR**.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2743.

```cpp
// C2743.cpp
// compile with: /clr
public struct S {
   __clrcall ~S() {}
};

public struct T {
   ~T() {}
};

int main() {
   try {}
   catch(S) {}   // C2743
   // try the following line instead
   // catch(T) {}

   try {}
   catch(S*) {}   // OK
}
```
