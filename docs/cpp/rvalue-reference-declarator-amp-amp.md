---
title: 'Declarador de referencia rvalue: &amp;&amp;'
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: 185c2de5dc21dd305a2792d4ee8e6baf69c35b28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331095"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Declarador de referencia rvalue: &amp;&amp;

Mantiene una referencia a una expresión de valor R.

## <a name="syntax"></a>Sintaxis

```
type-id && cast-expression
```

## <a name="remarks"></a>Comentarios

Las referencias de valor R permiten distinguir un valor L de un valor R Las referencias de valor L y valor R son sintáctica y semánticamente similares, pero siguen reglas algo distintas. Para obtener más información acerca de lvalues y rvalues, vea [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md). Para obtener más información acerca de las referencias de valor l, vea [declarador de referencia Lvalue: &](../cpp/lvalue-reference-declarator-amp.md).

Las secciones siguientes describen cómo las referencias rvalue son compatibles con la implementación de *semántica de transferencia* y *el reenvío directo*.

## <a name="move-semantics"></a>Semántica de transferencia de recursos

Referencias a valor r admiten la implementación de *semántica de transferencia*, lo que puede aumentar significativamente el rendimiento de las aplicaciones. La semántica de transferencia de recursos permite escribir código que transfiere recursos (tales como memoria asignada dinámicamente) de un objeto a otro. La semántica de transferencia de recursos funciona porque permite transferir recursos desde objetos temporales a los que no se puede hacer referencia en otra parte del programa.

