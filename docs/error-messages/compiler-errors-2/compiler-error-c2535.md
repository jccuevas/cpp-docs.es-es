---
title: Error del compilador C2535
ms.date: 11/04/2016
f1_keywords:
- C2535
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
ms.openlocfilehash: b2b5452cfe59284d56b019674ffbabbda0dc62d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574035"
---
# <a name="compiler-error-c2535"></a>Error del compilador C2535

'identificador' : función miembro ya definida o declarada

Este error podría producirse al utilizar la misma lista de parámetros formales en más una definición o declaración de una función sobrecargada.

Si obtiene el error C2535 debido a la función Dispose, vea [destructores y finalizadores](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) para obtener más información.

El ejemplo siguiente genera el error C2535:

```
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```