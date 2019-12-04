---
title: Error del compilador C3738
ms.date: 11/04/2016
f1_keywords:
- C3738
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
ms.openlocfilehash: ffefa0eff23e11412573b8062fa15bb5679923e7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752774"
---
# <a name="compiler-error-c3738"></a>Error del compilador C3738

' calling_convention ': la Convención de llamada de la creación de instancias explícita debe coincidir con la de la plantilla de la que se crean instancias

Se recomienda no especificar una Convención de llamada en una creación de instancias explícita. Sin embargo, si es necesario, las convenciones de llamada deben coincidir.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3738.

```cpp
// C3738.cpp
// compile with: /clr
// processor: x86
#include <stdio.h>
template< class T >
void f ( T arg ) {   // by default calling convention is __cdecl
   printf ( "f: %s\n", __FUNCSIG__ );
}

template
void __stdcall f< int > ( int arg );   // C3738
// try the following line instead
// void f< int > ( int arg );

int main () {
   f(1);
   f< int > ( 1 );
}
```
