---
title: Advertencia del compilador (nivel 2) C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: 8baf3c03c87dc70a80b785d7f81cbee4e1d828f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349716"
---
# <a name="compiler-warning-level-2-c4250"></a>Advertencia del compilador (nivel 2) C4250

'class1': hereda 'clase2:: miembro' mediante dominación

Dos o más miembros tienen el mismo nombre. En `class2` es heredado, porque es una clase base para las otras clases que contiene este miembro.

Para suprimir C4250, utilice el [advertencia](../../preprocessor/warning.md) pragma.

Dado que una clase base virtual se comparte entre varias clases derivadas, un nombre en una clase derivada domina un nombre en una clase base. Por ejemplo, dada la siguiente jerarquía de clases, hay dos definiciones de funciones heredadas dentro del rombo: la instancia vbc::Func() a través de la clase débil y el dominante:: func() a través de la clase dominante. Una llamada incompleta de func() a través de un objeto de clase de rombo siempre llama a la instancia dominate:: func.  Si la clase débil fuera a introducir una instancia de func(), ni podría dominar la definición y la llamada se marcaría como ambigua.

```
// C4250.cpp
// compile with: /c /W2
#include <stdio.h>
struct vbc {
   virtual void func() { printf("vbc::func\n"); }
};

struct weak : public virtual vbc {};

struct dominant : public virtual vbc {
   void func() { printf("dominant::func\n"); }
};

struct diamond : public weak, public dominant {};

int main() {
   diamond d;
   d.func();   // C4250
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4250.

```
// C4250_b.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;
class A {
public:
   virtual operator int () {
      return 2;
   }
};

class B : virtual public A {
public:
   virtual operator int () {
      return 3;
   }
};

class C : virtual public A {};

class E : public B, public C {};   // C4250

int main() {
   E eObject;
   cout << eObject.operator int() << endl;
}
```

## <a name="example"></a>Ejemplo

En este ejemplo se muestra una situación más compleja. El ejemplo siguiente genera la advertencia C4250.

```
// C4250_c.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;

class V {
public:
   virtual int f() {
      return 1024;
   }
};

class B : virtual public V {
public:
   int b() {
      return f(); // B::b() calls V::f()
   }
};

class M : virtual public V {
public:
   int f() {
      return 7;
   }
};

// because of dominance, f() is M::f() inside D,
// changing the meaning of B::b's f() call inside a D
class D : public B, public M {};   // C4250

int main() {
   D d;
   cout << "value is: " << d.b();   // invokes M::f()
}
```