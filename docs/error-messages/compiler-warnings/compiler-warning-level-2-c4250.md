---
title: Advertencia del compilador (nivel 2) C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: e0feb1cb7131b4388c87213a85ff1c921f636e1b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162041"
---
# <a name="compiler-warning-level-2-c4250"></a>Advertencia del compilador (nivel 2) C4250

' Class1 ': hereda ' clase2:: Member ' mediante dominación

Dos o más miembros tienen el mismo nombre. El de `class2` se hereda porque es una clase base para las demás clases que contenían este miembro.

Para suprimir C4250, use la pragma [Warning](../../preprocessor/warning.md) .

Dado que una clase base virtual se comparte entre varias clases derivadas, un nombre en una clase derivada domina un nombre en una clase base. Por ejemplo, dada la siguiente jerarquía de clases, hay dos definiciones de FUNC heredadas en el rombo: la instancia de VBC:: FUNC () a través de la clase débil y la dominante:: FUNC () a través de la clase dominante. Una llamada incompleta de FUNC () a través de un objeto de clase de rombo, siempre llama a la instancia de dominate:: FUNC ().  Si la clase débil fuera a introducir una instancia de FUNC (), ninguna definición dominaría y la llamada se marcaría como ambigua.

```cpp
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

En el ejemplo siguiente se genera C4250.

```cpp
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

Este ejemplo muestra una situación más compleja. En el ejemplo siguiente se genera C4250.

```cpp
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
