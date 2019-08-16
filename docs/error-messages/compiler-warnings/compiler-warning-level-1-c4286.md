---
title: Advertencia del compilador (nivel 1) C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: be02d330678eaab7f538ed092641f957bdcb01b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207074"
---
# <a name="compiler-warning-level-1-c4286"></a>Advertencia del compilador (nivel 1) C4286

'type1': ha sido detectada por la clase base ('tipo2') en la línea número

El tipo de excepción especificada está controlado por un controlador anterior. El tipo del segundo elemento catch se deriva el tipo de la primera. Excepciones para una clase base detectar las excepciones para una clase derivada.

## <a name="example"></a>Ejemplo

```
//C4286.cpp
// compile with: /W1
#include <eh.h>
class C {};
class D : public  C {};
int main()
{
    try
    {
        throw "ooops!";
    }
    catch( C ) {}
    catch( D ) {}  // warning C4286, D is derived from C
}
```