---
title: Compilador advertencia (nivel 3) C4995
ms.date: 11/04/2016
f1_keywords:
- C4995
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
ms.openlocfilehash: 54bc8931b5eaa3bbb5053e5c21aa2aaaa73126fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401519"
---
# <a name="compiler-warning-level-3-c4995"></a>Compilador advertencia (nivel 3) C4995

'function': se marcó el nombre como #pragma deprecated

El compilador encontró una función marcada con pragma [en desuso](../../preprocessor/deprecated-c-cpp.md). Puede que la función deje de ser compatible en futuras versiones. Puede desactivar esta advertencia con el [advertencia](../../preprocessor/warning.md) pragma (el ejemplo siguiente).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4995:

```
// C4995.cpp
// compile with: /W3
#include <stdio.h>

// #pragma warning(disable : 4995)
void func1(void)
{
    printf("\nIn func1");
}

int main()
{
    func1();
    #pragma deprecated(func1)
    func1();   // C4995
}
```