---
title: Error del compilador C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 1d3078614ff6818dd4185b3bd5ed2f49413db16f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755959"
---
# <a name="compiler-error-c3609"></a>Error del compilador C3609

'member': una función sealed o final debe ser virtual

Las palabras clave [Sealed](../../extensions/sealed-cpp-component-extensions.md) y [final](../../cpp/final-specifier.md) solo se permiten en una función de clase, struct o miembro marcada como `virtual`.

El ejemplo siguiente genera el error C3609:

```cpp
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
