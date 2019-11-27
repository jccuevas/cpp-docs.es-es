---
title: Advertencia del compilador (nivel 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: 3123a414dc7a169d2a472dad96d659a9e56c9020
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541746"
---
# <a name="compiler-warning-level-4-c4242"></a>Advertencia del compilador (nivel 4) C4242

' Identifier ': conversión de ' tipo1 ' a ' tipo2 ', posible pérdida de datos

Los tipos son diferentes. La conversión de tipos puede provocar la pérdida de datos. El compilador realiza la conversión de tipos.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

Para obtener información adicional sobre C4242, vea [errores comunes del compilador](/windows/win32/WinProg64/common-compiler-errors).

En el ejemplo siguiente se genera C4242:

```cpp
// C4242.cpp
// compile with: /W4
#pragma warning(4:4242)
int func() {
   return 0;
}

int main() {
   char a;
   a = func();   // C4242, return type and variable type do not match
}
```