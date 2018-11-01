---
title: Error del compilador C3350
ms.date: 11/04/2016
f1_keywords:
- C3350
helpviewer_keywords:
- C3350
ms.assetid: cfbbc338-92b5-4f34-999e-aa2d2376bc70
ms.openlocfilehash: a19dbde6409afaae29e9110315c7c68fe9d43d62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547217"
---
# <a name="compiler-error-c3350"></a>Error del compilador C3350

'delegate': un constructor de delegado espera argumentos de número

Cuando se crea una instancia de un delegado, debe pasar dos argumentos, una instancia del tipo que contiene la función de delegado y la función.

El ejemplo siguiente genera la advertencia C3350:

```
// C3350.cpp
// compile with: /clr
delegate void SumDelegate();

public ref class X {
public:
   void F() {}
   static void F2() {}
};

int main() {
   X ^ MyX = gcnew X();
   SumDelegate ^ pSD = gcnew SumDelegate();   // C3350
   SumDelegate ^ pSD1 = gcnew SumDelegate(MyX, &X::F);
   SumDelegate ^ pSD2 = gcnew SumDelegate(&X::F2);
}
```
