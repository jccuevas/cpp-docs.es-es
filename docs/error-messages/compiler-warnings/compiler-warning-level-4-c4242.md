---
title: Advertencia del compilador (nivel 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: e0582f3dfdd223b4571e361dc69fae1990aeea1c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401012"
---
# <a name="compiler-warning-level-4-c4242"></a>Advertencia del compilador (nivel 4) C4242

'identifier': conversión de 'tipo1' a 'tipo2', posible pérdida de datos

Los tipos son diferentes. Conversión de tipos puede provocar la pérdida de datos. El compilador realiza la conversión de tipos.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

Para obtener más información sobre C4242, consulte [errores comunes del compilador](/windows/desktop/WinProg64/common-compiler-errors).

El ejemplo siguiente genera C4242:

```
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