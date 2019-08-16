---
title: Advertencia del compilador (nivel 4) C4245
ms.date: 11/04/2016
f1_keywords:
- c4254
helpviewer_keywords:
- C4254
ms.assetid: c7dcef24-d535-4c98-bb41-fc3d2b88fd11
ms.openlocfilehash: 925428cffae37ea26144e5b550cbc7988b33ef01
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400986"
---
# <a name="compiler-warning-level-4-c4254"></a>Advertencia del compilador (nivel 4) C4245

'operador': conversión de 'tipo1' a 'tipo2', posible pérdida de datos

Un campo de bits mayor se asignó a un campo de bits más pequeño. Podría haber una pérdida de datos.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

El ejemplo siguiente genera C4254:

```
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