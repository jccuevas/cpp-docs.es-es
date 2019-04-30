---
title: Error del compilador C2247
ms.date: 11/04/2016
f1_keywords:
- C2247
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
ms.openlocfilehash: ab1f83e2075128441cbffd2d939e3b99b45be4c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301375"
---
# <a name="compiler-error-c2247"></a>Error del compilador C2247

'identifier' no es accesible porque 'class' utiliza 'especificador' para heredar de 'class'

`identifier` se hereda de una clase declarada con acceso privado o protegido.

El ejemplo siguiente genera C2247:

```
// C2247.cpp
class A {
public:
   int i;
};
class B : private A {};    // B inherits a private A
class C : public B {} c;   // so even though C's B is public
int j = c.i;               // C2247, i not accessible
```

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio .NET 2003: control de acceso con miembros protegidos. Un miembro protegido (n) solo puede obtenerse a través de una función miembro de una clase (B) que hereda de la clase (A) de los cuales (n) es un miembro.

Para el código que es válido en Visual Studio .NET 2003 y en versiones de Visual Studio .NET de Visual C++, declare el miembro como friend del tipo. También se puede usar la herencia pública.

```
// C2247b.cpp
// compile with: /c
// C2247 expected
class A {
public:
   void f();
   int n;
};

class B: protected A {
   // Uncomment the following line to resolve.
   // friend void A::f();
};

void A::f() {
   B b;
   b.n;
}
```

También puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio .NET 2003 C2247: ahora clases inaccesible base privada. Una clase (A) que es una clase base privada a un tipo no (B) debe estar accesible para un tipo (C) que utiliza B como clase base.

Para el código que es válido en Visual Studio .NET 2003 y en versiones de Visual Studio .NET de Visual C++, use el operador de ámbito.

```
// C2247c.cpp
// compile with: /c
struct A {};

struct B: private A {};

struct C : B {
   void f() {
      A *p1 = (A*) this;   // C2247
      // try the following line instead
      // ::A *p2 = (::A*) this;
   }
};
```