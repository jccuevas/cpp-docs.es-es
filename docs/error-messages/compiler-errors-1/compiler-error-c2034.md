---
title: Error del compilador C2034
ms.date: 11/04/2016
f1_keywords:
- C2034
helpviewer_keywords:
- C2034
ms.assetid: 953d70fa-bde9-4ce6-a55d-741e7bc63ff4
ms.openlocfilehash: 4b4fe769f78e5f826ba08d4819019210f21f860f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400481"
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