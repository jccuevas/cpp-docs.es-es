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
ms.openlocfilehash: 6c1c91aec7d974836b1ec031a1e8b38e8abb65ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399088"
---
# <a name="decltype--c"></a>decltype (C++)

El **decltype** especificador de tipo produce el tipo de una expresión especificada. El **decltype** especificador, de tipo junto con el [palabra clave auto](../cpp/auto-cpp.md), es útil principalmente para los desarrolladores que crean bibliotecas de plantillas. Use **automática** y **decltype** para declarar una función de plantilla cuyo valor devuelto tipo depende de los tipos de sus argumentos de plantilla. O bien, use **automática** y **decltype** para declarar una función de plantilla que contiene una llamada a otra función y, a continuación, devuelve el tipo de valor devuelto de la función encapsulada.

## <a name="syntax"></a>Sintaxis

```
decltype( expression )
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*expression*|Una expresión. Para obtener más información, consulte [expresiones](../cpp/expressions-cpp.md).|

## <a name="return-value"></a>Valor devuelto

El tipo de la *expresión* parámetro.

## <a name="remarks"></a>Comentarios

El **decltype** especificador de tipo se admite en Visual C++ 2010 o versiones posteriores y se puede usar con código nativo o administrado. `decltype(auto)` (C++14) se admite en Visual Studio de 2015 y versiones posteriores.

El compilador usa las siguientes reglas para determinar el tipo de la *expresión* parámetro.

- Si el *expresión* parámetro es un identificador o un [acceso a miembros de clase](../cpp/member-access-operators-dot-and.md), `decltype(expression)` es el tipo de entidad designado por *expresión*. Si no hay ninguna entidad o la *expresión* parámetro designa un conjunto de funciones sobrecargadas, el compilador produce un mensaje de error.

- Si el *expresión* parámetro es una llamada a una función o un operador sobrecargado, `decltype(expression)` es el tipo de valor devuelto de la función. Los paréntesis alrededor de un operador sobrecargado se omiten.

- Si el *expresión* parámetro es un [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` es el tipo de *expresión*. Si el *expresión* parámetro es un [lvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` es un [referencia lvalue](../cpp/lvalue-reference-declarator-amp.md) al tipo de *expresión*.

En el ejemplo de código siguiente se muestra algunos usos de la **decltype** especificador de tipo. En primer lugar, suponga que ha incluido las siguientes instrucciones en el código.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

A continuación, examine los tipos devueltos por los cuatro **decltype** instrucciones en la tabla siguiente.

|Instrucción|Tipo|Notas|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|Un [referencia rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) a un **const int**.|
|`decltype(var);`|**int**|El tipo de variable `var`.|
|`decltype(a->x);`|**double**|El tipo del acceso a miembros.|
|`decltype((a->x));`|`const double&`|Los paréntesis internos hacen que la instrucción se evalúe como una expresión en lugar de como un acceso a miembros. Y dado que `a` se declara como un `const` puntero, el tipo es una referencia a **doble const**.|

## <a name="decltype-and-auto"></a>Decltype y Auto

En C ++ 14, puede usar `decltype(auto)` con ningún tipo de valor devuelto final para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla.

En C ++ 11, puede usar el **decltype** especificador en un tipo de valor devuelto final, de tipo junto con el **automática** palabra clave, para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de su plantilla argumentos. Considere, por ejemplo el ejemplo de código siguiente en el que el tipo de valor devuelto de la función de plantilla depende de los tipos de los argumentos de plantilla. En el ejemplo de código, el *desconocido* marcador de posición indica que no se puede especificar el tipo de valor devuelto.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

La introducción de la **decltype** especificador de tipo permite que un desarrollador obtener el tipo de la expresión que devuelve la función de plantilla. Use la *sintaxis de declaración de función alternativa* que se muestra más adelante, el **automática** palabra clave y el **decltype** escriba especificador para declarar un  *en tiempo de ejecución especificado* tipo de valor devuelto. El tipo de valor devuelto especificado en tiempo de compilación se determina cuando se compila la declaración, en lugar de cuando se codifica.

El prototipo siguiente muestra la sintaxis de una declaración de función alternativa. Tenga en cuenta que el **const** y **volátil** calificadores y el **throw** [especificación de excepción](../cpp/exception-specifications-throw-cpp.md) son opcionales. El *function_body* marcador de posición representa una instrucción compuesta que especifica lo que hace la función. Como procedimiento recomendado, de codificación el *expresión* marcador de posición en el **decltype** instrucción debe coincidir con la expresión especificada por el **devolver** instrucción, si existe alguno, en el *function_body*.

**Auto** *function_name* **(** *parámetros*<sub>opt</sub> **)**  **Const**<sub>opt</sub> **volátil**<sub>opt</sub> **->** **decltype (** *expresión* **)** **throw**<sub>opt</sub> **{** *function_body* **};**

En el ejemplo de código siguiente, el tipo de valor devuelto especificado en tiempo de compilación de la función de plantilla `myFunc` viene determinado por los tipos de los argumentos de plantilla `t` y `u`. Como práctica de codificación, el ejemplo de código también usa las referencias rvalue y `forward` plantilla de función, que son compatibles con *el reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

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

En este escenario, no se puede escribir una expresión de tipo adecuada sin el **decltype** especificador de tipo. El **decltype** especificador de tipo permite funciones de reenvío genéricas porque no pierde la información necesaria sobre si una función devuelve un tipo de referencia. Para obtener un ejemplo de código de una función de reenvío, vea el ejemplo anterior de la función de plantilla `myFunc`.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se declara el tipo de valor devuelto especificado en tiempo de compilación de la función de plantilla `Plus()`. El `Plus` función procesa sus operandos con el **operator +** sobrecargar. Por consiguiente, la interpretación de operador más (+) y el tipo de valor devuelto de la función `Plus` depende de los tipos de los argumentos de la función.

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

**Visual Studio 2017 y versiones posterior:** El compilador analiza argumentos decltype cuando las plantillas se declara en lugar de crear una instancia. Por consiguiente, si se detecta una especialización no dependiente en el argumento decltype, no se aplaza hasta el momento de la creación de instancias, sino que se procesa inmediatamente y los errores resultantes se diagnostican en ese momento.

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

Visual C++ 2010 o versiones posteriores.

`decltype(auto)` requiere Visual Studio 2015 o posterior.