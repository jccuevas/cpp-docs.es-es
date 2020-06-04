---
title: Error del compilador C2327
ms.date: 11/04/2016
f1_keywords:
- C2327
helpviewer_keywords:
- C2327
ms.assetid: 95278c95-d1f9-4487-ad27-53311f5e8112
ms.openlocfilehash: 36222b8469f5a51254c6a6172e20384ebafc89ab
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747779"
---
# <a name="compiler-error-c2327"></a>Error del compilador C2327

' Symbol ': no es un nombre de tipo, static o Enumerator

El código de una clase anidada intenta tener acceso a un miembro de la clase envolvente que no es un nombre de tipo, un miembro estático o un enumerador.

Al compilar con **/CLR**, una causa común de C2327 es una propiedad con el mismo nombre que el tipo de propiedad.

En el ejemplo siguiente se genera C2327:

```cpp
// C2327.cpp
int x;
class enclose {
public:
   int x;
   static int s;
   class inner {
      void f() {
         x = 1;   // C2327; enclose::x is not static
         s = 1;   // ok; enclose::s is static
         ::x = 1;   // ok; ::x refers to global
      }
   };
};
```

C2327 también se puede producir si el nombre de un tipo está oculto por el nombre de un miembro:

```cpp
// C2327b.cpp
class X {};

class S {
   X X;
   // try the following line instead
   // X MyX;
   X other;   // C2327, rename member X
};
```

C2327 también se puede activar en esta situación, donde es necesario especificar por completo el tipo de datos del parámetro:

```cpp
// C2327c.cpp
// compile with: /c
struct A {};

struct B {
   int A;
   void f(A a) {   // C2327
   void f2(struct A a) {}   // OK
   }
};
```

En el ejemplo siguiente se genera C2327:

```cpp
// C2327d.cpp
// compile with: /clr /c
using namespace System;

namespace NA {
   public enum class E : Int32 {
      one = 1,
      two = 2,
      three = 3
   };

   public ref class A {
   private:
      E m_e;
   public:
      property E E {
         NA::E get() {
            return m_e;
         }
         // At set, compiler doesn't know whether E is get_E or
         // Enum E, therefore fully qualifying Enum E is necessary
         void set( E e ) {   // C2327
            // try the following line instead
            // void set(NA::E e) {
            m_e = e;
         }
      }
   };
}
```

En el ejemplo siguiente se muestra C2327 cuando una propiedad tiene el mismo nombre que el tipo de propiedad:

```cpp
// C2327f.cpp
// compile with: /clr /c
public value class Address {};

public ref class Person {
public:
   property Address Address {
      ::Address get() {
         return address;
      }
      void set(Address addr) {   // C2327
      // try the following line instead
      // set(::Address addr) {
         address = addr;
      }
   }
private:
   Address address;   // C2327
   // try the following line instead
   // ::Address address;
};
```
