---
title: ADVERTENCIA del compilador (nivel 1) C4545
ms.date: 11/04/2016
f1_keywords:
- C4545
helpviewer_keywords:
- C4545
ms.assetid: 43f8f34f-ed46-4661-95c0-c588c577ff73
ms.openlocfilehash: 39770a8c7ad5241ed625575c94dc19bf91e3b5bd
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966428"
---
# <a name="compiler-warning-level-1-c4545"></a>ADVERTENCIA del compilador (nivel 1) C4545

la expresión antes de la coma se evalúa como una función a la que le falta una lista de argumentos

El compilador detectó una expresión de coma con formato incorrecto.

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

En el ejemplo siguiente se genera C4545:

```cpp
// C4545.cpp
// compile with: /W1
#pragma warning (default : 4545)

void f() { }

int main()
{
   *(&f), 10;   // C4545
   // try the following line instead
   // (*(&f))(), 10;
}
```