---
title: ADVERTENCIA del compilador (nivel 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: 75d706fafacc5c1524915d063a7fa392cea01b4c
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624880"
---
# <a name="compiler-warning-level-1-c4258"></a>ADVERTENCIA del compilador (nivel 1) C4258

' variable ': se omite la definición del bucle for; la definición del ámbito de inclusión se usa "

En [/ze](../../build/reference/za-ze-disable-language-extensions.md) y [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md), las variables definidas en un bucle [for](../../cpp/for-statement-cpp.md) salen del ámbito después de que finalice el bucle **for** . Esta advertencia se produce si una variable con el mismo nombre que la variable de bucle, pero definida en el bucle de inclusión, se usa de nuevo en el ámbito que contiene el bucle **for** . Por ejemplo:

```cpp
// C4258.cpp
// compile with: /Zc:forScope /W1
int main()
{
   int i;
   {
      for (int i =0; i < 1; i++)
         ;
      i = 20;   // C4258 i (in for loop) has gone out of scope
   }
}
```