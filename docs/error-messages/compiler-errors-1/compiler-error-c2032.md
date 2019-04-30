---
title: Error del compilador C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: 5743aba880f23d7706940936fc4a3a1973a84ca1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400518"
---
# <a name="compiler-error-c2032"></a>Error del compilador C2032

'identifier': función no puede ser miembro del struct/union 'estructuraounión'

La estructura o unión tiene una función miembro, que se admite en C++, pero no en C. Para resolver el error, compile como un programa de C++ o quite la función miembro.

El ejemplo siguiente genera C2032:

```
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

Posible resolución:

```
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```