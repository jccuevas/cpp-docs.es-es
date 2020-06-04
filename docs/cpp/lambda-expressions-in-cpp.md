---
title: Expresiones lambda en C++
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
ms.openlocfilehash: e206ea8d67bb333065bf43f7f9c2dc373a5a5258
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857494"
---
# <a name="lambda-expressions-in-c"></a>Expresiones lambda en C++

En C++ 11 y versiones posteriores, una expresión lambda, a menudo denominada *lambda*, es una manera cómoda de definir un objeto de función anónimo (un *cierre*) justo en la ubicación donde se invoca o se pasa como argumento a una función. Normalmente, las lambdas se usan para encapsular unas líneas de código que se pasan a algoritmos o métodos asincrónicos. En este artículo se define qué son las expresiones lambda, se comparan con otras técnicas de programación, se describen sus ventajas y se proporciona un ejemplo básico.

## <a name="related-topics"></a>Temas relacionados

- [Expresiones lambda frente a objetos de función](lambda-expression-syntax.md)
- [Trabajar con expresiones lambda](examples-of-lambda-expressions.md)
- [expresiones lambda de constexpr](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Partes de una expresión lambda

La norma ISO de C++ muestra una expresión lambda sencilla que se pasa como tercer argumento a la función `std::sort()`:

```cpp
#include <algorithm>
#include <cmath>

void abssort(float* x, unsigned n) {
    std::sort(x, x + n,
        // Lambda expression begins
        [](float a, float b) {
            return (std::abs(a) < std::abs(b));
        } // end of lambda expression
    );
}
```

En esta ilustración se muestran las partes de una expresión lambda:

![Elementos estructurales de una expresión lambda](../cpp/media/lambdaexpsyntax.png "Elementos estructurales de una expresión lambda")

1. *cláusula de captura* (también conocida como el *presentador lambda* en la C++ especificación).

1. *lista de parámetros* Opta. (También conocido como *declarador lambda*)

1. *especificación mutable* Opta.

1. *especificación de excepción* Opta.

1. *finalización: tipo de valor devuelto* Opta.

1. *cuerpo de la expresión lambda*.

### <a name="capture-clause"></a>Cláusula capture

Una expresión lambda puede introducir nuevas variables en su cuerpo (en **C++ 14**) y también puede tener acceso a las variables del ámbito circundante, o *capturarlas*. Una expresión lambda comienza con la cláusula Capture (*lambda-presentador* en la sintaxis estándar), que especifica las variables que se capturan y si la captura es por valor o por referencia. A las variables que tienen como prefijo una y comercial (`&`) se accede mediante referencia y a las variables que no tienen el prefijo se accede por valor.

Una cláusula de captura vacía, `[ ]`, indica que el cuerpo de la expresión lambda no tiene acceso a ninguna variable en el ámbito de inclusión.

Puede usar el modo de captura predeterminado (*captura predeterminada* en la sintaxis estándar) para indicar cómo se capturan las variables externas a las que se hace referencia en la expresión lambda: `[&]` significa que todas las variables a las que se hace referencia se capturan por referencia, y `[=]` significa que se capturan por valor. Puede usar un modo de captura predeterminado y, después, especificar el modo opuesto de forma explícita para unas variables específicas. Por ejemplo, si el cuerpo de una expresión lambda accede a la variable externa `total` por referencia y a la variable externa `factor` por valor, las siguientes cláusulas capture serán equivalentes:

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

Solo se capturan las variables que se mencionan en la expresión lambda cuando se usa una captura de valor predeterminado.

Si una cláusula de captura incluye una `&`de captura predeterminada, ningún `identifier` de una `capture` de la cláusula de captura puede tener el formulario `& identifier`. Del mismo modo, si la cláusula Capture incluye un `=`predeterminado de captura, ningún `capture` de la cláusula Capture podrá tener el formato `= identifier`. Un identificador o **esto** no puede aparecer más de una vez en una cláusula de captura. En el fragmento de código siguiente se muestran algunos ejemplos.

```cpp
struct S { void f(int i); };

void S::f(int i) {
    [&, i]{};      // OK
    [&, &i]{};     // ERROR: i preceded by & when & is the default
    [=, this]{};   // ERROR: this when = is the default
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated
}
```

Una captura seguida de puntos suspensivos es una expansión de paquete, como se muestra en este ejemplo de [plantilla variádicas](../cpp/ellipses-and-variadic-templates.md) :

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

Para usar expresiones lambda en el cuerpo de un método de clase, pase el puntero **this** a la cláusula Capture para proporcionar acceso a los métodos y miembros de datos de la clase envolvente.

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): el puntero **this** se puede capturar por valor especificando `*this` en la cláusula Capture. La captura por valor significa que todo el *cierre*, que es el objeto de función anónimo que encapulates la expresión lambda, se copia en todos los sitios de llamada en los que se invoca la expresión lambda. La captura por valor es útil cuando la expresión lambda se ejecutará en operaciones paralelas o asincrónicas, especialmente en determinadas arquitecturas de hardware, como NUMA.

