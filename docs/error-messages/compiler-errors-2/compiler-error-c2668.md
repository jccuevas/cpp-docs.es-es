---
title: Error del compilador C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: f59cb33bed15847ed1a7a2dbe99ea030babf3337
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177162"
---
# <a name="compiler-error-c2668"></a>Error del compilador C2668

' función ': llamada ambigua a una función sobrecargada

No se pudo resolver la llamada de función sobrecargada especificada. Puede que desee convertir explícitamente uno o varios parámetros reales.

También puede obtener este error a través del uso de la plantilla. Si, en la misma clase, tiene una función miembro normal y una función miembro con plantilla con la misma firma, debe aparecer primero la plantilla. Se trata de una limitación de la implementación actual de C++visual.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2668:

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

Otra manera de resolver este error es mediante una [declaración Using](../../cpp/using-declaration.md):

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

Este error también se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: conversión ambigua en la conversión de constante 0.

La conversión en una conversión con la constante 0 es ambigua, ya que int requiere una conversión tanto a Long como a void *. Para resolver este error, convierta 0 al tipo exacto del parámetro de función para el que se usa para que no sea necesario realizar ninguna conversión (este código será válido en las versiones de Visual Studio .NET 2003 y Visual Studio .NET de Visual C++).

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

Este error puede producirse porque CRT ahora tiene formatos float y Double de todas las funciones matemáticas.

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

Este error puede producirse porque se ha quitado Pow (int, int) de Math. h en CRT.

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>Ejemplo

Este código se ejecuta correctamente en Visual Studio 2015, pero produce un error en Visual Studio 2017 y versiones posteriores con C2668. En Visual Studio 2015, el compilador trataba erróneamente la inicialización de lista de copia como si fuera inicialización de copia regular; solo consideraba la conversión de constructores para la resolución de sobrecarga.

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
