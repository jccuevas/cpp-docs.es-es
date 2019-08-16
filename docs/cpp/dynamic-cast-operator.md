---
title: dynamic_cast (Operador)
ms.date: 11/19/2018
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 3b359885eb72f9272fb1efe14afe9a6cbe6ddb30
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399060"
---
# <a name="dynamiccast-operator"></a>dynamic_cast (Operador)

Convierte el operando `expression` en un objeto del tipo `type-id`.

## <a name="syntax"></a>Sintaxis

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>Comentarios

`type-id` debe ser un puntero o una referencia a un tipo de clase definido previamente o un "puntero a void". El tipo de `expression` debe ser un puntero si `type-id` es un puntero, o un valor L si `type-id` es una referencia.

Consulte [static_cast](../cpp/static-cast-operator.md) para obtener una explicación de la diferencia entre las conversiones estáticas y dinámicas, y cuándo es adecuado utilizar cada una.

Hay dos cambios importantes en el comportamiento de **dynamic_cast** en código administrado:

- **dynamic_cast** a un puntero al tipo subyacente de una enumeración conversión boxing producirá un error en tiempo de ejecución, devolviendo 0 en lugar del puntero convertido.

- **dynamic_cast** ya no se iniciará una excepción cuando `type-id` es un puntero interior a un tipo de valor con error en tiempo de ejecución en la conversión.  La conversión devolverá ahora el valor de puntero 0 en lugar de producirse una excepción.

Si `type-id` es un puntero a una clase base directa o indirecta accesible de forma no ambigua desde `expression`, el resultado es un puntero al subobjeto único de tipo `type-id`. Por ejemplo:

```cpp
// dynamic_cast_1.cpp
// compile with: /c
class B { };
class C : public B { };
class D : public C { };

void f(D* pd) {
   C* pc = dynamic_cast<C*>(pd);   // ok: C is a direct base class
                                   // pc points to C subobject of pd
   B* pb = dynamic_cast<B*>(pd);   // ok: B is an indirect base class
                                   // pb points to B subobject of pd
}
```

Este tipo de conversión se denomina "conversión hacia arriba" porque sube un puntero en una jerarquía de clases, desde una clase derivada a una clase de la que se deriva. Una conversión hacia arriba es una conversión implícita.

Si `type-id` es void*, se realiza una comprobación en tiempo de ejecución para determinar el tipo real de `expression`. El resultado es un puntero al objeto completo al que apunta `expression`. Por ejemplo:

```cpp
// dynamic_cast_2.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = new B;
   void* pv = dynamic_cast<void*>(pa);
   // pv now points to an object of type A

   pv = dynamic_cast<void*>(pb);
   // pv now points to an object of type B
}
```

Si `type-id` no es void*, se realiza una comprobación en tiempo de ejecución para ver si el objeto al que apunta `expression` se puede convertir al tipo indicado por `type-id`.

Si el tipo de `expression` es una clase base del tipo de `type-id`, se realiza una comprobación en tiempo de ejecución para ver si `expression` apunta realmente a un objeto completo del tipo de `type-id`. Si es cierto, el resultado es un puntero a un objeto completo del tipo de `type-id`. Por ejemplo:

```cpp
// dynamic_cast_3.cpp
// compile with: /c /GR
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   B* pb = new D;   // unclear but ok
   B* pb2 = new B;

   D* pd = dynamic_cast<D*>(pb);   // ok: pb actually points to a D
   D* pd2 = dynamic_cast<D*>(pb2);   // pb2 points to a B not a D
}
```

Este tipo de conversión se denomina "conversión hacia abajo" porque baja un puntero en una jerarquía de clases, desde una clase especificada a una clase derivada de ella.

En los casos de herencia múltiple, se introducen posibilidades de ambigüedad. Considere la jerarquía de clases que se muestra en la ilustración siguiente.

Para los tipos CLR, **dynamic_cast** da como resultado una operación sin efecto si se puede realizar la conversión implícita, o bien un MSIL `isinst` instrucción, que realiza una comprobación dinámica y devuelve **nullptr** si el se produce un error de conversión.

El ejemplo siguiente usa **dynamic_cast** para determinar si una clase es una instancia del tipo determinado:

```cpp
// dynamic_cast_clr.cpp
// compile with: /clr
using namespace System;

void PrintObjectType( Object^o ) {
   if( dynamic_cast<String^>(o) )
      Console::WriteLine("Object is a String");
   else if( dynamic_cast<int^>(o) )
      Console::WriteLine("Object is an int");
}

int main() {
   Object^o1 = "hello";
   Object^o2 = 10;

   PrintObjectType(o1);
   PrintObjectType(o2);
}
```

![Jerarquía que muestra herencia múltiple de clases](../cpp/media/vc39011.gif "jerarquía que muestra herencia múltiple de clases") <br/>
Jerarquía de clases que muestra herencia múltiple

Un puntero a un objeto de tipo `D` se puede convertir de manera segura a `B` o a `C`. Sin embargo, si `D` se convierte para que apunte a un objeto `A`, ¿qué instancia de `A` resultaría? Esto produciría un error de conversión ambigua. Para eludir este problema, puede realizar dos conversiones no ambiguas. Por ejemplo:

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   D* pd = new D;
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

