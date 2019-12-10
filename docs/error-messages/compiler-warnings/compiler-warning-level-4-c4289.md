---
title: Advertencia del compilador (nivel 4) C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: b9083670465d68493d90a8e96ff7ee5db34c1978
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991324"
---
# <a name="compiler-warning-level-4-c4289"></a>Advertencia del compilador (nivel 4) C4289

se ha utilizado una extensión no estándar : 'var' : la variable de control de bucles declarada en el bucle For se utiliza fuera del ámbito del bucle For

Al compilar con [/ze](../../build/reference/za-ze-disable-language-extensions.md) y **/Zc: forScope-** , una variable declarada en un bucle [for](../../cpp/for-statement-cpp.md) se usaba después del ámbito del bucle **for**.

Vea [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) para obtener información sobre cómo especificar el comportamiento estándar en los bucles **for** con **/ze**.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

En el ejemplo siguiente se genera C4289:

```cpp
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```
