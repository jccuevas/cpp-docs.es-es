---
title: Error del compilador C2583
ms.date: 11/04/2016
f1_keywords:
- C2583
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
ms.openlocfilehash: b78b9dd69b701e1a66646234d4603973657e90c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597982"
---
# <a name="compiler-error-c2583"></a>Error del compilador C2583

'identifier': ' const/volatile' puntero 'this' no es válido para constructores/destructores

Se declara un constructor o destructor `const` o `volatile`. Esto no está permitido.

El ejemplo siguiente genera C2583:

```
// C2583.cpp
// compile with: /c
class A {
public:
   int i;
   A() const;   // C2583

   // try the following line instead
   // A();
};
```