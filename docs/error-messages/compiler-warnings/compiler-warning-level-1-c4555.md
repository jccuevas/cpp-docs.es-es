---
title: Advertencia del compilador (nivel 1) C4555
ms.date: 11/04/2016
f1_keywords:
- C4555
helpviewer_keywords:
- C4555
ms.assetid: 50b286c1-f7bf-4292-b1fa-baaac9538611
ms.openlocfilehash: fb3373178ebb53d7b14228a361fcc2f0a08c873b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162366"
---
# <a name="compiler-warning-level-1-c4555"></a>Advertencia del compilador (nivel 1) C4555

la expresión no tiene efecto; se esperaba una expresión con efecto secundario

Esta advertencia le informa cuando una expresión no tiene ningún efecto.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

Por ejemplo:

```cpp
// C4555.cpp
// compile with: /W1
#pragma warning(default:4555)

void func1()
{
   1;   // C4555
}

void func2()
{
   int x;
   x;   // C4555
}

int main()
{
}
```
