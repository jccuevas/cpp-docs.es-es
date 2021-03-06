---
title: Advertencia del compilador (nivel 1) C4556
ms.date: 08/27/2018
f1_keywords:
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: 501d79a8a86fcd3e2d8ba08dc2f03488f9abb827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162314"
---
# <a name="compiler-warning-level-1-c4556"></a>Advertencia del compilador (nivel 1) C4556

> el valor del argumento inmediato intrínseco '*Value*' está fuera del intervalo '*límite inferior* - *superior*'

## <a name="remarks"></a>Observaciones

Un intrínseco coincide con una instrucción de hardware. La instrucción de hardware tiene un número fijo de bits para codificar la constante. Si el *valor* está fuera del intervalo, no se codificará correctamente. El compilador trunca los bits adicionales.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4556:

```cpp
// C4556.cpp
// compile with: /W1
// processor: x86 IPF
#include <xmmintrin.h>

void test()
{
   __m64 m;
   _m_pextrw(m, 5);   // C4556
}

int main()
{
}
```
