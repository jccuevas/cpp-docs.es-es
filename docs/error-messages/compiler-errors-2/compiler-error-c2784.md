---
title: Error del compilador C2784
ms.date: 11/04/2016
f1_keywords:
- C2784
helpviewer_keywords:
- C2784
ms.assetid: 3d761fe2-881c-48bd-afae-e2e714e20473
ms.openlocfilehash: 906cb5d8df9fb8ac57c5d4289d77ac662ac26a92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563704"
---
# <a name="compiler-error-c2784"></a>Error del compilador C2784

'declaration' : no se pudo deducir el argumento de plantilla para 'type' de 'type'

El compilador no puede determinar un argumento de plantilla a partir de los argumentos de función proporcionados.

El siguiente ejemplo genera el error C2784 e indica cómo corregirlo:

```
// C2784.cpp
template<class T> class X {};
template<class T> void f(X<T>) {}

int main() {
   X<int> x;
   f(1);   // C2784

   // To fix it, try the following line instead
   f(x);
}
```