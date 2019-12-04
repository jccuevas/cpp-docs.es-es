---
title: Error del compilador C2511
ms.date: 11/04/2016
f1_keywords:
- C2511
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
ms.openlocfilehash: ff78cb50b274fe40d513739264bd7e9894bbed9d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746570"
---
# <a name="compiler-error-c2511"></a>Error del compilador C2511

' Identifier ': la función miembro sobrecargada no se encuentra en ' clase '

No se ha declarado ninguna versión de la función con los parámetros especificados.  Posibles causas:

1. Se pasaron parámetros incorrectos a la función.

1. Parámetros pasados en orden incorrecto.

1. Ortografía incorrecta de los nombres de parámetro.

En el ejemplo siguiente se genera C2511:

```cpp
// C2511.cpp
// compile with: /c
class C {
   int c_2;
   int Func(char *, char *);
};

int C::Func(char *, char *, int i) {   // C2511
// try the following line instead
// int C::Func(char *, char *) {
   return 0;
}
```
