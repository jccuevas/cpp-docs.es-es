---
title: Error del compilador C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 0816fcb4d9e2a3e6588dfcf937383fed7ab11395
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737132"
---
# <a name="compiler-error-c2530"></a>Error del compilador C2530

' Identifier ': se deben inicializar las referencias

Debe inicializar una referencia cuando se declaró, a menos que ya esté declarada:

- Con la palabra clave [extern](../../cpp/using-extern-to-specify-linkage.md).

- Como miembro de una clase, estructura o unión (y se inicializa en el constructor).

- Como parámetro en una declaración o definición de función.

- Como el tipo de valor devuelto de una función.

En el ejemplo siguiente se genera C2530:

```cpp
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```
