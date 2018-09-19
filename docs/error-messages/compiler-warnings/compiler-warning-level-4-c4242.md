---
title: Del compilador (nivel 4) de la advertencia C4242 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4242
dev_langs:
- C++
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9879b9258902a496dd46c59c44f7bf211726e460
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056877"
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