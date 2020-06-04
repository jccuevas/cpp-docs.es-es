---
title: Advertencia del compilador (nivel 1) C4600
ms.date: 11/04/2016
f1_keywords:
- C4600
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
ms.openlocfilehash: 15ad64ad29f6f01253a2329fb04897c299cedff9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186080"
---
# <a name="compiler-warning-level-1-c4600"></a>Advertencia del compilador (nivel 1) C4600

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
