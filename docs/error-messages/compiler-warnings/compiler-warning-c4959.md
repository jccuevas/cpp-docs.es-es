---
title: Advertencia del compilador C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 646347dec7bc2bac7fa73c8f754d2f9549cb2ba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473663"
---
# <a name="compiler-warning-c4959"></a>Advertencia del compilador C4959

> no se puede definir la estructura no administrada '*tipo*' en/CLR: safe porque el acceso a sus miembros proporciona código no comprobable

## <a name="remarks"></a>Comentarios

El acceso a un miembro de un tipo no administrado generará una imagen que no se puede comprobar (peverify.exe).

Para obtener más información, consulte [código puro y comprobable (C++ / c++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

El **/CLR: safe** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Esta advertencia se emite como un error y puede deshabilitarse con pragma [warning](../../preprocessor/warning.md) o la opción del compilador [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4959:

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```