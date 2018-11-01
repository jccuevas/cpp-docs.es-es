---
title: Error del compilador C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: 30a88d1047f8395fc8e3042cf2a1da88e6e5c2d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608421"
---
# <a name="compiler-error-c3288"></a>Error del compilador C3288

'type': desreferenciación no válida de un tipo de identificador

El compilador detectó una desreferenciación no válida de un tipo de identificador. Puede desreferenciar un tipo de identificador y asignarlo a una referencia. Para obtener más información, consulte [operador de referencia de seguimiento](../../windows/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3288.

```
// C3288.cpp
// compile with: /clr
ref class R {};
int main() {
   *(System::Object^) nullptr;   // C3288

// OK
   (System::Object^) nullptr;   // OK
   R^ r;
   R% pr = *r;
}
```