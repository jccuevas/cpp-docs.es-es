---
title: Error del compilador C2679
ms.date: 11/04/2016
f1_keywords:
- C2679
helpviewer_keywords:
- C2679
ms.assetid: 1a5f9d00-9190-4aa6-bc72-949f68ec136f
ms.openlocfilehash: 2b9238493e7925f2786df2acb7ecad80eb6ca2eb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760327"
---
# <a name="compiler-error-c2679"></a>Error del compilador C2679

' Operator ' binario: no se encontró ningún operador que adopte un operando en la parte derecha del tipo ' type ' (o bien no existe una conversión aceptable)

Para usar este operador, debe sobrecargarlo para el tipo especificado o definir una conversión a un tipo para el que esté definido el operador.

En el ejemplo siguiente se genera C2679:

```cpp
// C2679.cpp
class C {
public:
   C();   // no constructor with an int argument
} c;

class D {
public:
   D(int) {}
   D(){}
} d;

int main() {
   c = 10;   // C2679
   d = 10;   // OK
}
```
