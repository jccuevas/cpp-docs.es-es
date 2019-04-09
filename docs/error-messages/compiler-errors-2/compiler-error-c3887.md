---
title: Error del compilador C3887
ms.date: 11/04/2016
f1_keywords:
- C3887
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
ms.openlocfilehash: 85434cb8daba0db82843c09e2d1bb09d98960272
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777446"
---
# <a name="compiler-error-c3887"></a>Error del compilador C3887

'var': el inicializador de un miembro de datos literal debe ser una expresión constante

Un [literal](../../extensions/literal-cpp-component-extensions.md) solo se puede inicializar el miembro de datos con una expresión constante.

El ejemplo siguiente genera C3887:

```
// C3887.cpp
// compile with: /clr
ref struct Y1 {
   static int i = 9;
   literal
   int staticConst = i;   // C3887
};
```

Posible resolución:

```
// C3887b.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   int staticConst = 9;
};
```