---
title: Error del compilador C2533
ms.date: 11/04/2016
f1_keywords:
- C2533
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
ms.openlocfilehash: 00cb13d1999b00dfcaa5a2bc7bfb3b8eb16af5f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661882"
---
# <a name="compiler-error-c2533"></a>Error del compilador C2533

'identificador': los constructores no permiten un tipo de valor devuelto

Un constructor no puede tener un tipo de valor devuelto (ni siquiera un tipo de valor devuelto `void`).

Una causa común de este error es la ausencia de un punto y coma entre el final de una definición de clase y la primera implementación de constructor. El compilador ve la clase como una definición del tipo de valor devuelto para la función de constructor y genera C2533.

El ejemplo siguiente genera el error C2533 y muestra cómo corregirlo:

```
// C2533.cpp
// compile with: /c
class X {
public:
   X();
};

int X::X() {}   // C2533 - constructor return type not allowed
X::X() {}   // OK - fix by using no return type
```