---
title: Advertencia del compilador (nivel 1) C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: e706a448f4264eceedbb4fa8932c0fc30e88d532
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175745"
---
# <a name="compiler-warning-level-1-c4288"></a>Advertencia del compilador (nivel 1) C4288

se ha utilizado una extensión no estándar: ' var ': la variable de control de bucles declarada en el bucle for se utiliza fuera del ámbito del bucle for; entra en conflicto con la declaración en el ámbito externo

Al compilar con [/ze](../../build/reference/za-ze-disable-language-extensions.md) y **/Zc: forScope-** , una variable declarada en un bucle **for** se usaba después del ámbito del bucle [for](../../cpp/for-statement-cpp.md). Una extensión de Microsoft al C++ lenguaje permite que esta variable permanezca en el ámbito y C4288 le recuerda que no se usa la primera declaración de la variable.

Consulte [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) para obtener información sobre cómo especificar la extensión de Microsoft en bucles **for** con/ze.

En el ejemplo siguiente se genera C4288:

```cpp
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```
