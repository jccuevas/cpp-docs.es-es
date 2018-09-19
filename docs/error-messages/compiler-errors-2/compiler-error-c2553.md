---
title: Error del compilador C2553 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2553
dev_langs:
- C++
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38fb61b7281dd0371c546fd7b7bc960232cf2e00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043994"
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