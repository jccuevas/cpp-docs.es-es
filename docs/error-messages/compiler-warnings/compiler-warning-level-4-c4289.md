---
title: Advertencia del compilador (nivel 4) C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: 3a997af466ddfdaaf4631afeb53d917ce0338c3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488821"
---
# <a name="compiler-warning-level-4-c4289"></a>Advertencia del compilador (nivel 4) C4289

se ha utilizado una extensión no estándar : 'var' : la variable de control de bucles declarada en el bucle For se utiliza fuera del ámbito del bucle For

Cuando se compila con [/Ze](../../build/reference/za-ze-disable-language-extensions.md) y **forScope**, una variable declarada en un [para](../../cpp/for-statement-cpp.md) bucle se usa después la **para**-ámbito del bucle.

Consulte [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) para obtener información acerca de cómo especificar el comportamiento estándar en **para** bucles con **/Ze**.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

El ejemplo siguiente genera C4289:

```
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```