---
title: Advertencia del compilador (nivel 1) C4669
ms.date: 11/04/2016
f1_keywords:
- C4669
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
ms.openlocfilehash: b45490ec399249a721f2d2567ca0182d44667243
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175564"
---
# <a name="compiler-warning-level-1-c4669"></a>Advertencia del compilador (nivel 1) C4669

'cast': conversión no segura: 'class' es un objeto de tipo administrado o WinRT

Una conversión contiene un tipo administrado o de Windows Runtime. El compilador completa la conversión con una copia bit a bit de un puntero a otro, pero no realiza ninguna otra comprobación. Para resolver esta advertencia, no convierta las clases que contienen miembros administrados o tipos de Windows Runtime.

El ejemplo siguiente genera el error C4669 y muestra cómo corregirlo:

```cpp
// C4669.cpp
// compile with: /clr /W1
ref struct A {
   int i;
   Object ^ pObj;   // remove the managed member to fix the warning
};

ref struct B {
   int j;
};

int main() {
   A ^ a = gcnew A;
   B ^ b = reinterpret_cast<B ^>(a);   // C4669
}
```
