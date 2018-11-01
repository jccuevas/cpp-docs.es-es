---
title: Error del compilador C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: 1920af8873578c63ab768dae4bcdf4d91fe7cd57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642230"
---
# <a name="compiler-error-c2668"></a>Error del compilador C2668

'function': llamada ambigua a una función sobrecargada

No se pudo resolver la llamada de función sobrecargada especificada. Es posible que desee convertir explícitamente uno o varios de los parámetros reales.

También puede obtener este error mediante el uso de la plantilla. En la misma clase, si tiene una función miembro normal y una función miembro con plantilla con la misma firma, alguna debe aparecer en primer lugar. Esta es una limitación de la implementación actual de Visual C++.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2668:

```cpp
// C2668.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};

void func( X, X ){}
void func( A, B ){}
D d;
int main() {
   func( d, d );   // C2668 D has an A, B, and X
   func( (X)d, (X)d );   // OK, uses func( X, X )
}
```

## <a name="example"></a>Ejemplo

Es otra manera de resolver este error con un [mediante declaración](../../cpp/using-declaration.md):

```cpp
// C2668b.cpp
// compile with: /EHsc /c
// C2668 expected
#include <iostream>
class TypeA {
public:
   TypeA(int value) {}
};

class TypeB {
   TypeB(int intValue);
   TypeB(double dbValue);
};

class TestCase {
public:
   void AssertEqual(long expected, long actual, std::string
                    conditionExpression = "");
};

class AppTestCase : public TestCase {
public:
   // Uncomment the following line to resolve.
   // using TestCase::AssertEqual;
   void AssertEqual(const TypeA expected, const TypeA actual,
                    std::string conditionExpression = "");
   void AssertEqual(const TypeB expected, const TypeB actual,
                    std::string conditionExpression = "");
};

class MyTestCase : public AppTestCase {
   void TestSomething() {
      int actual = 0;
      AssertEqual(0, actual, "Value");
   }
};
```

## <a name="example"></a>Ejemplo

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio .NET 2003: conversión ambigua de la constante 0.

La conversión mediante la constante 0 es ambigua, ya que int requiere conversiones a long y void *. Para resolver este error, convierta 0 para el tipo exacto del parámetro de función que se usa para por lo que ninguna conversión debe tener lugar (este código será válido en las versiones de Visual Studio .NET 2003 y Visual Studio .NET de Visual C++).

```cpp
// C2668c.cpp
#include "stdio.h"
void f(long) {
   printf_s("in f(long)\n");
}
void f(void*) {
   printf_s("in f(void*)\n");
}
int main() {
   f((int)0);   // C2668

   // OK
   f((long)0);
   f((void*)0);
}
```

## <a name="example"></a>Ejemplo

Este error puede producirse porque el CRT tiene ahora formas float y double de todas las funciones matemáticas.

```cpp
// C2668d.cpp
#include <math.h>
int main() {
   int i = 0;
   float f;
   f = cos(i);   // C2668
   f = cos((float)i);   // OK
}
```

## <a name="example"></a>Ejemplo

Este error puede producirse porque el pow (int, int) se ha quitado de math.h en CRT.

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>Ejemplo

Este código funciona correctamente en Visual Studio 2015, pero se produce un error en Visual Studio 2017 y versiones posteriores con C2668. En Visual Studio 2015, el compilador trataba erróneamente la inicialización de lista de copia como si fuera inicialización de copia regular; solo consideraba la conversión de constructores para la resolución de sobrecarga.

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```