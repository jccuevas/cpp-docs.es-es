---
title: Advertencia del compilador (nivel 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: e32509e4d32eef4f53b8d43a7db769844f1182c7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779471"
---
# <a name="compiler-warning-level-1-c4572"></a>Advertencia del compilador (nivel 1) C4572

El atributo [ParamArray] está en desuso en/CLR, use '...' en lugar de

Se ha utilizado un estilo obsoleto para especificar una lista de argumentos de variable. Cuando se compila para CLR, use la sintaxis de puntos suspensivos en lugar de <xref:System.ParamArrayAttribute>. Para obtener más información, consulte [listas de argumentos variables (...) (C++ / C++ / CLI) ](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

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