---
title: Ejemplos de expresiones Lambda | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], examples
ms.assetid: 52506b15-0771-4190-a966-2f302049ca86
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3177896b8cfdff78b0af2aeb40873f31099ce7d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="examples-of-lambda-expressions"></a>Ejemplos de expresiones lambda
En este artículo se muestra cómo usar expresiones lambda en programas. Para obtener información general sobre expresiones lambda, vea [expresiones Lambda](../cpp/lambda-expressions-in-cpp.md). Para obtener más información acerca de la estructura de una expresión lambda, vea [sintaxis de expresiones Lambda](../cpp/lambda-expression-syntax.md).  
  
##  <a name="declaringLambdaExpressions"></a>Declarar expresiones Lambda  
  
### <a name="example-1"></a>Ejemplo 1  
 Puesto que una expresión lambda tiene tipo, puede asignarla a una `auto` variable o a una [función](../standard-library/function-class.md) de objeto, como se muestra aquí:  
  
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
  
### <a name="output"></a>Salida  
  
```Output  
5  
7  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [automática](../cpp/auto-cpp.md), [función clase](../standard-library/function-class.md), y [llamadas a función](../cpp/function-call-cpp.md).  
  
 Aunque las expresiones lambda se suelen declarar en el cuerpo de una función, se pueden declarar en cualquier lugar donde se pueda inicializar una variable.  
  
### <a name="example-2"></a>Ejemplo 2  
 El compilador de Visual C++ enlaza una expresión lambda a sus variables capturadas cuando se declara la expresión, no cuando se llama a la misma. En el ejemplo siguiente se muestra una expresión lambda que captura la variable local `i` por valor y la variable local `j` por referencia. Como la expresión lambda captura `i` por valor, la reasignación de `i` más adelante en el programa no afecta al resultado de la expresión. Sin embargo, puesto que la expresión lambda captura `j` por referencia, la reasignación de `j` afecta al resultado de la expresión.  
  
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
  
### <a name="output"></a>Salida  
  
```Output  
47  
```  
  
 [[En este artículo](#top)]  
  
##  <a name="callingLambdaExpressions"></a>Llamar a expresiones Lambda  
 Es posible llamar a una expresión lambda inmediatamente, como se muestra en el fragmento de código siguiente. El segundo fragmento de código muestra cómo pasar una expresión lambda como argumento a algoritmos de la biblioteca estándar de C++ como `find_if`.  
  
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
  
### <a name="output"></a>Salida  
  
```Output  
9  
```  
  
### <a name="example-2"></a>Ejemplo 2  
 En este ejemplo se pasa una expresión lambda como argumento a la función `find_if`. La expresión lambda devuelve `true` si el parámetro es un número par.  
  
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
  
### <a name="output"></a>Salida  
  
```Output  
The first even number in the list is 42.  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre la `find_if` función, vea [find_if](../standard-library/algorithm-functions.md#find_if). Para obtener más información sobre las funciones de biblioteca estándar de C++ que realizan algoritmos comunes, consulte [ \<algoritmo >](../standard-library/algorithm.md).  
  
 [[En este artículo](#top)]  
  
##  <a name="nestingLambdaExpressions"></a>Anidar expresiones Lambda  
  
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
  
### <a name="output"></a>Salida  
  
```Output  
13  
```  
  
### <a name="remarks"></a>Comentarios  
 En este ejemplo, `[](int y) { return y * 2; }` es la expresión lambda anidada.  
  
 [[En este artículo](#top)]  
  
##  <a name="higherOrderLambdaExpressions"></a>Funciones Lambda de orden superior  
  
### <a name="example"></a>Ejemplo  
 Muchos lenguajes de programación admiten el concepto de un *función de orden superior.* Una función de orden superior es una expresión lambda que toma otra expresión lambda como argumento o que devuelve una expresión lambda. Puede usar el [función](../standard-library/function-class.md) clase para habilitar una expresión lambda de C++ se comporte como una función de orden superior. En el ejemplo siguiente se muestra una expresión lambda que devuelve un objeto `function` y una expresión lambda que toma un objeto `function` como argumento.  
  
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
  
### <a name="output"></a>Salida  
  
```Output  
30  
```  
  
 [[En este artículo](#top)]  
  
##  <a name="methodLambdaExpressions"></a>Usar una expresión Lambda en una función  
  
### <a name="example"></a>Ejemplo  
 Las expresiones lambda se pueden usar en el cuerpo de una función. La expresión lambda puede tener acceso a cualquier función o miembro de datos al que pueda tener acceso la función envolvente. Se puede capturar explícita o implícitamente el puntero `this` para proporcionar acceso a las funciones y miembros de datos de la clase envolvente.  
**Visual Studio 2017 15,3 y versiones posteriores** (disponible con [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): capturar `this` por valor (`[*this]`) cuando la expresión lambda se usará en operaciones asincrónicas o paralelo donde el código podría ejecutar después de que el objeto original queda fuera del ámbito.
  
 Se puede usar el puntero `this` explícitamente en una función, como se muestra aquí:  
  
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
  
 También se puede capturar el puntero `this` de forma implícita:  
  
```  
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
  
### <a name="output"></a>Salida  
  
```Output  
3  
6  
9  
12  
  
```  
  
### <a name="remarks"></a>Comentarios  
 La función `ApplyScale` usa una expresión lambda para imprimir el producto del valor de escala y cada elemento de un objeto `vector`. La expresión lambda captura implícitamente el puntero `this` para poder tener acceso al miembro `_scale`.  
  
 [[En este artículo](#top)]  
  
##  <a name="templateLambdaExpressions"></a>Usar expresiones Lambda con plantillas  
  
### <a name="example"></a>Ejemplo  
 Puesto que las expresiones lambda tienen tipo, pueden utilizarse con plantillas de C++. En el ejemplo siguiente se muestran las funciones `negate_all` y `print_all`. La función `negate_all` aplica el `operator-` unario a todos los elementos del objeto `vector`. La función `print_all` imprime en la consola todos los elementos del objeto `vector`.  
  
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
  
### <a name="output"></a>Salida  
  
```Output  
34  
-43  
56  
After negate_all():  
-34  
43  
-56  
  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las plantillas de C++, vea [plantillas](../cpp/templates-cpp.md).  
  
 [[En este artículo](#top)]  
  
##  <a name="ehLambdaExpressions"></a>Control de excepciones  
  
### <a name="example"></a>Ejemplo  
 El cuerpo de una expresión lambda sigue las reglas tanto del control de excepciones estructurado (SEH) como del control de excepciones de C++. Es posible controlar una excepción generada en el cuerpo de una expresión lambda o aplazar el control de excepciones al ámbito de inclusión. En el ejemplo siguiente se usa la función `for_each` y una expresión lambda para rellenar un objeto `vector` con los valores de otro. Usa un `try` / `catch` bloque para controlar el acceso no válido para el primer vector.  
  
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
  
### <a name="output"></a>Salida  
  
```Output  
Caught 'invalid vector<T> subscript'.  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre el control de excepciones, vea [Exception Handling](../cpp/exception-handling-in-visual-cpp.md).  
  
 [[En este artículo](#top)]  
  
##  <a name="managedLambdaExpressions"></a>Usar expresiones Lambda con tipos administrados (C++ / CLI)  
  
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
  
### <a name="output"></a>Salida  
  
```Output  
Hello!  
```  
  
### <a name="remarks"></a>Comentarios  
 También se pueden usar expresiones lambda con la biblioteca de STL/CLR. Para obtener más información, consulte [referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md).  
  
> [!IMPORTANT]
>  Las expresiones lambda no se admite en estas entidades administradas siguientes de Common Language Runtime (CLR): `ref class`, `ref struct`, `value class` y `value struct`.  
  
 [[En este artículo](#top)]  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md)   
 [Sintaxis de expresiones lambda](../cpp/lambda-expression-syntax.md)   
 [Automático](../cpp/auto-cpp.md)   
 [Function (clase)](../standard-library/function-class.md)   
 [find_if](../standard-library/algorithm-functions.md#find_if)   
 [\<algoritmo >](../standard-library/algorithm.md)   
 [Llamada de función](../cpp/function-call-cpp.md)   
 [Plantillas](../cpp/templates-cpp.md)   
 [Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)   
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)