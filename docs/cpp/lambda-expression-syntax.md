---
title: Sintaxis de la expresión lambda
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
ms.openlocfilehash: 37e4a512678bf276b5244fd54945f49a37ff8d01
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222390"
---
# <a name="lambda-expression-syntax"></a>Sintaxis de la expresión lambda

En este artículo se demuestra la sintaxis y los elementos estructurales de las expresiones lambda. Para obtener una descripción de las expresiones lambda, vea [expresiones Lambda](../cpp/lambda-expressions-in-cpp.md).

## <a name="function-objects-vs-lambdas"></a>Objetos de función frente a expresiones Lambdas

Cuando escribe código, utilice probablemente punteros de función y los objetos de función para resolver problemas y realizar cálculos, especialmente cuando se usa [algoritmos de la biblioteca estándar de C++](../cpp/algorithms-modern-cpp.md). Tanto los punteros a función como los objetos de función tienen ventajas y desventajas; por ejemplo, los punteros a función tienen una sobrecarga sintáctica mínima pero no conservan el estado dentro de un ámbito, y los objetos de función pueden conservar el estado pero requieren la sobrecarga sintáctica de una definición de clase.

Una expresión lambda combina las ventajas de los punteros a función y los objetos de función y evita sus desventajas. Como los objetos de función, una expresión lambda es flexible y puede conservar el estado, pero, a diferencia de un objeto de función, su sintaxis compacta no requiere una definición de clase explícita. Mediante expresiones lambda, se puede escribir código menos complejo y menos propenso a errores que el código para un objeto de función equivalente.

En los ejemplos siguientes se compara el uso de una expresión lambda con el uso de un objeto de función. En el primer ejemplo se utiliza una expresión lambda para imprimir en la consola si cada elemento de un objeto `vector` es par o impar. En el segundo ejemplo se usa un objeto de función para realizar la misma tarea.

## <a name="example-1-using-a-lambda"></a>Ejemplo 1: usar una expresión lambda

Este ejemplo pasa una expresión lambda para el **for_each** función. La expresión lambda imprime un resultado que indica si cada elemento de un objeto `vector` es par o impar.

### <a name="code"></a>Código

```cpp
// even_lambda.cpp
// compile with: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

int main()
{
   // Create a vector object that contains 9 elements.
   vector<int> v;
   for (int i = 1; i < 10; ++i) {
      v.push_back(i);
   }

   // Count the number of even numbers in the vector by
   // using the for_each function and a lambda.
   int evenCount = 0;
   for_each(v.begin(), v.end(), [&evenCount] (int n) {
      cout << n;
      if (n % 2 == 0) {
         cout << " is even " << endl;
         ++evenCount;
      } else {
         cout << " is odd " << endl;
      }
   });

   // Print the count of even numbers to the console.
   cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

### <a name="comments"></a>Comentarios

En el ejemplo, el tercer argumento para el **for_each** función es una expresión lambda. La parte `[&evenCount]` especifica la cláusula capture de la expresión, `(int n)` especifica la lista de parámetros y la parte restante especifica el cuerpo de la expresión.

## <a name="example-2-using-a-function-object"></a>Ejemplo 2: Usar un objeto de función

En ocasiones, una expresión lambda sería demasiado difícil de extender mucho más allá del ejemplo anterior. En el ejemplo siguiente se usa un objeto de función en lugar de una expresión lambda, junto con el **for_each** función, para producir los mismos resultados que el ejemplo 1. Ambos ejemplos almacenan el recuento de números pares en un objeto `vector`. Para mantener el estado de la operación, la clase `FunctorClass` almacena la variable `m_evenCount` por referencia como una variable miembro. Para realizar la operación, `FunctorClass` implementa el operador de llamada de función, **operator()**. Microsoft C++ compilador genera código que es comparable en tamaño y rendimiento para el código de la expresión lambda en el ejemplo 1. Si se trata de un problema básico como el de este artículo, probablemente el diseño lambda más simple sea mejor que el diseño de objeto de función. Sin embargo, si cree que la funcionalidad puede requerir una extensión importante en el futuro, utilice el diseño de objeto de función para que el mantenimiento del código sea más sencillo.

Para obtener más información sobre la **operator()**, consulte [llamadas a función](../cpp/function-call-cpp.md). Para obtener más información sobre la **for_each** de función, vea [for_each](../standard-library/algorithm-functions.md#for_each).

### <a name="code"></a>Código

```cpp
// even_functor.cpp
// compile with: /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

class FunctorClass
{
public:
    // The required constructor for this example.
    explicit FunctorClass(int& evenCount)
        : m_evenCount(evenCount) { }

    // The function-call operator prints whether the number is
    // even or odd. If the number is even, this method updates
    // the counter.
    void operator()(int n) const {
        cout << n;

        if (n % 2 == 0) {
            cout << " is even " << endl;
            ++m_evenCount;
        } else {
            cout << " is odd " << endl;
        }
    }

private:
    // Default assignment operator to silence warning C4512.
    FunctorClass& operator=(const FunctorClass&);

    int& m_evenCount; // the number of even variables in the vector.
};

int main()
{
    // Create a vector object that contains 9 elements.
    vector<int> v;
    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }

    // Count the number of even numbers in the vector by
    // using the for_each function and a function object.
    int evenCount = 0;
    for_each(v.begin(), v.end(), FunctorClass(evenCount));

    // Print the count of even numbers to the console.
    cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[generate](../standard-library/algorithm-functions.md#generate)<br/>
[generate_n](../standard-library/algorithm-functions.md#generate_n)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)<br/>
[Especificaciones de excepciones (throw)](../cpp/exception-specifications-throw-cpp.md)<br/>
[Advertencia del compilador (nivel 1) C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)<br/>
[Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md)