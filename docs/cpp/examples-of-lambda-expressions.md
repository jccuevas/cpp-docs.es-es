---
title: Ejemplos de expresiones lambda
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], examples
ms.assetid: 52506b15-0771-4190-a966-2f302049ca86
ms.openlocfilehash: 07c0f6b12c3c6a5dd0c3273acccbaacbc0db08a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189044"
---
# <a name="examples-of-lambda-expressions"></a>Ejemplos de expresiones lambda

En este artículo se muestra cómo usar expresiones lambda en programas. Para obtener información general sobre las expresiones lambda, vea [expresiones lambda](../cpp/lambda-expressions-in-cpp.md). Para obtener más información sobre la estructura de una expresión lambda, vea [Sintaxis de expresiones lambda](../cpp/lambda-expression-syntax.md).

##  <a name="declaring-lambda-expressions"></a><a name="declaringLambdaExpressions"></a>Declarar expresiones lambda

### <a name="example-1"></a>Ejemplo 1

Dado que una expresión lambda tiene tipo, puede asignarla a una variable **auto** o a un objeto de [función](../standard-library/function-class.md) , como se muestra aquí:

### <a name="code"></a>Código

```cpp
// declaring_lambda_expressions1.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{

    using namespace std;

    // Assign the lambda expression that adds two numbers to an auto variable.
    auto f1 = [](int x, int y) { return x + y; };

    cout << f1(2, 3) << endl;

    // Assign the same lambda expression to a function object.
    function<int(int, int)> f2 = [](int x, int y) { return x + y; };

    cout << f2(3, 4) << endl;
}
```

### <a name="output"></a>Output

```Output
5
7
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [auto](../cpp/auto-cpp.md), [function Class](../standard-library/function-class.md)y [FUNCTION call](../cpp/function-call-cpp.md).

Aunque las expresiones lambda se suelen declarar en el cuerpo de una función, se pueden declarar en cualquier lugar donde se pueda inicializar una variable.

### <a name="example-2"></a>Ejemplo 2

El compilador de Microsoft C++ enlaza una expresión lambda a sus variables capturadas cuando se declara la expresión en lugar de cuando se llama a la expresión. En el ejemplo siguiente se muestra una expresión lambda que captura la variable local `i` por valor y la variable local `j` por referencia. Como la expresión lambda captura `i` por valor, la reasignación de `i` más adelante en el programa no afecta al resultado de la expresión. Sin embargo, puesto que la expresión lambda captura `j` por referencia, la reasignación de `j` afecta al resultado de la expresión.

### <a name="code"></a>Código

```cpp
// declaring_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   int i = 3;
   int j = 5;

   // The following lambda expression captures i by value and
   // j by reference.
   function<int (void)> f = [i, &j] { return i + j; };

   // Change the values of i and j.
   i = 22;
   j = 44;

   // Call f and print its result.
   cout << f() << endl;
}
```

### <a name="output"></a>Output

```Output
47
```

[[En este artículo](#top)]

##  <a name="calling-lambda-expressions"></a><a name="callingLambdaExpressions"></a>Llamar a expresiones lambda

Es posible llamar a una expresión lambda inmediatamente, como se muestra en el fragmento de código siguiente. El segundo fragmento de código muestra cómo pasar una expresión lambda como argumento C++ a algoritmos de la biblioteca estándar, como `find_if`.

### <a name="example-1"></a>Ejemplo 1

En este ejemplo se declara una expresión lambda que devuelve la suma de dos números enteros y se llama a la expresión inmediatamente con los argumentos `5` y `4`:

### <a name="code"></a>Código

```cpp
// calling_lambda_expressions1.cpp
// compile with: /EHsc
#include <iostream>

