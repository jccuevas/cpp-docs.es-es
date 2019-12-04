---
title: Error del compilador C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: 4b1e481c733f52b0be419b7fd786b26a90362f9c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737094"
---
# <a name="compiler-error-c2534"></a>Error del compilador C2534

' Identifier ': el constructor no puede devolver un valor

Un constructor no puede devolver un valor ni tener un tipo de valor devuelto (ni siquiera un tipo de valor devuelto `void`).

Este error se puede corregir quitando la instrucción `return` de la definición del constructor.

En el ejemplo siguiente se genera C2534:

```cpp
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```
