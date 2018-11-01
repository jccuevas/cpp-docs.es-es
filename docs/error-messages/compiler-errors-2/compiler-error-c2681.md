---
title: Error del compilador C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: 8b311052d3a3525090d954c0dc8cee20e985b1b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632705"
---
# <a name="compiler-error-c2681"></a>Error del compilador C2681

'type': tipo de expresión no válida para el nombre

Un operador de conversión intentó convertir de un tipo no válido. Por ejemplo, si usa el [dynamic_cast](../../cpp/dynamic-cast-operator.md) para convertir una expresión en un tipo de puntero, la expresión de origen debe ser un puntero.

El ejemplo siguiente genera C2681:

```
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```