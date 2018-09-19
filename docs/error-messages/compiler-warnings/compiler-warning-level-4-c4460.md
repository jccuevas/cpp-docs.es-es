---
title: Compilador advertencia (nivel 4) C4460 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4460
dev_langs:
- C++
helpviewer_keywords:
- C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2635090d5aea4d5b80632ddf84b0eb3d2ccbdb6f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021296"
---
# <a name="compiler-warning-level-4-c4460"></a>Advertencia del compilador (nivel 4) C4460

El operador 'operator' de WinRT o CLR tiene el parámetro pasado por referencia. El operador 'operator' de WinRT o CLR tiene una semántica diferente del operador de C++ 'operator', ¿deseaba pasar por valor?

Ha pasado un valor por referencia a un operador CLR o a Windows Runtime definido por el usuario. Si el valor se cambia dentro de la función, tenga en cuenta que el valor devuelto después de la llamada a la función se asignará el valor devuelto de la función. En C++ estándar, el valor cambiado se refleja después de la llamada a función.

## <a name="example"></a>Ejemplo

El siguiente ejemplo genera el error C4460 y muestra cómo corregirlo.

```
// C4460.cpp
// compile with: /W4 /clr
#include <stdio.h>

public value struct V {
   static V operator ++(V& me) {   // C4460
   // try the following line instead
   // static V operator ++(V me) {

      printf_s(__FUNCSIG__ " called\n");
      V tmp = me;
      me.m_i++;
      return tmp;
   }
   int m_i;
};

int main() {
   V v;
   v.m_i = 0;

   printf_s("%d\n", v.m_i);   // Should print 0
   v++;   // Translates to "v = V::operator ++(v)"
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning
}
```