int main()
{
   using namespace std;
   int n = [] (int x, int y) { return x + y; }(5, 4);
   cout << n << endl;
}
```

### <a name="output"></a>Output

```Output
9
```

### <a name="example-2"></a>Ejemplo 2

En este ejemplo se pasa una expresión lambda como argumento a la función `find_if`. La expresión lambda devuelve **true** si su parámetro es un número par.

### <a name="code"></a>Código

```cpp
// calling_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    // Create a list of integers with a few initial elements.
    list<int> numbers;
    numbers.push_back(13);
    numbers.push_back(17);
    numbers.push_back(42);
    numbers.push_back(46);
    numbers.push_back(99);

    // Use the find_if function and a lambda expression to find the
    // first even number in the list.
    const list<int>::const_iterator result =
        find_if(numbers.begin(), numbers.end(),[](int n) { return (n % 2) == 0; });

    // Print the result.
    if (result != numbers.end()) {
        cout << "The first even number in the list is " << *result << "." << endl;
    } else {
        cout << "The list contains no even numbers." << endl;
    }
}
```

### <a name="output"></a>Output

```Output
The first even number in the list is 42.
```

### <a name="remarks"></a>Observaciones

Para obtener más información sobre la función `find_if`, vea [find_if](../standard-library/algorithm-functions.md#find_if). Para obtener más información sobre C++ las funciones de la biblioteca estándar que realizan algoritmos comunes, vea [\<algoritmo >](../standard-library/algorithm.md).

[[En este artículo](#top)]

##  <a name="nesting-lambda-expressions"></a><a name="nestingLambdaExpressions"></a>Anidar expresiones lambda

### <a name="example"></a>Ejemplo

Se puede anidar una expresión lambda dentro de otra, como se muestra en este ejemplo. La expresión lambda interna multiplica su argumento por 2 y devuelve el resultado. La expresión lambda externa llama a la expresión lambda interna con su argumento y suma 3 al resultado.

### <a name="code"></a>Código

```cpp
// nesting_lambda_expressions.cpp
// compile with: /EHsc /W4
#include <iostream>

int main()
{
    using namespace std;

    // The following lambda expression contains a nested lambda
    // expression.
    int timestwoplusthree = [](int x) { return [](int y) { return y * 2; }(x) + 3; }(5);

    // Print the result.
    cout << timestwoplusthree << endl;
}
```

### <a name="output"></a>Output

```Output
13
```

### <a name="remarks"></a>Observaciones

En este ejemplo, `[](int y) { return y * 2; }` es la expresión lambda anidada.

[[En este artículo](#top)]

##  <a name="higher-order-lambda-functions"></a><a name="higherOrderLambdaExpressions"></a>Funciones lambda de orden superior

### <a name="example"></a>Ejemplo

Muchos lenguajes de programación admiten el concepto de una *función de orden superior.* Una función de orden superior es una expresión lambda que toma otra expresión lambda como argumento o que devuelve una expresión lambda. Puede usar la clase de [función](../standard-library/function-class.md) para permitir que C++ una expresión lambda se comporte como una función de orden superior. En el ejemplo siguiente se muestra una expresión lambda que devuelve un objeto `function` y una expresión lambda que toma un objeto `function` como argumento.

### <a name="code"></a>Código

```cpp
// higher_order_lambda_expression.cpp
// compile with: /EHsc /W4
#include <iostream>
#include <functional>

