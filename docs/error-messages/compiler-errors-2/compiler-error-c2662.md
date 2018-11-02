---
title: Error del compilador C2662
ms.date: 11/04/2016
f1_keywords:
- C2662
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
ms.openlocfilehash: fefd523ca3b9a3406afc307150322f9d431aa730
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515250"
---
# <a name="compiler-error-c2662"></a>Error del compilador C2662

'function': no se puede convertir el puntero 'this' de 'tipo1' a 'tipo2'

El compilador no pudo convertir el `this` puntero desde `type1` a `type2`.

Este error puede deberse a invocar no`const` función miembro en un `const` objeto.  Soluciones posibles:

- Quitar el `const` de la declaración del objeto.

- Agregar `const` a la función miembro.

El ejemplo siguiente genera C2662:

```
// C2662.cpp
class C {
public:
   void func1();
   void func2() const{}
} const c;

int main() {
   c.func1();   // C2662
   c.func2();   // OK
}
```

Cuando se compila con **/CLR**, no se puede llamar a una función en un `const` o `volatile` calificado tipo administrado. No se puede declarar una función miembro const de una clase administrada, por lo que no se puede llamar a métodos en objetos administrados constantes.

```
// C2662_b.cpp
// compile with: /c /clr
ref struct M {
   property M^ Type {
      M^ get() { return this; }
   }

   void operator=(const M %m) {
      M ^ prop = m.Type;   // C2662
   }
};

ref struct N {
   property N^ Type {
      N^ get() { return this; }
   }

   void operator=(N % n) {
      N ^ prop = n.Type;   // OK
   }
};
```

El ejemplo siguiente genera C2662:

```
// C2662_c.cpp
// compile with: /c
// C2662 expected
typedef int ISXVD;
typedef unsigned char BYTE;

class LXBASE {
protected:
    BYTE *m_rgb;
};

class LXISXVD:LXBASE {
public:
   // Delete the following line to resolve.
   ISXVD *PMin() { return (ISXVD *)m_rgb; }

   ISXVD *PMin2() const { return (ISXVD *)m_rgb; };   // OK
};

void F(const LXISXVD *plxisxvd, int iDim) {
   ISXVD isxvd;
   // Delete the following line to resolve.
   isxvd = plxisxvd->PMin()[iDim];

   isxvd = plxisxvd->PMin2()[iDim];
}
```