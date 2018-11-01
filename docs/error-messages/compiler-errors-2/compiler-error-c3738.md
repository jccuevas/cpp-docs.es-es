---
title: Error del compilador C3738
ms.date: 11/04/2016
f1_keywords:
- C3738
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
ms.openlocfilehash: e313c7d66bc030183e330dd961fad2fb35f02ac2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539329"
---
# <a name="compiler-error-c3738"></a>Error del compilador C3738

'convención de llamada': debe coincidir con la convención de llamada de la creación de instancias explícita de la plantilla que se va a crear una instancia

Se recomienda que no especifican una convención de llamada en una instancia explícita. Si es necesario, sin embargo, deben coincidir con las convenciones de llamada.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3738.

```
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