---
title: Error del compilador C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d39f737ba02f3fa9c9d5f61594ddf730db6739a5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760665"
---
# <a name="compiler-error-c2803"></a>Error del compilador C2803

' operator Operator ' debe tener al menos un parámetro formal de tipo de clase

El operador sobrecargado no tiene un parámetro de tipo de clase.

Debe pasar al menos un parámetro por referencia (sin usar punteros, pero referencias) o por valor para poder escribir "a < b" (a y b de tipo clase A).

Si ambos parámetros son punteros, será una comparación pura de las direcciones de puntero y no usará la conversión definida por el usuario.

En el ejemplo siguiente se genera C2803:

```cpp
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```
