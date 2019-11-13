---
title: ADVERTENCIA del compilador (nivel 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 97ad076325b11329896d98367fb3ac311ec5ded9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051569"
---
# <a name="compiler-warning-level-1-c4804"></a>ADVERTENCIA del compilador (nivel 1) C4804

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