Para implementar la semántica de movimiento, suelen proporcionar un *constructor de movimiento,* y, opcionalmente, un operador de asignación de movimiento (**operador =**), a la clase. Las operaciones de copia y asignación cuyos orígenes son valores R aprovechan entonces automáticamente la semántica de transferencia de recursos. A diferencia del constructor de copia predeterminado, el compilador no proporciona un constructor de movimiento predeterminado. Para obtener más información sobre cómo escribir un constructor de movimiento y cómo utilizarlo en su aplicación, consulte [constructores de movimiento y operadores de asignación de movimiento (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

También puede sobrecargar funciones y operadores normales para aprovechar la semántica de transferencia de recursos. Visual C++ 2010 presenta la semántica de movimiento en la biblioteca estándar de C++. Por ejemplo, la clase `string` implementa operaciones que realizan semántica de transferencia de recursos. Considere el ejemplo siguiente que concatena varias cadenas e imprime el resultado:

```cpp
// string_concatenation.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

int main()
{
   string s = string("h") + "e" + "ll" + "o";
   cout << s << endl;
}
```

Antes de Visual C++ 2010, con cada llamada a **operator +** asigna y devuelve un nuevo archivo temporal `string` objeto (un valor r). **operator +** no se puede anexar una cadena al otro porque no sabe si las cadenas de origen son valores l o valores r. Si las cadenas de origen son ambas valores L, puede que se haga referencia a las mismas en otra parte del programa y, por consiguiente, no se deben modificar. Mediante el uso de las referencias rvalue, **operator +** puede modificarse para que acepte valores r, que no se puede hacer referencia en otro lugar en el programa. Por lo tanto, **operator +** ahora se puede anexar una cadena a otra. Esto puede reducir significativamente el número de asignaciones de memoria dinámica que la clase `string` debe realizar. Para obtener más información sobre la `string` de clases, vea [basic_string (clase)](../standard-library/basic-string-class.md).

La semántica de transferencia de recursos también ayuda cuando el compilador no puede utilizar la optimización del valor devuelto (RVO) o la optimización del valor devuelto con nombre (NRVO). En estos casos, el compilador llama al constructor de movimiento si el tipo lo define. Para obtener más información acerca de la optimización de valor devuelto con nombre, vea [denominada optimización del valor devuelto en Visual C++ 2005](https://msdn.microsoft.com/library/ms364057.aspx).

Para entender mejor la semántica de transferencia de recursos, considere el ejemplo de la inserción de un elemento en un objeto `vector`. Si se supera la capacidad del objeto `vector`, el objeto `vector` debe reasignar memoria para sus elementos y, a continuación, copiar cada elemento en otra ubicación de memoria para dejar espacio al elemento insertado. Cuando una operación de inserción copia un elemento, crea un nuevo elemento, llama al constructor de copias para copiar los datos del elemento anterior en el nuevo elemento y, a continuación, destruye el elemento anterior. La semántica de transferencia de recursos permite mover objetos directamente sin tener que realizar una asignación de gran consumo de memoria ni operaciones de copia.

Para aprovechar la semántica de transferencia de recursos en el ejemplo `vector`, puede escribir un constructor de movimiento para mover los datos de un objeto a otro.

Para obtener más información sobre la introducción de semántica de movimiento en la biblioteca estándar de C++ en Visual C++ 2010, consulte [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md).

## <a name="perfect-forwarding"></a>Reenvío directo

El reenvío directo reduce la necesidad de funciones sobrecargadas y ayuda a evitar el problema de reenvío. El *problema de reenvío* puede producirse cuando se escribe una función genérica que acepta referencias como parámetros y pasa (o *reenvía*) estos parámetros a otra función. Por ejemplo, si la función genérica toma un parámetro de tipo `const T&`, la función llamada no puede modificar el valor de ese parámetro. Si la función genérica toma un parámetro de tipo `T&`, no se puede llamar a la función mediante un valor R (tal como un objeto temporal o un literal entero).

Normalmente, para solucionar este problema, debe proporcionar versiones sobrecargadas de la función genérica que acepten tanto `T&` como `const T&` para cada uno de sus parámetros. Como resultado, el número de funciones sobrecargadas aumenta exponencialmente con el número de parámetros. Las referencias de valor R permiten escribir una versión de una función que acepte argumentos arbitrarios y los reenvíe a otra función como si se hubiera llamado directamente a la otra función.

Considere el ejemplo siguiente en el que se declaran cuatro tipos, `W`, `X`, `Y` y `Z`. El constructor para cada tipo toma una combinación diferente de **const** y no-**const** referencias lvalue como parámetros.

```cpp
struct W
{
   W(int&, int&) {}
};

struct X
{
   X(const int&, int&) {}
};

struct Y
{
   Y(int&, const int&) {}
};

struct Z
{
   Z(const int&, const int&) {}
};
```

Supongamos que desea escribir una función genérica que genere objetos. En el siguiente ejemplo, se muestra una forma de escribir esta función:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

En el ejemplo siguiente se muestra una llamada válida a la función `factory`.

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

Sin embargo, el ejemplo siguiente no contiene una llamada válida a la función `factory` porque `factory` acepta referencias de valor L que son modificables como parámetros, pero la llamada se realiza usando valores R:

```cpp
Z* pz = factory<Z>(2, 2);
```

Normalmente, para solucionar este problema se debe crear una versión sobrecargada de la función `factory` para cada combinación de los parámetros `A&` y `const A&`. Las referencias de valor R permiten escribir una versión de la función `factory`, como se muestra en el ejemplo siguiente:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

En este ejemplo se usan referencias de valor R como parámetros para la función `factory`. El propósito de la [std:: Forward](../standard-library/utility-functions.md#forward) función es reenviar los parámetros de la función de generador al constructor de la clase de plantilla.

En el ejemplo siguiente se muestra la función `main` que usa la función `factory` revisada para crear instancias de las clases `W`, `X``Y` y `Z`. La función `factory` revisada reenvía sus parámetros (ya sean valores L o valores R) al constructor de clase adecuado.

```cpp
int main()
{
   int a = 4, b = 5;
   W* pw = factory<W>(a, b);
   X* px = factory<X>(2, b);
   Y* py = factory<Y>(a, 2);
   Z* pz = factory<Z>(2, 2);

   delete pw;
   delete px;
   delete py;
   delete pz;
}
```

## <a name="additional-properties-of-rvalue-references"></a>Propiedades adicionales de referencias de valor R

**Puede sobrecargar una función para que tome una referencia de valor l y una referencia rvalue.**

Mediante la sobrecarga de una función tome un **const** referencia lvalue o una referencia rvalue, puede escribir código que distinga entre objetos no modificables (valores l) y valores temporales modificables (valores r). Puede pasar un objeto a una función que toma una referencia rvalue, a menos que el objeto está marcado como **const**. El ejemplo siguiente muestra la función `f`, que se sobrecarga para aceptar una referencia de valor L y una referencia de valor R. La función `main` llama a `f` con ambos valores L y un valor R.

```cpp
// reference-overload.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void f(const MemoryBlock&)
{
   cout << "In f(const MemoryBlock&). This version cannot modify the parameter." << endl;
}

void f(MemoryBlock&&)
{
   cout << "In f(MemoryBlock&&). This version can modify the parameter." << endl;
}

int main()
{
   MemoryBlock block;
   f(block);
   f(MemoryBlock());
}
```

Este ejemplo produce el siguiente resultado:

```Output
In f(const MemoryBlock&). This version cannot modify the parameter.
In f(MemoryBlock&&). This version can modify the parameter.
```

En este ejemplo, la primera llamada a `f` pasa una variable local (un valor L) como argumento. La segunda llamada a `f` pasa un objeto temporal como argumento. Como no se puede hacer referencia al objeto temporal en otra parte del programa, la llamada se enlaza a la versión sobrecargada de `f` que acepta una referencia de valor R, que es libre de modificar el objeto.

**El compilador trata una referencia de valor r con nombre como un valor l y una referencia rvalue sin nombre como un valor r.**

Cuando se escribe una función que acepta una referencia de valor R como parámetro, ese parámetro se trata como un valor L en el cuerpo de la función. El compilador trata una referencia de valor R con nombre como un valor L porque se puede hacer referencia a un objeto con nombre en varias partes de un programa; sería peligroso permitir que varias partes de un programa modificaran o quitaran recursos de ese objeto. Por ejemplo, si varias partes de un programa intentan transferir recursos del mismo objeto, solo la primera parte transferirá el recurso correctamente.

El ejemplo siguiente muestra la función `g`, que se sobrecarga para aceptar una referencia de valor L y una referencia de valor R. La función `f` acepta una referencia de valor R como parámetro (una referencia de valor R con nombre) y devuelve una referencia de valor R (una referencia de valor R sin nombre). En la llamada a `g` desde `f`, la resolución de sobrecarga selecciona la versión de `g` que acepta una referencia de valor L porque el cuerpo de `f` considera el parámetro como un valor L. En la llamada a `g` desde `main`, la resolución de sobrecarga selecciona la versión de `g` que acepta una referencia de valor R porque `f` devuelve una referencia de valor R.

```cpp
// named-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

MemoryBlock&& f(MemoryBlock&& block)
{
   g(block);
   return move(block);
}

int main()
{
   g(f(MemoryBlock()));
}
```

Este ejemplo produce el siguiente resultado:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

En este ejemplo, la función `main` pasa un valor R a `f`. El cuerpo de `f` trata el parámetro con nombre como valor L. La llamada de `f` a `g` enlaza el parámetro a una referencia de valor L (la primera versión sobrecargada de `g`).

- **Puede convertir un valor de l en una referencia rvalue.**

La biblioteca estándar de C++ [std:: Move](../standard-library/utility-functions.md#move) función le permite convertir un objeto en una referencia rvalue a ese objeto. Como alternativa, puede usar el **static_cast** palabra clave para convertir un valor de l en una referencia rvalue, tal como se muestra en el ejemplo siguiente:

```cpp
// cast-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

int main()
{
   MemoryBlock block;
   g(block);
   g(static_cast<MemoryBlock&&>(block));
}
```

Este ejemplo produce el siguiente resultado:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

**Las plantillas de función deducen sus tipos de argumento de plantilla y, a continuación, usar las reglas de contracción de referencias.**

Es común escribir una plantilla de función que se pasa (o *reenvía*) sus parámetros a otra función. Es importante saber cómo funciona la deducción de tipos de plantilla para plantillas de función que acepten referencias de valor R.

Si el argumento de función es un valor R, el compilador deduce que el argumento será una referencia de valor R. Por ejemplo, si se pasa una referencia de valor R a un objeto de tipo `X` a una función de plantilla que acepta el tipo `T&&` como su parámetro, la deducción de argumento de plantilla deduce que `T` será `X`. Por consiguiente, el parámetro es de tipo `X&&`. Si el argumento de función es un valor l o **const** de valor l, el compilador deduce que su tipo será una referencia lvalue o **const** referencia lvalue de ese tipo.

En el ejemplo siguiente se declara una plantilla de estructura y, a continuación, se especializa para distintos tipos de referencia. La función `print_type_and_value` acepta una referencia de valor R como parámetro y lo reenvía a la versión especializada adecuada del método `S::print`. La función `main` muestra las diversas maneras de llamar al método `S::print`.

```cpp
// template-type-deduction.cpp
// Compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

template<typename T> struct S;

// The following structures specialize S by
// lvalue reference (T&), const lvalue reference (const T&),
// rvalue reference (T&&), and const rvalue reference (const T&&).
// Each structure provides a print method that prints the type of
// the structure and its parameter.

template<typename T> struct S<T&> {
   static void print(T& t)
   {
      cout << "print<T&>: " << t << endl;
   }
};

template<typename T> struct S<const T&> {
   static void print(const T& t)
   {
      cout << "print<const T&>: " << t << endl;
   }
};

template<typename T> struct S<T&&> {
   static void print(T&& t)
   {
      cout << "print<T&&>: " << t << endl;
   }
};

template<typename T> struct S<const T&&> {
   static void print(const T&& t)
   {
      cout << "print<const T&&>: " << t << endl;
   }
};

// This function forwards its parameter to a specialized
// version of the S type.
template <typename T> void print_type_and_value(T&& t)
{
   S<T&&>::print(std::forward<T>(t));
}

// This function returns the constant string "fourth".
const string fourth() { return string("fourth"); }

int main()
{
   // The following call resolves to:
   // print_type_and_value<string&>(string& && t)
   // Which collapses to:
   // print_type_and_value<string&>(string& t)
   string s1("first");
   print_type_and_value(s1);

   // The following call resolves to:
   // print_type_and_value<const string&>(const string& && t)
   // Which collapses to:
   // print_type_and_value<const string&>(const string& t)
   const string s2("second");
   print_type_and_value(s2);

   // The following call resolves to:
   // print_type_and_value<string&&>(string&& t)
   print_type_and_value(string("third"));

   // The following call resolves to:
   // print_type_and_value<const string&&>(const string&& t)
   print_type_and_value(fourth());
}
```

Este ejemplo produce el siguiente resultado:

```cpp
print<T&>: first
print<const T&>: second
print<T&&>: third
print<const T&&>: fourth
```

Para resolver cada llamada a la función `print_type_and_value`, el compilador realiza primero la deducción de argumento de plantilla. A continuación, el compilador aplica reglas de contracción de referencias cuando sustituye los argumentos de plantilla deducidos para los tipos de parámetro. Por ejemplo, al pasar la variable local `s1` a la función `print_type_and_value` se provoca que el compilador genere la siguiente signatura de función:

```cpp
print_type_and_value<string&>(string& && t)
```

El compilador usa reglas de contracción de referencias para reducir la signatura a lo siguiente:

```cpp
print_type_and_value<string&>(string& t)
```

Esta versión de la función `print_type_and_value` reenvía a continuación su parámetro a la versión especializada correcta del método `S::print`.

En la tabla siguiente se resumen las reglas de contracción de referencias para la deducción de tipos de argumento de plantilla:

|||
|-|-|
|Tipo expandido|Tipo contraído|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

La deducción de argumento de plantilla es un elemento importante de la implementación del reenvío directo. El reenvío directo de secciones, que se presentó anteriormente en este tema, describe el reenvío directo con mayor detalle.

## <a name="summary"></a>Resumen

Las referencias de valor R distinguen los valores L de los valores R. Pueden ayudarle a mejorar el rendimiento de las aplicaciones al eliminar la necesidad de asignaciones de memoria y operaciones de copia innecesarias. También permiten escribir una versión de una función que acepte argumentos arbitrarios y los reenvíe a otra función como si se hubiera llamado directamente a la otra función.

## <a name="see-also"></a>Vea también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Declarador de referencia a un valor L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Constructores de movimiento y operadores de asignación de movimiento (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
