---
title: Error del compilador C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: 03cd7c13e093be5073b3df7e7cf29dda870bc47a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531006"
---
# <a name="compiler-error-c2743"></a>Error del compilador C2743

'type': no se puede detectar un tipo nativo con el destructor __clrcall o el constructor de copias

Un módulo compilado con **/CLR** intentó detectar una excepción de tipo nativo y en la que se utiliza el tipo destructor o constructor de copias `__clrcall` convención de llamada.

Cuando se compila con **/CLR**, control de excepciones espera que las funciones miembro de un tipo nativo que [__cdecl](../../cpp/cdecl.md) y no [__clrcall](../../cpp/clrcall.md). Los tipos nativos con funciones miembro mediante `__clrcall` convención de llamada no se pueden detectar en un módulo compilado con **/CLR**.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2743.

```
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