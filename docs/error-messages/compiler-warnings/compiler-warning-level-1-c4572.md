---
title: Advertencia del compilador (nivel 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: b4d3356522faacfc343c33908b64597387fbe51c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521078"
---
# <a name="compiler-warning-level-1-c4572"></a>Advertencia del compilador (nivel 1) C4572

El atributo [ParamArray] está desusado en /clr; use '...' en su lugar

Se ha utilizado un estilo obsoleto para especificar una lista de argumentos de variable. Cuando se compila para CLR, use la sintaxis de puntos suspensivos en lugar de <xref:System.ParamArrayAttribute>. Para obtener más información, consulte [listas de argumentos variables (...) (C++ / C++ / CLI) ](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4572.

```
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```