---
title: Error del compilador C2668 | Microsoft Docs
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2668
dev_langs:
- C++
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3b318c663bb036629086d0bca9a67641e3c4c4e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093758"
---
# <a name="compiler-error-c2668"></a>Error del compilador C2668

'function': llamada ambigua a una función sobrecargada

No se pudo resolver la llamada de función sobrecargada especificada. Es posible que desee convertir explícitamente uno o varios de los parámetros reales.

También puede obtener este error mediante el uso de la plantilla. En la misma clase, si tiene una función miembro normal y una función miembro con plantilla con la misma firma, alguna debe aparecer en primer lugar. Esta es una limitación de la implementación actual de Visual C++.

Consulte el artículo de Knowledge Base Q240869 para obtener más información sobre la ordenación parcial de plantillas de función.

Si va a crear un proyecto ATL que contiene un objeto COM compatible con `ISupportErrorInfo`, consulte el artículo de Knowledge Base Q243298.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2668:

```
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

```
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

```
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

```
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

```
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>Ejemplo

Este código funciona correctamente en Visual Studio 2015, pero se produce un error en Visual Studio 2017 y versiones posteriores con C2668. En Visual Studio 2015, el compilador trataba erróneamente la inicialización de lista de copia como si fuera inicialización de copia regular; solo consideraba la conversión de constructores para la resolución de sobrecarga.

```
C++
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