int main()
{
    using namespace std;

    // The following code declares a lambda expression that returns
    // another lambda expression that adds two numbers.
    // The returned lambda expression captures parameter x by value.
    auto addtwointegers = [](int x) -> function<int(int)> {
        return [=](int y) { return x + y; };
    };

    // The following code declares a lambda expression that takes another
    // lambda expression as its argument.
    // The lambda expression applies the argument z to the function f
    // and multiplies by 2.
    auto higherorder = [](const function<int(int)>& f, int z) {
        return f(z) * 2;
    };

    // Call the lambda expression that is bound to higherorder.
    auto answer = higherorder(addtwointegers(7), 8);

    // Print the result, which is (7+8)*2.
    cout << answer << endl;
}
```

### <a name="output"></a>Output

```Output
30
```

[[En este artículo](#top)]

##  <a name="using-a-lambda-expression-in-a-function"></a><a name="methodLambdaExpressions"></a>Usar una expresión lambda en una función

### <a name="example"></a>Ejemplo

Las expresiones lambda se pueden usar en el cuerpo de una función. La expresión lambda puede tener acceso a cualquier función o miembro de datos al que pueda tener acceso la función envolvente. Puede capturar explícita o implícitamente el puntero **this** para proporcionar acceso a funciones y miembros de datos de la clase envolvente.
**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): Capture **este** valor (`[*this]`) cuando la expresión lambda se usará en operaciones asincrónicas o paralelas en las que el código pueda ejecutarse después de que el objeto original salga del ámbito.

Puede usar el puntero **this** explícitamente en una función, como se muestra aquí:

```cpp
// capture "this" by reference
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [this](int n) { cout << n * _scale << endl; });
}

// capture "this" by value (Visual Studio 2017 version 15.3 and later)
void ApplyScale2(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [*this](int n) { cout << n * _scale << endl; });
}
```

También puede capturar el puntero **this** implícitamente:

```cpp
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [=](int n) { cout << n * _scale << endl; });
}
```

En el ejemplo siguiente se muestra la clase `Scale`, que encapsula un valor de escala.

```cpp
// function_lambda_expression.cpp
// compile with: /EHsc /W4
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

class Scale
{
public:
    // The constructor.
    explicit Scale(int scale) : _scale(scale) {}

    // Prints the product of each element in a vector object
    // and the scale value to the console.
    void ApplyScale(const vector<int>& v) const
    {
        for_each(v.begin(), v.end(), [=](int n) { cout << n * _scale << endl; });
    }

private:
    int _scale;
};

int main()
{
    vector<int> values;
    values.push_back(1);
    values.push_back(2);
    values.push_back(3);
    values.push_back(4);

    // Create a Scale object that scales elements by 3 and apply
    // it to the vector object. Does not modify the vector.
    Scale s(3);
    s.ApplyScale(values);
}
```

### <a name="output"></a>Output

```Output
3
6
9
12
```

### <a name="remarks"></a>Observaciones

La función `ApplyScale` usa una expresión lambda para imprimir el producto del valor de escala y cada elemento de un objeto `vector`. La expresión lambda captura implícitamente **esto** para que pueda tener acceso al miembro de `_scale`.

[[En este artículo](#top)]

##  <a name="using-lambda-expressions-with-templates"></a><a name="templateLambdaExpressions"></a>Usar expresiones lambda con plantillas

### <a name="example"></a>Ejemplo

Puesto que las expresiones lambda tienen tipo, pueden utilizarse con plantillas de C++. En el ejemplo siguiente se muestran las funciones `negate_all` y `print_all`. La función `negate_all` aplica el **operador** unario a cada elemento del objeto `vector`. La función `print_all` imprime en la consola todos los elementos del objeto `vector`.

### <a name="code"></a>Código

```cpp
// template_lambda_expression.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

// Negates each element in the vector object. Assumes signed data type.
template <typename T>
void negate_all(vector<T>& v)
{
    for_each(v.begin(), v.end(), [](T& n) { n = -n; });
}

// Prints to the console each element in the vector object.
template <typename T>
void print_all(const vector<T>& v)
{
    for_each(v.begin(), v.end(), [](const T& n) { cout << n << endl; });
}

