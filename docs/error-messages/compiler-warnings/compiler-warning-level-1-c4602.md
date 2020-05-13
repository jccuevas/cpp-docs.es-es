---
title: Advertencia del compilador (nivel 1) C4602
ms.date: 11/04/2016
f1_keywords:
- C4602
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
ms.openlocfilehash: f93af5b37c87e30891dd09009b53e73c7d384b1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162132"
---
# <a name="compiler-warning-level-1-c4602"></a>Advertencia del compilador (nivel 1) C4602

\#pragma pop_macro: ' macro name ' no hay ningún push_macro de #pragma anterior para este identificador

Si usa [pop_macro](../../preprocessor/pop-macro.md) para una macro concreta, primero debe haber pasado ese nombre de macro a [push_macro](../../preprocessor/push-macro.md). Por ejemplo, El ejemplo siguiente genera el error C4602:

```cpp
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```
