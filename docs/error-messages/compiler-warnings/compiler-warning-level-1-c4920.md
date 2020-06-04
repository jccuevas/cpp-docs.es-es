---
title: Advertencia del compilador (nivel 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: b587a4ca2a78bc2ac54640adb2b149d97bef4def
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174666"
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

```cpp
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```