Se pueden introducir más ambigüedades cuando se utilizan clases base virtuales. Considere la jerarquía de clases que se muestra en la ilustración siguiente.

![Clase de la jerarquía que muestra clases base virtuales](../cpp/media/vc39012.gif "jerarquía que muestra clases base virtuales") <br/>
Jerarquía de clases que muestra clases base virtuales

En esta jerarquía, `A` es una clase base virtual. Dada una instancia de clase `E` y un puntero a la `A` subobjeto, un **dynamic_cast** a un puntero a `B` se producirá un error debido a la ambigüedad. Primero debe convertir de nuevo al objeto `E` completo y después volver a subir por la jerarquía, de forma no ambigua, hasta llegar al objeto `B` correcto.

Considere la jerarquía de clases que se muestra en la ilustración siguiente.

![Clase de la jerarquía que muestra clases base duplicadas](../cpp/media/vc39013.gif "jerarquía que muestra clases base duplicadas") <br/>
Jerarquía de clases que muestra clases base duplicadas

Dado un objeto de tipo `E` y un puntero al subobjeto `D`, para navegar desde el subobjeto `D` hasta el subobjeto `A` situado más a la izquierda, se pueden realizar tres conversiones. Puede realizar un **dynamic_cast** la conversión de la `D` puntero a un `E` puntero y, a continuación, una conversión (ya sea **dynamic_cast** o una conversión implícita) desde `E`a `B`y, por último, una conversión implícita de `B` a `A`. Por ejemplo:

```cpp
// dynamic_cast_5.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   E* pe = dynamic_cast<E*>(pd);
   B* pb = pe;   // upcast, implicit conversion
   A* pa = pb;   // upcast, implicit conversion
}
```

El **dynamic_cast** operador también puede utilizarse para realizar una "conversión cruzada". Utilizando la misma jerarquía de clases, es posible convertir un puntero (por ejemplo, del subobjeto `B` al subobjeto `D`) siempre y cuando el objeto completo sea de tipo `E`.

Teniendo en cuenta las conversiones cruzadas, en realidad es posible efectuar la conversión de un puntero a `D` a un puntero al subobjeto `A` situado más a la izquierda en solo dos pasos. Puede realizar una conversión cruzada de `D` a `B` y después una conversión implícita de `B` a `A`. Por ejemplo:

```cpp
// dynamic_cast_6.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   B* pb = dynamic_cast<B*>(pd);   // cross cast
   A* pa = pb;   // upcast, implicit conversion
}
```

Un valor de puntero null se convierte en el valor de puntero null del tipo de destino mediante **dynamic_cast**.

Cuando se utiliza `dynamic_cast < type-id > ( expression )`, si `expression` no se puede convertir de forma segura al tipo `type-id`, la comprobación en tiempo de ejecución hace que se produzca un error en la conversión. Por ejemplo:

```cpp
// dynamic_cast_7.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = dynamic_cast<B*>(pa);   // fails at runtime, not safe;
   // B not derived from A
}
```

El valor de una conversión con errores al tipo de puntero es el puntero NULL. Una conversión con errores al tipo de referencia produce una [bad_cast (excepción)](../cpp/bad-cast-exception.md).   Si `expression` apuntan o hacen referencia a un objeto válido, no un `__non_rtti_object` es una excepción.

Consulte [typeid](../cpp/typeid-operator.md) para obtener una explicación de la `__non_rtti_object` excepción.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea el puntero de la clase base (struct A) a un objeto (struct C).  Esto, además del hecho de que hay funciones virtuales, hace posible el polimorfismo en tiempo de ejecución.

En el ejemplo también se llama a una función no virtual de la jerarquía.

```cpp
// dynamic_cast_8.cpp
// compile with: /GR /EHsc
#include <stdio.h>
#include <iostream>

struct A {
    virtual void test() {
        printf_s("in A\n");
   }
};

struct B : A {
    virtual void test() {
        printf_s("in B\n");
    }

    void test2() {
        printf_s("test2 in B\n");
    }
};

struct C : B {
    virtual void test() {
        printf_s("in C\n");
    }

    void test2() {
        printf_s("test2 in C\n");
    }
};

void Globaltest(A& a) {
    try {
        C &c = dynamic_cast<C&>(a);
        printf_s("in GlobalTest\n");
    }
    catch(std::bad_cast) {
        printf_s("Can't cast to C\n");
    }
}

int main() {
    A *pa = new C;
    A *pa2 = new B;

    pa->test();

    B * pb = dynamic_cast<B *>(pa);
    if (pb)
        pb->test2();

    C * pc = dynamic_cast<C *>(pa2);
    if (pc)
        pc->test2();

    C ConStack;
    Globaltest(ConStack);

   // will fail because B knows nothing about C
    B BonStack;
    Globaltest(BonStack);
}
```

```Output
in C
test2 in B
in GlobalTest
Can't cast to C
```

## <a name="see-also"></a>Vea también

[Operadores de conversión](../cpp/casting-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)