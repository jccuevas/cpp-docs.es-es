---
title: Error del compilador C2440
ms.date: 03/28/2017
f1_keywords:
- C2440
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
ms.openlocfilehash: 8de433361901b5d247616c154afc48d637373d43
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448029"
---
# <a name="compiler-error-c2440"></a>Error del compilador C2440

'conversion': no se puede convertir de 'tipo1' a 'tipo2'

El compilador no puede realizar la conversión de `type1` a `type2`.

## <a name="example"></a>Ejemplo

C2440 puede producirse si se intenta inicializar una variable que no sea const `char*` (o `wchar_t*`) mediante el uso de un literal de cadena de código de C++, cuando la opción de conformidad del compilador [/Zc: strictstrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) está establecido. En C, el tipo de un literal de cadena es matriz de `char`, pero en C++, es una matriz de `const char`. Este ejemplo genera el error C2440:

```cpp
// C2440s.cpp
// Build: cl /Zc:strictStrings /W3 C2440s.cpp
// When built, the compiler emits:
// error C2440: 'initializing' : cannot convert from 'const char [5]'
// to 'char *'
//        Conversion from string literal loses const qualifier (see
// /Zc:strictStrings)

int main() {
   char* s1 = "test"; // C2440
   const char* s2 = "tests"; // OK
}
```

## <a name="example"></a>Ejemplo

El error C2440 también puede producirse si intenta convertir un puntero a miembro a void *. El ejemplo siguiente genera el error C2440:

```cpp
// C2440.cpp
class B {
public:
   void  f(){;}

   typedef void (B::*pf)();

   void f2(pf pf) {
       (this->*pf)();
       void* pp = (void*)pf;   // C2440
   }

   void f3() {
      f2(f);
   }
};
```

## <a name="example"></a>Ejemplo

El error C2440 también puede producirse si se intenta realizar la conversión de un tipo que se declara solo hacia delante pero no se define. Este ejemplo genera el error C2440:

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}
```

## <a name="example"></a>Ejemplo

Los errores C2440 en las líneas 15 y 16 del ejemplo siguiente se califican con el `Incompatible calling conventions for UDT return value` mensaje. Un *UDT* es un tipo definido por el usuario, como una clase, struct o unión. Estos tipos de errores de incompatibilidad se producen cuando la convención de llamada de un UDT especificado en el tipo de valor devuelto de una declaración hacia delante entra en conflicto con la convención de llamada real del UDT y cuando hay implicado un puntero de función.

En el ejemplo, en primer lugar hay declaraciones adelantadas para struct y para una función que devuelve struct; el compilador supone que struct utiliza la convención de llamada de C++. A continuación está la definición de struct, que, de forma predeterminada, usa el C convención de llamada. Dado que el compilador no conoce la convención de llamada de struct hasta que termine de leer el struct completo, la convención de llamada de struct en el tipo de valor devuelto de `get_c2` también se supone que es C++.

Struct tiene detrás otra declaración de función que devuelve struct, pero en este momento, el compilador sabe que la convención de llamada es C++. De igual forma, el puntero de función que devuelve struct, se define después de la definición de struct para que el compilador sepa que struct utiliza la convención de llamada de C++.

Para resolver el error C2440 producido a consecuencia de convenciones de llamada incompatibles, declare funciones que devuelvan un UDT después de la definición de UDT.

```cpp
// C2440b.cpp
struct MyStruct;

MyStruct get_c1();

struct MyStruct {
   int i;
   static MyStruct get_C2();
};

MyStruct get_C3();

typedef MyStruct (*FC)();

FC fc1 = &get_c1;   // C2440, line 15
FC fc2 = &MyStruct::get_C2;   // C2440, line 16
FC fc3 = &get_C3;

class CMyClass {
public:
   explicit CMyClass( int iBar)
      throw()   {
   }

   static CMyClass get_c2();
};

