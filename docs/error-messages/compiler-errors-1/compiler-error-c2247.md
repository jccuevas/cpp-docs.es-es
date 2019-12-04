---
title: Error del compilador C2247
ms.date: 11/04/2016
f1_keywords:
- C2247
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
ms.openlocfilehash: e82b406b20d77a824b62207b1766fec55ac65c5c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758910"
---
# <a name="compiler-error-c2247"></a>Error del compilador C2247

' Identifier ' no accesible porque ' Class ' usa ' Specifier ' para heredar de ' Class '

`identifier` se hereda de una clase declarada con acceso privado o protegido.

En el ejemplo siguiente se genera C2247:

```cpp
// C2247.cpp
class A {
public:
   int i;
};
class B : private A {};    // B inherits a private A
class C : public B {} c;   // so even though C's B is public
int j = c.i;               // C2247, i not accessible
```

Este error también se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: control de acceso con miembros protegidos. Solo se puede tener acceso a un miembro protegido (n) a través de una función miembro de una clase (B) que hereda de la clase (A) de la que (n) es miembro.

Para que el código sea válido en las versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C++, declare el miembro como un elemento Friend del tipo. También se puede usar la herencia pública.

```cpp
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

C2247 también se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: las clases base privadas ahora inaccesibles. Una clase (A) que es una clase base privada a un tipo (B) no debe ser accesible para un tipo (C) que use B como clase base.

Para el código que es válido en las versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C++, use el operador ámbito.

```cpp
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
