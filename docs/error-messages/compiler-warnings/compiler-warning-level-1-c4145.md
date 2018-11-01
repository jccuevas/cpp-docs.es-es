---
title: Advertencia del compilador (nivel 1) C4145
ms.date: 11/04/2016
f1_keywords:
- C4145
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
ms.openlocfilehash: 10c0211bfda354a00e05cba3131d047fce843df8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553795"
---
# <a name="compiler-warning-level-1-c4145"></a>Advertencia del compilador (nivel 1) C4145

'expression1': expresión relacional como expresión switch; posible confusión con 'expression2'

Una instrucción `switch` utiliza una expresión relacional como su expresión de control, lo que resulta en un valor booleano para las instrucciones **case** . ¿Quiso decir *expression2*?

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4145:

```
// C4145.cpp
// compile with: /W1
int main() {
   int i = 0;
   switch(i == 1) {   // C4145, use i instead of i == 1 to resolve
      case 1:
         break;
      default:
         break;
   }
}
```