int main() {
   CMyClass myclass = 2;   // C2440
   // try one of the following
   // CMyClass myclass{2};
   // CMyClass myclass(2);

   int *i;
   float j;
   j = (float)i;   // C2440, cannot cast from pointer to int to float
}
```

## <a name="example"></a>Ejemplo

El error C2440 también puede producirse si se asigna el valor cero a un puntero interior:

```cpp
// C2440c.cpp
// compile with: /clr
int main() {
   array<int>^ arr = gcnew array<int>(100);
   interior_ptr<int> ipi = &arr[0];
   ipi = 0;   // C2440
   ipi = nullptr;   // OK
}
```

## <a name="example"></a>Ejemplo

El error C2440 también se puede producir un uso incorrecto de una conversión definida por el usuario. Por ejemplo, cuando un operador de conversión se ha definido como `explicit`, el compilador no puede usar en una conversión implícita. Para obtener más información sobre las conversiones definidas por el usuario, consulte [conversiones definidas por el usuario (C++ / c++ / CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)). Este ejemplo genera el error C2440:

```cpp
// C2440d.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   int i;
   i = d;   // C2440
   // Uncomment the following line to resolve.
   // i = static_cast<int>(d);
}
```

## <a name="example"></a>Ejemplo

El error C2440 también se puede producir si se intenta crear una instancia de una matriz de Visual C++ cuyo tipo es un <xref:System.Array>.  Para obtener más información, consulte [matrices](../../extensions/arrays-cpp-component-extensions.md).  El ejemplo siguiente genera el error C2440:

```cpp
// C2440e.cpp
// compile with: /clr
using namespace System;
int main() {
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440
   // try the following line instead
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));
}
```

## <a name="example"></a>Ejemplo

El error C2440 también se puede producir debido a cambios en la función de atributos.  El ejemplo siguiente genera el error C2440.

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

## <a name="example"></a>Ejemplo

Microsoft C++ compilador ya no permite la [const_cast (operador)](../../cpp/const-cast-operator.md) convertir hacia abajo al código fuente que utiliza **/CLR** se compila la programación.

Para resolver el error C2440, utilice el operador de conversión correcta. Para obtener más información, consulte [operadores de conversión](../../cpp/casting-operators.md).

Este ejemplo genera el error C2440:

```cpp
// c2440g.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};
int main() {
   Derived ^d = gcnew Derived;
   Base ^b = d;
   d = const_cast<Derived^>(b);   // C2440
   d = dynamic_cast<Derived^>(b);   // OK
}
```

## <a name="example"></a>Ejemplo

El error C2440 puede producirse debido a cambios de conformidad del compilador en Visual Studio 2015 Update 3. Anteriormente, el compilador tratará incorrectamente ciertas expresiones distintas como el mismo tipo para identificar una coincidencia de plantilla para un `static_cast` operación. Ahora el compilador distingue los tipos correctamente y de código que dependía de la anterior `static_cast` comportamiento está roto. Para corregir este problema, cambie el argumento de plantilla para coincidir con el tipo de parámetro de plantilla, o usar un `reinterpret_cast` o conversión de estilo C.

Este ejemplo genera el error C2440:

```cpp
// c2440h.cpp

template<int *a>
struct S1 {};

int g;
struct S2 : S1<&g> {
};

int main()
{
    S2 s;
    static_cast<S1<&*&g>>(s); // C2440 in VS 2015 Update 3
    // This compiles correctly:
    // static_cast<S1<&g>>(s);
}

This error can appear in ATL code that uses the SINK_ENTRY_INFO macro defined in <atlcom.h>.
```

## <a name="example"></a>Ejemplo

### <a name="copy-list-initialization"></a>Inicialización de lista de copia

Visual Studio 2017 y versiones posterior correctamente provocar errores de compilador relacionados con la creación de objetos mediante listas de inicializadores que no se detectaban en Visual Studio 2015 y podían provocar bloqueos o un comportamiento en tiempo de ejecución indefinido. En C ++ 17 copia la inicialización de lista, el compilador es necesario tener en cuenta un constructor explícito para la resolución de sobrecarga, pero debe generar un error si se elige realmente esa sobrecarga.

El ejemplo siguiente se compila en Visual Studio 2015, pero no en Visual Studio 2017.

```cpp
// C2440j.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot
                         // convert from 'int' to 'const A &'
}
```

Para corregir el error, use la inicialización directa:

```cpp
// C2440k.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2{ 1 };
}
```

## <a name="example"></a>Ejemplo

### <a name="cv-qualifiers-in-class-construction"></a>Calificadores cv en la construcción de clases

En Visual Studio 2015, el compilador a veces omite incorrectamente al calificador cv al generar un objeto de clase mediante una llamada al constructor. Esto puede causar un bloqueo o un comportamiento inesperado en tiempo de ejecución. En el ejemplo siguiente se compila en Visual Studio 2015, pero genera un error del compilador en Visual Studio 2017 y versiones posteriores:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Para corregir el error, declare el operador int() como const.
