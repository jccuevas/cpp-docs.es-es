---
title: Advertencia del compilador (nivel 1) C4556
ms.date: 08/27/2018
f1_keywords:
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: c31602766261a8d6d0c4f0bb0a880ee34ee1ed45
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815411"
---
# <a name="compiler-warning-level-1-c4556"></a>Advertencia del compilador (nivel 1) C4556

> valor del argumento inmediato intrínseco '*valor*'está fuera del intervalo'*lowerbound* - *upperbound*'

## <a name="remarks"></a>Comentarios

Intrínseco coincide con una instrucción máquina. La instrucción máquina tiene un número fijo de bits para codificar la constante. Si *valor* está fuera del intervalo, no se codificará correctamente. El compilador trunca los bits adicionales.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4556:

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