---
title: decltype (C++)
ms.date: 11/04/2016
f1_keywords:
- decltype_cpp
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
ms.openlocfilehash: 1ed07b8987df7b621ea2809409069cc1121fa24f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180217"
---
# <a name="decltype--c"></a>decltype (C++)

El especificador de tipo **decltype** produce el tipo de una expresión especificada. El especificador de tipo **decltype** , junto con la [palabra clave auto](../cpp/auto-cpp.md), resulta útil principalmente para los desarrolladores que escriben bibliotecas de plantillas. Use **auto** y **decltype** para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla. O bien, use **auto** y **decltype** para declarar una función de plantilla que contiene una llamada a otra función y, a continuación, devuelve el tipo de valor devuelto de la función ajustada.

## <a name="syntax"></a>Sintaxis

```
decltype( expression )
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*expression*|Expresión. Para obtener más información, vea [expresiones](../cpp/expressions-cpp.md).|

## <a name="return-value"></a>Valor devuelto

Tipo del parámetro de *expresión* .

## <a name="remarks"></a>Observaciones

El especificador de tipo **decltype** es compatible con Visual Studio 2010 o versiones posteriores, y se puede usar con código nativo o administrado. `decltype(auto)` (C++14) se admite en Visual Studio de 2015 y versiones posteriores.

El compilador usa las siguientes reglas para determinar el tipo del parámetro *Expression* .

- Si el parámetro *Expression* es un identificador o un [acceso de miembro de clase](../cpp/member-access-operators-dot-and.md), `decltype(expression)` es el tipo de la entidad denominada by *Expression*. Si no hay tal entidad o el parámetro de *expresión* nombra un conjunto de funciones sobrecargadas, el compilador produce un mensaje de error.

- Si el parámetro *Expression* es una llamada a una función o una función de operador sobrecargada, `decltype(expression)` es el tipo de valor devuelto de la función. Los paréntesis alrededor de un operador sobrecargado se omiten.

- Si el parámetro de *expresión* es un valor [r](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` es el tipo de *expresión*. Si el parámetro de *expresión* es un valor [l](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` es una referencia de valor [l](../cpp/lvalue-reference-declarator-amp.md) al tipo de *expresión*.

En el ejemplo de código siguiente se muestran algunos usos del especificador de tipo **decltype** . En primer lugar, suponga que ha incluido las siguientes instrucciones en el código.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

A continuación, examine los tipos devueltos por las cuatro instrucciones **decltype** en la tabla siguiente.

|.|Tipo|Notas|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|Referencia a un valor [r](../cpp/rvalue-reference-declarator-amp-amp.md) a **const int**.|
|`decltype(var);`|**int**|El tipo de variable `var`.|
|`decltype(a->x);`|**double**|El tipo del acceso a miembros.|
|`decltype((a->x));`|`const double&`|Los paréntesis internos hacen que la instrucción se evalúe como una expresión en lugar de como un acceso a miembros. Y como `a` se declara como un puntero `const`, el tipo es una referencia a **const Double**.|

## <a name="decltype-and-auto"></a>Decltype y Auto

En C++ 14, puede usar `decltype(auto)` sin ningún tipo de valor devuelto final para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla.

En C++ 11, puede usar el especificador de tipo **decltype** en un tipo de valor devuelto final, junto con la palabra clave **auto** , para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla. Considere, por ejemplo el ejemplo de código siguiente en el que el tipo de valor devuelto de la función de plantilla depende de los tipos de los argumentos de plantilla. En el ejemplo de código, el marcador de posición *Unknown* indica que no se puede especificar el tipo de valor devuelto.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

La introducción del especificador de tipo **decltype** permite a un desarrollador obtener el tipo de la expresión que devuelve la función de plantilla. Use la *Sintaxis de declaración de función alternativa* que se muestra más adelante, la palabra clave **auto** y el especificador de tipo **decltype** para declarar un tipo de valor devuelto *especificado en tiempo de ejecución* . El tipo de valor devuelto especificado en tiempo de compilación se determina cuando se compila la declaración, en lugar de cuando se codifica.

El prototipo siguiente muestra la sintaxis de una declaración de función alternativa. Tenga en cuenta que los calificadores **const** y **volatile** , y la especificación **Throw** [Exception](../cpp/exception-specifications-throw-cpp.md) son opcionales. El marcador de posición *function_body* representa una instrucción compuesta que especifica lo que hace la función. Como práctica recomendada de codificación, el marcador de posición de *expresión* en la instrucción **decltype** debe coincidir con la expresión especificada por la instrucción **Return** , si existe, en el *function_body*.

**auto** *function_name* **(** *parámetros*<sub>OPC</sub> **)** **const**<sub>OPC</sub> **volatile**<sub>OPC</sub> **->** **decltype (** *expresión* **)** **Throw**<sub>OPT</sub> **{** *function_body* **};**

En el ejemplo de código siguiente, el tipo de valor devuelto especificado en tiempo de compilación de la función de plantilla `myFunc` viene determinado por los tipos de los argumentos de plantilla `t` y `u`. Como práctica recomendada de codificación, en el ejemplo de código también se utilizan referencias rvalue y la plantilla de función `forward`, que admiten el *reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

```cpp
//C++11
template<typename T, typename U>
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))
        { return forward<T>(t) + forward<U>(u); };

