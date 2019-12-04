---
title: Error del compilador C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: cedee3f1e3289aaf0ea38d75b6c812b61f891435
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756128"
---
# <a name="compiler-error-c2652"></a>Error del compilador C2652

' Identifier ': constructor de copias no válido: el primer parámetro no debe ser un ' Identifier '

El primer parámetro del constructor de copias tiene el mismo tipo que la clase, estructura o Unión para el que se define. El primer parámetro puede ser una referencia al tipo, pero no el propio tipo.

En el ejemplo siguiente se genera C2651:

```cpp
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```
