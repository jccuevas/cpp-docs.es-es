---
title: Error del compilador C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: d076dabe0df91cefb90be5ec9e90f371331a51f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300631"
---
# <a name="compiler-error-c3288"></a>Error del compilador C3288

'type': desreferenciación no válida de un tipo de identificador

El compilador detectó una desreferenciación no válida de un tipo de identificador. Puede desreferenciar un tipo de identificador y asignarlo a una referencia. Para obtener más información, consulte [operador de referencia de seguimiento](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

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