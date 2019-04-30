---
title: Error del compilador C2678
ms.date: 11/04/2016
f1_keywords:
- C2678
helpviewer_keywords:
- C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
ms.openlocfilehash: 9055210401e14eeb9fdb88266870ac8fe5cbd496
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395396"
---
# <a name="compiler-error-c2678"></a>Error del compilador C2678

'operator' binario: no se definió ningún operador que adopte un operando en la parte izquierda de tipo 'type' (o bien no existe una conversión aceptable)

Para usar este operador, debe sobrecargarlo para el tipo especificado o definir una conversión a un tipo para el que esté definido el operador.

## <a name="example"></a>Ejemplo

Puede producirse el error C2678 si el operando izquierdo es calificado como constante, pero el operador está definido para tomar un argumento no constante.

El siguiente ejemplo genera el error C2678 y muestra cómo corregirlo:

```
// C2678a.cpp
// Compile by using: cl /EHsc /W4 C2678a.cpp
struct Combo {
   int number;
   char letter;
};

inline Combo& operator+=(Combo& lhs, int rhs) {
   lhs.number += rhs;
   return lhs;
}

int main() {
   Combo const combo1{ 42, 'X' };
   Combo combo2{ 13, 'Z' };

   combo1 += 6; // C2678
   combo2 += 9; // OK - operator+= matches non-const Combo
}
```

## <a name="example"></a>Ejemplo

El error C2678 también se puede producir si no se ancla un miembro nativo antes de llamar a una función miembro en él.

El siguiente ejemplo genera el error C2678 y muestra cómo corregirlo.

```
// C2678.cpp
// compile with: /clr /c
struct S { int _a; };

ref class C {
public:
   void M( S param ) {
      test = param;   // C2678

      // OK
      pin_ptr<S> ptest = &test;
      *ptest = param;
   }
   S test;
};
```
