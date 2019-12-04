---
title: Error del compilador C3737
ms.date: 11/04/2016
f1_keywords:
- C3737
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
ms.openlocfilehash: 25dbb8897db45cbddaaf7f0530bcb2a8653b03cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752800"
---
# <a name="compiler-error-c3737"></a>Error del compilador C3737

' Delegate ': un delegado no puede tener una Convención de llamada explícita

No se puede especificar la [Convención de llamada](../../cpp/calling-conventions.md) para un `delegate`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3737:

```cpp
// C3737a.cpp
// compile with: /clr
delegate void __stdcall MyFunc();   // C3737
// Try the following line instead.
// delegate void MyFunc();

int main() {
}
```
