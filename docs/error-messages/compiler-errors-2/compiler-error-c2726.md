---
title: Error del compilador C2726
ms.date: 11/04/2016
f1_keywords:
- C2726
helpviewer_keywords:
- C2726
ms.assetid: f0191bb7-c175-450b-bf09-a3213db96d09
ms.openlocfilehash: 36ddf54b3924ae48969fa810ba2883c51b2264b5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757428"
---
# <a name="compiler-error-c2726"></a>Error del compilador C2726

'gcnew' solo se puede usar para crear un objeto con tipo WinRT o administrado

No se puede crear una instancia de un tipo nativo en el montón de recolección de elementos no utilizados.

En el ejemplo siguiente se genera el error C2726 y se muestra cómo corregirlo:

```cpp
// C2726.cpp
// compile with: /clr
using namespace System;
class U {};
ref class V {};
value class W {};

int main() {
   U* pU = gcnew U;    // C2726
   U* pU2 = new U;   // OK
   V^ p2 = gcnew V;   // OK
   W p3;   // OK

}
```
