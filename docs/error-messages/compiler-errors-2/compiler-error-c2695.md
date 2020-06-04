---
title: Error del compilador C2695
ms.date: 11/04/2016
f1_keywords:
- C2695
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
ms.openlocfilehash: 6d46699a2036c4f45daf3c34802ddb6b44e554ff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755218"
---
# <a name="compiler-error-c2695"></a>Error del compilador C2695

' function1 ': la función virtual de invalidación solo es distinta de ' función2 ' mediante la Convención de llamada

La firma de una función en una clase derivada no puede invalidar una función en una clase base y cambiar la Convención de llamada.

En el ejemplo siguiente se genera C2695:

```cpp
// C2695.cpp
class C {
   virtual void __fastcall func();
};

class D : public C {
   virtual void __clrcall func();   // C2695
};
```
