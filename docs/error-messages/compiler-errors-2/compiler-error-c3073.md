---
title: Error del compilador C3073
ms.date: 11/04/2016
f1_keywords:
- C3073
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
ms.openlocfilehash: 0b53e704c14746579a32550726364c062a9ade6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756752"
---
# <a name="compiler-error-c3073"></a>Error del compilador C3073

' type ': la clase Ref no tiene un constructor de copias definido por el usuario

En una compilación [/CLR (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , el compilador no generará un constructor de copias para un tipo de referencia. En cualquier compilación de **/CLR** , debe definir su propio constructor de copias para un tipo de referencia si espera que se copie una instancia del tipo.

Para obtener más información, vea [ C++ semántica de pila para los tipos de referencia](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3073.

```cpp
// C3073.cpp
// compile with: /clr
ref class R {
public:
   R(int) {}
};

ref class S {
public:
   S(int) {}
   S(const S %rhs) {}   // copy constructor
};

void f(R) {}
void f2(S) {}
void f3(R%){}

int main() {
   R r(1);
   f(r);   // C3073
   f3(r);   // OK

   S s(1);
   f2(s);   // OK
}
```
