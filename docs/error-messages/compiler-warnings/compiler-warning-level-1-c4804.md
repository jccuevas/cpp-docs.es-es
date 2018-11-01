---
title: Advertencia del compilador (nivel 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 28b3e49717993a3bf20c8cfec5938d698266c0f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476081"
---
# <a name="compiler-warning-level-1-c4804"></a>Advertencia del compilador (nivel 1) C4804

'operación': uso no seguro del tipo 'bool' en la operación

Esta advertencia es para cuando usa un `bool` variable o un valor de forma inesperada. Por ejemplo, se genera C4804 si usa operadores como el operador unario negativo (**-**) o el operador de complemento (`~`). El compilador evalúa la expresión.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4804:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```