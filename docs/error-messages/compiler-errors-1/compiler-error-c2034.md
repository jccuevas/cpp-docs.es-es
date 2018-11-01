---
title: Error del compilador C2034
ms.date: 11/04/2016
f1_keywords:
- C2034
helpviewer_keywords:
- C2034
ms.assetid: 953d70fa-bde9-4ce6-a55d-741e7bc63ff4
ms.openlocfilehash: 4b4fe769f78e5f826ba08d4819019210f21f860f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479682"
---
# <a name="compiler-error-c2034"></a>Error del compilador C2034

'identifier': tipo de campo de bits demasiado pequeño para el número de bits

El número de bits de la declaración de campo de bits supera el tamaño del tipo base.

El ejemplo siguiente genera C2034:

```
// C2034.cpp
struct A {
   char test : 9;   // C2034, char has 8 bits
};
```

Posible resolución:

```
// C2034b.cpp
// compile with: /c
struct A {
   char test : 8;
};
```