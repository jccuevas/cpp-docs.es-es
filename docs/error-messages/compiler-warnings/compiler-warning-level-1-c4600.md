---
title: ADVERTENCIA del compilador (nivel 1) C4600
ms.date: 11/04/2016
f1_keywords:
- C4600
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
ms.openlocfilehash: 6eae37d006b5fcd6bd1c5e2993f1752c0534ee45
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966226"
---
# <a name="compiler-warning-level-1-c4600"></a>ADVERTENCIA del compilador (nivel 1) C4600

\#pragma ' nombre de macro ': se esperaba una cadena no vacía válida

No se puede especificar una cadena vacía cuando se presiona o se extrae un nombre de macro con el [pop_macro](../../preprocessor/pop-macro.md) o [push_macro](../../preprocessor/push-macro.md).

En el ejemplo siguiente se genera C4600:

```cpp
// C4600.cpp
// compile with: /W1
int main()
{
   #pragma push_macro("")   // C4600 passing an empty string
}
```