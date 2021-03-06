---
title: Advertencia del compilador (nivel 1) C4730
ms.date: 11/04/2016
f1_keywords:
- C4730
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
ms.openlocfilehash: ba6d305a414e99bd22ca603aaac2615994780c7d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185768"
---
# <a name="compiler-warning-level-1-c4730"></a>Advertencia del compilador (nivel 1) C4730

' Main ': la combinación de expresiones de _m64 y de punto flotante puede dar lugar a código incorrecto

Una función utiliza los tipos de [__m64](../../cpp/m64.md) y **float**/**Double** . Dado que los registros MMX y de punto flotante comparten el mismo espacio de registro físico (no se pueden usar simultáneamente), el uso de `__m64` y **float**/tipos **Double** en la misma función puede provocar daños en los datos, lo que podría producir una excepción.

Para usar de forma segura tipos de `__m64` y tipos de punto flotante en la misma función, cada instrucción que usa uno de los tipos debe estar separada por el **_m_empty ()** (para MMX) o **_M_femms (** para 3DNow!) intrínseco.

En el ejemplo siguiente se genera C4730:

```cpp
// C4730.cpp
// compile with: /W1
// processor: x86
#include "mmintrin.h"

void func(double)
{
}

int main(__m64 a, __m64 b)
{
   __m64 m;
   double f;
   f = 1.0;
   m = _m_paddb(a, b);
   // uncomment the next line to resolve C4730
   // _m_empty();
   func(f * 3.0);   // C4730
}
```