//C++14
template<typename T, typename U>
decltype(auto) myFunc(T&& t, U&& u)
        { return forward<T>(t) + forward<U>(u); };
```

## <a name="decltype-and-forwarding-functions-c11"></a>Funciones de reenvío y decltype (C++11)

Las funciones de reenvío encapsulan llamadas a otras funciones. Considere una plantilla de función que reenvía sus argumentos, o los resultados de una expresión en la que participan estos argumentos, a otra función. Además, la función de reenvío devuelve el resultado de la llamada a otra función. En este escenario, el tipo de valor devuelto de la función de reenvío debe ser el mismo que el tipo de valor devuelto de la función encapsulada.

En este escenario, no se puede escribir una expresión de tipo adecuada sin el especificador de tipo **decltype** . El especificador de tipo **decltype** habilita las funciones de reenvío genéricas porque no pierde información necesaria sobre si una función devuelve un tipo de referencia. Para obtener un ejemplo de código de una función de reenvío, vea el ejemplo anterior de la función de plantilla `myFunc`.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se declara el tipo de valor devuelto especificado en tiempo de compilación de la función de plantilla `Plus()`. La función `Plus` procesa sus dos operandos con **Operator +** Overload. Por consiguiente, la interpretación de operador más (+) y el tipo de valor devuelto de la función `Plus` depende de los tipos de los argumentos de la función.

```cpp
// decltype_1.cpp
// compile with: cl /EHsc decltype_1.cpp

#include <iostream>
#include <string>
#include <utility>
#include <iomanip>

using namespace std;

template<typename T1, typename T2>
auto Plus(T1&& t1, T2&& t2) ->
   decltype(forward<T1>(t1) + forward<T2>(t2))
{
   return forward<T1>(t1) + forward<T2>(t2);
}

class X
{
   friend X operator+(const X& x1, const X& x2)
   {
      return X(x1.m_data + x2.m_data);
   }

public:
   X(int data) : m_data(data) {}
   int Dump() const { return m_data;}
private:
   int m_data;
};

int main()
{
   // Integer
   int i = 4;
   cout <<
      "Plus(i, 9) = " <<
      Plus(i, 9) << endl;

   // Floating point
   float dx = 4.0;
   float dy = 9.5;
   cout <<
      setprecision(3) <<
      "Plus(dx, dy) = " <<
      Plus(dx, dy) << endl;

   // String
   string hello = "Hello, ";
   string world = "world!";
   cout << Plus(hello, world) << endl;

   // Custom type
   X x1(20);
   X x2(22);
   X x3 = Plus(x1, x2);
   cout <<
      "x3.Dump() = " <<
      x3.Dump() << endl;
}
```

```Output
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```

## <a name="example"></a>Ejemplo

**Visual Studio 2017 y versiones posteriores:** El compilador analiza los argumentos de decltype cuando se declaran las plantillas en lugar de crear una instancia. Por consiguiente, si se detecta una especialización no dependiente en el argumento decltype, no se aplaza hasta el momento de la creación de instancias, sino que se procesa inmediatamente y los errores resultantes se diagnostican en ese momento.

En el ejemplo siguiente se muestra este tipo de error del compilador que se genera en el punto de declaración:

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>Requisitos

Visual Studio 2010 o versiones posteriores.

`decltype(auto)` requiere Visual Studio 2015 o posterior.
