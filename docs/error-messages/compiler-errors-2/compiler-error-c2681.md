---
title: Error del compilador C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: d7cf39e89f70f27471fb3a251aac12793f1fb33b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760301"
---
# <a name="compiler-error-c2681"></a>Error del compilador C2681

' type ': tipo de expresión no válido para el nombre

Un operador de conversión intentó convertir de un tipo no válido. Por ejemplo, si usa el operador [dynamic_cast](../../cpp/dynamic-cast-operator.md) para convertir una expresión en un tipo de puntero, la expresión de origen debe ser un puntero.

En el ejemplo siguiente se genera C2681:

```cpp
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```
