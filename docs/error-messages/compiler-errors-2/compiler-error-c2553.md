---
title: Error del compilador C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: 11cb2b83d958f0c59d05034a716a022f00b326ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658685"
---
# <a name="compiler-error-c2553"></a>Error del compilador C2553

'función_base': función virtual de invalidación devolver tipo difiere de 'función_de_reemplazo'

Una función en una clase derivada intentó reemplazar una función virtual en una clase base, pero la función de la clase derivada no tenía el mismo tipo de valor devuelto que la función de la clase base.  Una firma de función de reemplazo debe coincidir con la firma de la función que se va a reemplazar.

El ejemplo siguiente genera C2553:

```
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```