int main()
{
    // Create a vector of signed integers with a few elements.
    vector<int> v;
    v.push_back(34);
    v.push_back(-43);
    v.push_back(56);

    print_all(v);
    negate_all(v);
    cout << "After negate_all():" << endl;
    print_all(v);
}
```

### <a name="output"></a>Output

```Output
34
-43
56
After negate_all():
-34
43
-56
```

### <a name="remarks"></a>Observaciones

Para obtener más información C++ acerca de las plantillas, consulte [plantillas](../cpp/templates-cpp.md).

[[En este artículo](#top)]

##  <a name="handling-exceptions"></a><a name="ehLambdaExpressions"></a>Controlar excepciones

### <a name="example"></a>Ejemplo

El cuerpo de una expresión lambda sigue las reglas tanto del control de excepciones estructurado (SEH) como del control de excepciones de C++. Es posible controlar una excepción generada en el cuerpo de una expresión lambda o aplazar el control de excepciones al ámbito de inclusión. En el ejemplo siguiente se usa la función **for_each** y una expresión lambda para rellenar un objeto `vector` con los valores de otro. Usa un bloque **try**/**catch** para controlar el acceso no válido al primer vector.

### <a name="code"></a>Código

```cpp
// eh_lambda_expression.cpp
// compile with: /EHsc /W4
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

int main()
{
    // Create a vector that contains 3 elements.
    vector<int> elements(3);

    // Create another vector that contains index values.
    vector<int> indices(3);
    indices[0] = 0;
    indices[1] = -1; // This is not a valid subscript. It will trigger an exception.
    indices[2] = 2;

    // Use the values from the vector of index values to
    // fill the elements vector. This example uses a
    // try/catch block to handle invalid access to the
    // elements vector.
    try
    {
        for_each(indices.begin(), indices.end(), [&](int index) {
            elements.at(index) = index;
        });
    }
    catch (const out_of_range& e)
    {
        cerr << "Caught '" << e.what() << "'." << endl;
    };
}
```

### <a name="output"></a>Output

```Output
Caught 'invalid vector<T> subscript'.
```

### <a name="remarks"></a>Observaciones

Para obtener más información sobre el control de excepciones, vea [control de excepciones](../cpp/exception-handling-in-visual-cpp.md).

[[En este artículo](#top)]

##  <a name="using-lambda-expressions-with-managed-types-ccli"></a><a name="managedLambdaExpressions"></a>Usar expresiones lambda con tipos administradosC++(/CLI)

### <a name="example"></a>Ejemplo

La cláusula capture de una expresión lambda no puede contener una variable que tenga un tipo administrado. Sin embargo, se puede pasar un argumento que tenga un tipo administrado a la lista de parámetros de una expresión lambda. El ejemplo siguiente contiene una expresión lambda que captura la variable local no administrada `ch` por valor y toma un objeto <xref:System.String?displayProperty=fullName> como parámetro.

### <a name="code"></a>Código

```cpp
// managed_lambda_expression.cpp
// compile with: /clr
using namespace System;

int main()
{
    char ch = '!'; // a local unmanaged variable

    // The following lambda expression captures local variables
    // by value and takes a managed String object as its parameter.
    [=](String ^s) {
        Console::WriteLine(s + Convert::ToChar(ch));
    }("Hello");
}
```

### <a name="output"></a>Output

```Output
Hello!
```

### <a name="remarks"></a>Observaciones

También se pueden usar expresiones lambda con la biblioteca de STL/CLR. Para obtener más información, vea referencia de la [biblioteca de STL/CLR](../dotnet/stl-clr-library-reference.md).

> [!IMPORTANT]
>  Las expresiones lambda no se admiten en estas entidades administradas de Common Language Runtime (CLR): **ref Class**, **ref struct**, **Value Class**y **Value struct**.

[[En este artículo](#top)]

## <a name="see-also"></a>Consulte también

[Expresiones lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Sintaxis de la expresión lambda](../cpp/lambda-expression-syntax.md)<br/>
[auto](../cpp/auto-cpp.md)<br/>
[function (Clase)](../standard-library/function-class.md)<br/>
[find_if](../standard-library/algorithm-functions.md#find_if)<br/>
[\<algorithm>](../standard-library/algorithm.md)<br/>
[Llamada a función](../cpp/function-call-cpp.md)<br/>
[Templates](../cpp/templates-cpp.md) (Plantillas [C++])<br/>
[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)
