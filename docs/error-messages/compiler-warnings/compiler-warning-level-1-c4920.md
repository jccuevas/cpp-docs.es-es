---
title: Advertencia del compilador (nivel 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: cd501cf0e3b434523623276027056c93c77fc278
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393485"
---
# <a name="compiler-warning-level-1-c4920"></a>Advertencia del compilador (nivel 1) C4920

enum enum member member = valor ya se vió en enum enum as member = valor

Si un archivo .tlb pasado a #import tiene el mismo símbolo definido en dos o más enumeraciones, esta advertencia indica que los símbolos idénticos posteriores se omitirán y se marcarán con comentarios en el archivo .tlh.

Suponiendo que un archivo .tlb contiene:

```
library MyLib
{
    typedef enum {
        enumMember = 512
    } AProblem;

    typedef enum {
        enumMember = 1024
    } BProblem;
};
```

los siguientes ejemplos generan el error C4920,

```
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```