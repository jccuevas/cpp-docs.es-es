---
title: Error del compilador C2758
ms.date: 11/04/2016
f1_keywords:
- C2758
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
ms.openlocfilehash: c3a86b8b8c7f122929a52221d4f01a17c50395be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618041"
---
# <a name="compiler-error-c2758"></a>Error del compilador C2758

'member': debe inicializarse un miembro de tipo de referencia

El error del compilador C2758 se produce cuando el constructor no inicializa un miembro de tipo de referencia en una lista de inicializadores. El compilador deja el miembro sin definir. Las variables de miembro de referencia deben inicializarse cuando se declaran o se les debe dar un valor en la lista de inicialización del constructor.

El siguiente ejemplo genera el error C2758:

```
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```