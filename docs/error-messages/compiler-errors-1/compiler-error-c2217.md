---
title: Error del compilador C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: 7417c651fde6bef781bb6eb2e081cd3ad8ecc3a0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741305"
---
# <a name="compiler-error-c2217"></a>Error del compilador C2217

' atributo1 ' requiere ' attribute2 '

El primer atributo de función requiere el segundo atributo.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Función Interrupt (`__interrupt`) declarada como `near`. Las funciones de interrupción deben ser `far`.

1. Función de interrupción declarada con `__stdcall`o `__fastcall`. Las funciones de interrupción deben usar las convenciones de llamada de C.

## <a name="example"></a>Ejemplo

C2217 también se puede producir si se intenta enlazar un delegado a una función CLR que toma un número variable de argumentos. Si la función también tiene una sobrecarga de matriz de parámetros de e, utilice en su lugar. En el ejemplo siguiente se genera C2217.

```cpp
// C2217.cpp
// compile with: /clr
using namespace System;
delegate void MyDel(String^, Object^, Object^, ...);   // C2217
delegate void MyDel2(String ^, array<Object ^> ^);   // OK

int main() {
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);
   array<Object ^ > ^ x = gcnew array<Object ^>(2);
   x[0] = safe_cast<Object^>(0);
   x[1] = safe_cast<Object^>(1);

   // wl("{0}, {1}", 0, 1);
   wl("{0}, {1}", x);
}
```