Para ver un ejemplo en el que se muestra cómo usar expresiones lambda con métodos de clase, vea "ejemplo: usar una expresión lambda en un método" en [ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md).

Al usar la cláusula de captura, se recomienda tener en cuenta estos aspectos importantes, especialmente cuando se usan expresiones lambda con multithreading:

- Se pueden usar capturas por referencia para modificar variables externas, pero no se pueden usar capturas por valor. (**mutable** permite modificar las copias, pero no los originales).

- Las capturas por referencia reflejan actualizaciones en variables externas, pero las capturas por valor no.

- Las capturas por referencia presentan una dependencia de la duración, pero las capturas por valor no tienen ninguna dependencia de la duración. Esto es muy importante cuando la expresión lambda se inicia de forma asincrónica. Si captura una variable local por referencia en una expresión lambda asincrónica, es muy probable que dicha variable desaparezca en cuanto se inicie la expresión lambda, lo que provocará una infracción de acceso en tiempo de ejecución.

### <a name="generalized-capture-c-14"></a>Captura generalizada (C++ 14)

En C++14 puede introducir e inicializar nuevas variables en la cláusula de captura sin necesidad de que dichas variables existan en el ámbito de inclusión de la función lambda. La inicialización se puede expresar como cualquier expresión arbitraria; el tipo de la variable nueva se deduce del tipo producido por la expresión. Una ventaja de esta característica es que en C++14 puede capturar variables solo de movimiento (por ejemplo, std::unique_ptr) del ámbito circundante y usarlas en una expresión lambda.

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>Lista de parámetros

Además de capturar variables, una expresión lambda puede aceptar parámetros de entrada. Una lista de parámetros (*declarador lambda* en la sintaxis estándar) es opcional y, en la mayoría de los aspectos, es similar a la lista de parámetros de una función.

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

En  **C++ 14**, si el tipo de parámetro es genérico, puede usar la palabra clave auto como especificador de tipo. Esto indica al compilador que debe crear el operador de llamada de función como plantilla. Cada instancia de "auto" en una lista de parámetros es equivalente a un parámetro de tipo distinto.

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

Una expresión lambda puede tomar otra expresión lambda como argumento. Para obtener más información, vea "expresiones lambda de orden superior" en el tema [ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md).

Dado que una lista de parámetros es opcional, puede omitir los paréntesis vacíos si no pasa argumentos a la expresión lambda y su declarador lambda no contiene *excepciones-Specification*, *Finally-return-type*ni **mutable**.

### <a name="mutable-specification"></a>Especificación mutable

Normalmente, el operador de llamada de función de una expresión lambda es const-by-value, pero el uso de la palabra clave **mutable** lo cancela. No genera miembros de datos mutables. La especificación mutable permite al cuerpo de una expresión lambda modificar las variables que se capturan por valor. En algunos de los ejemplos más adelante en este artículo se muestra cómo usar **mutable**.

### <a name="exception-specification"></a>Especificación de la excepción

Puede utilizar la especificación de excepción `noexcept` para indicar que la expresión lambda no produce ninguna excepción. Al igual que con las funciones normales C++ , el compilador de Microsoft genera la advertencia [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) si una expresión lambda declara la especificación de excepción `noexcept` y el cuerpo de la expresión lambda produce una excepción, como se muestra aquí:

```cpp
// throw_lambda_expression.cpp
// compile with: /W4 /EHsc
int main() // C4297 expected
{
   []() noexcept { throw 5; }();
}
```

Para obtener más información, vea [Especificaciones de excepciones (Throw)](../cpp/exception-specifications-throw-cpp.md).

### <a name="return-type"></a>Tipo devuelto

El tipo de valor devuelto de una expresión lambda se deduce automáticamente. No es necesario usar la palabra clave [auto](../cpp/auto-cpp.md) , a menos que se especifique un *final-return-type*. El *final-return-type* es similar a la parte del tipo de valor devuelto de un método o función normal. Pero el tipo de valor devuelto debe seguir la lista de parámetros y debe incluir la palabra clave trailing-return-type `->` antes del tipo de valor devuelto.

Puede omitir la parte return-type de una expresión lambda si el cuerpo de la expresión lambda contiene una sola instrucción return o si la expresión lambda no devuelve un valor. Si el cuerpo de la expresión lambda contiene una instrucción return, el compilador deduce el tipo de valor devuelto del tipo de expresión return. De lo contrario, el compilador deduce que el tipo de valor devuelto es **void**. Vea los fragmentos de código de ejemplo siguientes que muestran este principio.

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

Una expresión lambda puede generar otra expresión lambda como valor devuelto. Para obtener más información, vea "expresiones lambda de orden superior" en [ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md).

### <a name="lambda-body"></a>Cuerpo lambda

