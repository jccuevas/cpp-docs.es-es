---
title: Error del compilador C2312
ms.date: 11/04/2016
f1_keywords:
- C2312
helpviewer_keywords:
- C2312
ms.assetid: c8bcfd06-12c1-4323-bb53-ba392d36daa4
ms.openlocfilehash: 2c8d360be43c46b1a26c833dbb8aa95a7e3740e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478785"
---
# <a name="compiler-error-c2312"></a>Error del compilador C2312

'exception1': la capturó 'exception2' en la línea número

Dos controladores capturan el mismo tipo de excepción.

El ejemplo siguiente genera la advertencia C2312:

```
// C2312.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
    try {
        throw "ooops!";
    }
    catch( signed int ) {}
    catch( int ) {}   // C2312
}
```