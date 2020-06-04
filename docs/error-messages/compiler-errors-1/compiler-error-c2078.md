---
title: Error del compilador C2078
ms.date: 11/04/2016
f1_keywords:
- C2078
helpviewer_keywords:
- C2078
ms.assetid: 9bead850-4123-46cf-a634-5c77ba974b2b
ms.openlocfilehash: 514776c0feb12c46dea56dd8e85043345754a229
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756453"
---
# <a name="compiler-error-c2078"></a>Error del compilador C2078

hay demasiados inicializadores

El número de inicializadores supera el número de objetos que deben inicializarse.

El compilador puede deducir la asignación correcta de inicializadores a objetos y objetos internos cuando se eliden las llaves internas de la lista de inicializadores. Si se usan todas las llaves, se elimina la ambigüedad y, como resultado, se consigue una asignación correcta. Si las llaves se usan de forma parcial, puede generarse el error C2078 debido a la ambigüedad en la asignación de los inicializadores a los objetos.

El ejemplo siguiente genera el error C2078 y muestra cómo corregirlo:

```cpp
// C2078.cpp
// Compile by using: cl /c /W4 C2078.cpp
struct S {
   struct {
      int x, y;
   } z[2];
};

int main() {
   int d[2] = {1, 2, 3};   // C2078
   int e[2] = {1, 2};      // OK

   char a[] = {"a", "b"};  // C2078
   char *b[] = {"a", "b"}; // OK
   char c[] = {'a', 'b'};  // OK

   S s1{1, 2, 3, 4};       // OK
   S s2{{1, 2}, {3, 4}};   // C2078
   S s3{{1, 2, 3, 4}};     // OK
   S s4{{{1, 2}, {3, 4}}}; // OK
}
```