El cuerpo de la expresión lambda (*instrucción compuesta* en la sintaxis estándar) de una expresión lambda puede contener todo lo que puede contener el cuerpo de un método o una función ordinarios. El cuerpo de una función normal y de una expresión lambda puede tener acceso a estos tipos de variables:

- variables capturadas en el ámbito de inclusión, tal como se describió anteriormente.

- Parameters

- Variables declaradas localmente

- Miembros de datos de clase, **cuando se** declaran dentro de una clase y se capturan

- Cualquier variable que tenga duración de almacenamiento estática (por ejemplo, las variables globales)

El ejemplo siguiente contiene una expresión lambda que captura explícitamente la variable `n` por valor y captura implícitamente la variable `m` por referencia:

```cpp
// captures_lambda_expression.cpp
// compile with: /W4 /EHsc
#include <iostream>
using namespace std;

int main()
{
   int m = 0;
   int n = 0;
   [&, n] (int a) mutable { m = ++n + a; }(4);
   cout << m << endl << n << endl;
}
```

```Output
5
0
```

Como la variable `n` se captura por valor, el valor sigue siendo `0` después de la llamada a la expresión lambda. La especificación **mutable** permite modificar `n` dentro de la expresión lambda.

Aunque una expresión lambda solo puede capturar variables que tengan duración de almacenamiento automática, puede utilizar variables que tengan duración de almacenamiento estática en el cuerpo de una expresión lambda. En el ejemplo siguiente se utiliza la función `generate` y una expresión lambda para asignar un valor a cada elemento de un objeto `vector`. La expresión lambda modifica la variable estática para generar el valor del elemento siguiente.

```cpp
void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}
```

Para obtener más información, vea [generar](../standard-library/algorithm-functions.md#generate).

En el ejemplo de código siguiente se usa la función del ejemplo anterior y se agrega un ejemplo de una expresión lambda que C++ usa el algoritmo de la biblioteca estándar `generate_n`. Esta expresión lambda asigna un elemento de un objeto `vector` a la suma de los dos elementos anteriores. La palabra clave **mutable** se usa para que el cuerpo de la expresión lambda pueda modificar sus copias de las variables externas `x` y `y`, que la expresión lambda captura por valor. Como la expresión lambda captura las variables originales `x` e `y` por valor, sus valores siguen siendo `1` después de la ejecución de la expresión.

```cpp
// compile with: /W4 /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}

int main()
{
    // The number of elements in the vector.
    const int elementCount = 9;

    // Create a vector object with each element set to 1.
    vector<int> v(elementCount, 1);

    // These variables hold the previous two elements of the vector.
    int x = 1;
    int y = 1;

    // Sets each element in the vector to the sum of the
    // previous two elements.
    generate_n(v.begin() + 2,
        elementCount - 2,
        [=]() mutable throw() -> int { // lambda is the 3rd parameter
        // Generate current value.
        int n = x + y;
        // Update previous two values.
        x = y;
        y = n;
        return n;
    });
    print("vector v after call to generate_n() with lambda: ", v);

    // Print the local variables x and y.
    // The values of x and y hold their initial values because
    // they are captured by value.
    cout << "x: " << x << " y: " << y << endl;

    // Fill the vector with a sequence of numbers
    fillVector(v);
    print("vector v after 1st call to fillVector(): ", v);
    // Fill the vector with the next sequence of numbers
    fillVector(v);
    print("vector v after 2nd call to fillVector(): ", v);
}
```

```Output
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34
x: 1 y: 1
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18
```

Para obtener más información, vea [generate_n](../standard-library/algorithm-functions.md#generate_n).

## <a name="constexpr-lambda-expressions"></a>Expresiones lambda constexpr

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): una expresión lambda puede declararse como `constexpr` o utilizarse en una expresión constante cuando la inicialización de cada miembro de datos que captura o presenta se permite dentro de una expresión constante.

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

Una expresión lambda se `constexpr` implícitamente si su resultado cumple los requisitos de una función `constexpr`:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Si una expresión lambda se `constexpr`implícita o explícitamente, la conversión a un puntero de función genera una función de `constexpr`:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>Específico de Microsoft

Las expresiones lambda no se admiten en las siguientes entidades administradas de Common Language Runtime (CLR): **clase Ref**, **struct Ref**, **clase de valor**o **struct de valor**.

Si usa un modificador específico de Microsoft como [__declspec](../cpp/declspec.md), puede insertarlo en una expresión lambda inmediatamente después del `parameter-declaration-clause`, por ejemplo:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Para determinar si un modificador es compatible con las expresiones lambda, consulte el artículo sobre él en la sección [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md) de la documentación.

Además de la funcionalidad lambda estándar de C++ 11, Visual Studio es compatible con las expresiones lambda sin estado, que se pueden convertir en punteros de función que usan convenciones de llamada arbitrarias.

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Objetos de función en la biblioteca estándar de C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Llamada a función](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
