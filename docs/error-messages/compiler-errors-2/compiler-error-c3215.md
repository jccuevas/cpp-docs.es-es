---
title: Error del compilador C3215
ms.date: 11/04/2016
f1_keywords:
- C3215
helpviewer_keywords:
- C3215
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
ms.openlocfilehash: 24f17d2990c9258168a6d37fef101c21f62cb08d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768658"
---
# <a name="compiler-error-c3215"></a>Error del compilador C3215

'type1': el parámetro de tipo genérico ya estaba restringido por 'type2'

Se especificó una restricción más de una vez.

Para más información sobre genéricos, vea [Generics](../../extensions/generics-cpp-component-extensions.md).

El ejemplo siguiente genera la advertencia C3215:

```
// C3215.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A,A
ref class C {};   // C3215
```

Posible resolución:

```
// C3215b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
where T : A
ref class C {};
```