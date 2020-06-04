---
title: Error del compilador C2758
ms.date: 11/04/2016
f1_keywords:
- C2758
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
ms.openlocfilehash: c854aeff1c57b8be6b445bc3615008519ca00af7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759521"
---
# <a name="compiler-error-c2758"></a>Error del compilador C2758

'member': debe inicializarse un miembro de tipo de referencia

El error del compilador C2758 se produce cuando el constructor no inicializa un miembro de tipo de referencia en una lista de inicializadores. El compilador deja el miembro sin definir. Las variables de miembro de referencia deben inicializarse cuando se declaran o se les debe dar un valor en la lista de inicialización del constructor.

El siguiente ejemplo genera el error C2758:

```cpp
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```
