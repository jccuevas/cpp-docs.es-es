---
title: Error del compilador C2361
ms.date: 11/04/2016
f1_keywords:
- C2361
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
ms.openlocfilehash: 747b85b57bee9e53f13a978254798a1dc268ef85
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759898"
---
# <a name="compiler-error-c2361"></a>Error del compilador C2361

la inicialización de ' Identifier ' se omite en la etiqueta ' default '

La inicialización de `identifier` se puede omitir en una instrucción `switch`. No se puede saltar una declaración con un inicializador a menos que la declaración se incluya en un bloque. (A menos que se declare dentro de un bloque, la variable está dentro del ámbito hasta el final de la instrucción `switch`).

En el ejemplo siguiente se genera C2361:

```cpp
// C2361.cpp
void func( void ) {
   int x;
   switch (x) {
   case 0 :
      int i = 1;
      { int j = 1; }
   default :   // C2361 error
      int k = 1;
   }
}
```

Solución posible:

```cpp
// C2361b.cpp
// compile with: /c
void func( void ) {
   int x = 0;
   switch (x) {
   case 0 :
      { int j = 1; int i = 1;}
   default :
      int k = 1;
   }
}
```
