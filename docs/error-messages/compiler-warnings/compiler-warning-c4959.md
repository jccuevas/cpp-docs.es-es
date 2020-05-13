---
title: Advertencia del compilador C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 13d2ed705bff7b42eb3c348692a5829bd54158b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164877"
---
# <a name="compiler-warning-c4959"></a>Advertencia del compilador C4959

> no se puede definir la estructura no administrada '*Type*' en/clr: safe porque el acceso a sus miembros produce código no comprobable

## <a name="remarks"></a>Observaciones

El acceso a un miembro de un tipo no administrado generará una imagen que no se puede comprobar (peverify.exe).

Para obtener más información, consulte [código puro y comprobableC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

La opción del compilador **/clr: Safe** está en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

Esta advertencia se emite como un error y se puede deshabilitar con la pragma [warning](../../preprocessor/warning.md) o la opción del compilador [/wd](../../build/reference/compiler-option-warning-level.md) .

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
