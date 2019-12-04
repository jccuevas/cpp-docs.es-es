---
title: Error del compilador C2533
ms.date: 11/04/2016
f1_keywords:
- C2533
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
ms.openlocfilehash: b111448e7e9d8260a5101d05996a670013936894
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746414"
---
# <a name="compiler-error-c2533"></a>Error del compilador C2533

'identificador': los constructores no permiten un tipo de valor devuelto

Un constructor no puede tener un tipo de valor devuelto (ni siquiera un tipo de valor devuelto `void`).

Una causa común de este error es la ausencia de un punto y coma entre el final de una definición de clase y la primera implementación de constructor. El compilador ve la clase como una definición del tipo de valor devuelto para la función de constructor y genera C2533.

El ejemplo siguiente genera el error C2533 y muestra cómo corregirlo:

```cpp
// C2533.cpp
// compile with: /c
class X {
public:
   X();
};

int X::X() {}   // C2533 - constructor return type not allowed
X::X() {}   // OK - fix by using no return type
```
