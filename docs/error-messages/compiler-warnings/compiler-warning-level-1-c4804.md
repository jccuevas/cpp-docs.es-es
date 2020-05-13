---
title: Advertencia del compilador (nivel 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 3f1b349599c77bc001911431fe0d83496ca3dfce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199412"
---
# <a name="compiler-warning-level-1-c4804"></a>Advertencia del compilador (nivel 1) C4804

' Operation ': uso no seguro del tipo ' bool ' en la operación

Esta advertencia es para cuando se utiliza una variable o un valor `bool` de una manera inesperada. Por ejemplo, C4804 se genera si se utilizan operadores como el operador unario negativo ( **-** ) o el operador de complemento (`~`). El compilador evalúa la expresión.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4804:

```cpp
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
