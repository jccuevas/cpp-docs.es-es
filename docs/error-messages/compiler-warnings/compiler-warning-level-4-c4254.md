---
title: Advertencia del compilador (nivel 4) C4245
ms.date: 11/04/2016
f1_keywords:
- c4254
helpviewer_keywords:
- C4254
ms.assetid: c7dcef24-d535-4c98-bb41-fc3d2b88fd11
ms.openlocfilehash: 33b3ba795acb8c72c7d1630071aa2884b6137464
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541941"
---
# <a name="compiler-warning-level-4-c4254"></a>Advertencia del compilador (nivel 4) C4245

' operador ': conversión de ' tipo1 ' a ' tipo2 ', posible pérdida de datos

Se asignó un campo de bits mayor a un campo de bits más pequeño. Podría haber una pérdida de datos.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

En el ejemplo siguiente se genera C4254:

```cpp
// C4254.cpp
// compile with: /W4
#pragma warning(default: 4254)

struct X {
   int a : 20;
   int b : 12;
};

int main() {
   X *x = new X();
   x->b = 10;
   x->a = 4;
   x->a = x->b;    // OK
   x->b = x->a;    // C4254
};
```