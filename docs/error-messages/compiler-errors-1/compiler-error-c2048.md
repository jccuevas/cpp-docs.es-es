---
title: Error del compilador C2048
ms.date: 11/04/2016
f1_keywords:
- C2048
helpviewer_keywords:
- C2048
ms.assetid: 44704726-85fc-42f0-afb9-194df8c4ca7c
ms.openlocfilehash: 2cdb151d882d7b494e8d32494b0b3c8c62e01b3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560399"
---
# <a name="compiler-error-c2048"></a>Error del compilador C2048

más de una etiqueta default

Una instrucción `switch` contiene varias etiquetas `default` . Elimine una de las etiquetas `default` para resolver el error.

El ejemplo siguiente genera la advertencia C2048:

```
// C2048.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
      default:   // C2048
         a = 3;
   }
}
```

Posible resolución:

```
// C2048b.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
   }
}
```