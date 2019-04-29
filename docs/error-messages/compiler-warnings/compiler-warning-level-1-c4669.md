---
title: Advertencia del compilador (nivel 1) C4669
ms.date: 11/04/2016
f1_keywords:
- C4669
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
ms.openlocfilehash: f4d0b87c91649c5f2f6b5823fea82d2ce355d11a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374604"
---
# <a name="compiler-warning-level-1-c4669"></a>Advertencia del compilador (nivel 1) C4669

'cast': conversión no segura: 'class' es un objeto de tipo administrado o WinRT

Una conversión contiene un tipo administrado o de Windows Runtime. El compilador completa la conversión con una copia bit a bit de un puntero a otro, pero no realiza ninguna otra comprobación. Para resolver esta advertencia, no convierta las clases que contienen miembros administrados o tipos de Windows Runtime.

El ejemplo siguiente genera el error C4669 y muestra cómo corregirlo:

```
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