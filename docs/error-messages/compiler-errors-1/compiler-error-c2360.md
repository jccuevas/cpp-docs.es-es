---
title: Error del compilador C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 226fcd8a27c9abdb789b8191a5cf4e59cc4a66cc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759911"
---
# <a name="compiler-error-c2360"></a>Error del compilador C2360

la inicialización de ' Identifier ' se omite en la etiqueta ' Case '

La inicialización de `identifier` se puede omitir en una instrucción `switch`. No se puede saltar una declaración con un inicializador a menos que la declaración se incluya en un bloque. (A menos que se declare dentro de un bloque, la variable está dentro del ámbito hasta el final de la instrucción `switch`).

En el ejemplo siguiente se genera C2360:

```cpp
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

Solución posible:

```cpp
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```
