---
title: Error del compilador C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: d20bc61df2d0bab9115768b3bc0589f11a9bcdb9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302099"
---
# <a name="compiler-error-c2032"></a>Error del compilador C2032

' Identifier ': la función no puede ser miembro de struct/union ' structorunion '

La estructura o Unión tiene una función miembro, que se permite en C++ pero no en C. Para resolver el error, compile como un C++ programa o quite la función miembro.

En el ejemplo siguiente se genera C2032:

```c
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

Solución posible:

```c
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```
