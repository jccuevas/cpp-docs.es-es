---
title: Error del compilador C2804
ms.date: 11/04/2016
f1_keywords:
- C2804
helpviewer_keywords:
- C2804
ms.assetid: b066e563-cca4-450c-8ba7-3b0d7a89f3ea
ms.openlocfilehash: 1ebcfdc2f2555fa694ab8dfeabe77e5140ddace2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408425"
---
# <a name="compiler-error-c2804"></a>Error del compilador C2804

'operator operator' binario tiene demasiados parámetros

La función miembro del operador binario sobrecargado se declara con más de un parámetro. El primer parámetro de operando de una función miembro de operador binario, cuyo tipo es el tipo envolvente del operador, está implícito.

## <a name="example"></a>Ejemplo

La muestra siguiente genera el error C2804 y muestra cómo corregirlo.

```
// C2804.cpp
// compile by using: cl /c /W4 C2804.cpp
class X {
public:
   X& operator+= (const X &left, const X &right);   // C2804
   X& operator+= (const X &right);   // OK - left operand implicitly *this
};

int main() {
   X x, y;
   x += y;   // equivalent to x.operator+=(y)
}
```

## <a name="example"></a>Ejemplo

La muestra siguiente genera el error C2804 y muestra cómo corregirlo.

```
// C2804_2.cpp
// compile with: /clr /c
ref struct Y {
   Y^ operator +(Y^ hY, int i);   // C2804
   static Y^ operator +(Y^ hY, int i);   // OK
   Y^ operator +(int i);   // OK
};
```