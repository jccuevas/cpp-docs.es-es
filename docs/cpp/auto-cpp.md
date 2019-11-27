---
title: auto (C++)
ms.date: 11/04/2016
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: 8af2aceb2964a5ec3adcbb0b0accab0b051ff48c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303383"
---
# <a name="auto-c"></a>auto (C++)

Deduce el tipo de una variable declarada a partir de su expresión de inicialización.

## <a name="syntax"></a>Sintaxis

```
auto declarator initializer;
```

```
[](auto param1, auto param2) {};
```

## <a name="remarks"></a>Comentarios

La palabra clave **auto** indica al compilador que utilice la expresión de inicialización de una variable declarada o un parámetro de expresión lambda para deducir su tipo.

Se recomienda usar la palabra clave **auto** en la mayoría de las situaciones, a menos que desee realmente una conversión, ya que proporciona estas ventajas:

- **Solidez:** Si se cambia el tipo de la expresión (esto incluye cuando se cambia un tipo de valor devuelto de función), solo funciona.

- **Rendimiento:** Se garantiza que no habrá conversión.

- **Facilidad de uso:** No tiene que preocuparse por las dificultades de ortografía y los errores tipográficos.

- **Eficiencia:** La codificación puede ser más eficaz.

Casos de conversión en los que es posible que no desee usar **auto**:

- Cuando se desea un tipo específico y es la única alternativa.

- Tipos de aplicación auxiliar de plantilla de expresión: por ejemplo, `(valarray+valarray)`.

Para usar la palabra clave **auto** , úsela en lugar de un tipo para declarar una variable y especifique una expresión de inicialización. Además, puede modificar la palabra clave **auto** mediante especificadores y declaradores como **const**, **volatile**, Pointer (`*`), Reference (`&`) y referencia rvalue (`&&`). El compilador evalúa la expresión de inicialización y emplea esa información para deducir el tipo de la variable.

La expresión de inicialización puede ser una asignación (sintaxis de signo igual), una inicialización directa (sintaxis de estilo de función), una expresión de [operador New](new-operator-cpp.md) o la expresión de inicialización puede ser el parámetro *for-Range-declaration* en una instrucción [for-based for Statement (C++) basada en intervalo](../cpp/range-based-for-statement-cpp.md) . Para obtener más información, vea [inicializadores](../cpp/initializers.md) y los ejemplos de código más adelante en este documento.

La palabra clave **auto** es un marcador de posición para un tipo, pero no es un tipo. Por lo tanto, la palabra clave **auto** no se puede usar en conversiones u operadores como [sizeof](../cpp/sizeof-operator.md) y C++(para/CLI) [typeid](../extensions/typeid-cpp-component-extensions.md).

## <a name="usefulness"></a>Utilidad

La palabra clave **auto** es una forma sencilla de declarar una variable que tiene un tipo complejo. Por ejemplo, puede utilizar **auto** para declarar una variable en la que la expresión de inicialización implique plantillas, punteros a funciones o punteros a miembros.

También puede utilizar **auto** para declarar e inicializar una variable en una expresión lambda. No puede declarar el tipo de la variable porque solo el compilador conoce el tipo de una expresión lambda. Para obtener más información, vea [ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md).

## <a name="trailing-return-types"></a>Tipos de valor devuelto finales

Puede usar **auto**, junto con el especificador de tipo **decltype** , para ayudar a escribir bibliotecas de plantillas. Use **auto** y **decltype** para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla. O bien, use **auto** y **decltype** para declarar una función de plantilla que contiene una llamada a otra función y, a continuación, devuelve el tipo de valor devuelto de esa otra función. Para obtener más información, vea [decltype](../cpp/decltype-cpp.md).

## <a name="references-and-cv-qualifiers"></a>Referencias y calificadores cv

Tenga en cuenta que el uso de referencias **automáticas** , calificadores const y calificadores volátiles. Considere el ejemplo siguiente:

```cpp
// cl.exe /analyze /EHsc /W4
#include <iostream>

using namespace std;

int main( )
{
    int count = 10;
    int& countRef = count;
    auto myAuto = countRef;

    countRef = 11;
    cout << count << " ";

    myAuto = 12;
    cout << count << endl;
}
```

En el ejemplo anterior, he auto es un int, no una referencia int, por lo que la salida es `11 11`, no `11 12` como sería el caso si el calificador de referencia no se hubiera quitado por **auto**.

## <a name="type-deduction-with-braced-initializers-c14"></a>Deducción de tipos con inicializadores entre llaves (C++ 14)

En el ejemplo de código siguiente se muestra cómo inicializar una variable automática mediante llaves. Observe la diferencia entre B y C y entre A y E.

```cpp
#include <initializer_list>

int main()
{
    // std::initializer_list<int>
    auto A = { 1, 2 };

    // std::initializer_list<int>
    auto B = { 3 };

    // int
    auto C{ 4 };

    // C3535: cannot deduce type for 'auto' from initializer list'
    auto D = { 5, 6.7 };

    // C3518 in a direct-list-initialization context the type for 'auto'
    // can only be deduced from a single initializer expression
    auto E{ 8, 9 };

    return 0;
}
```

## <a name="restrictions-and-error-messages"></a>Restricciones y mensajes de error

En la tabla siguiente se enumeran las restricciones del uso de la palabra clave **auto** y el mensaje de error de diagnóstico correspondiente que emite el compilador.

|Número de error|Descripción|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|La palabra clave **auto** no se puede combinar con ningún otro especificador de tipo.|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Un símbolo que se declara con la palabra clave **auto** debe tener un inicializador.|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Ha utilizado incorrectamente la palabra clave **auto** para declarar un tipo. Por ejemplo, declaró un tipo de valor devuelto de método o una matriz.|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Un parámetro o un argumento de plantilla no se pueden declarar con la palabra clave **auto** .|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Un método o un parámetro de plantilla no se puede declarar con la palabra clave **auto** .|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|No se puede usar un símbolo antes de inicializarlo. En la práctica, esto significa que una variable no se puede usar para inicializarse a sí misma.|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|No se puede convertir a un tipo que se declara con la palabra clave **auto** .|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Todos los símbolos de una lista de declaradores que se declara con la palabra clave **auto** deben resolverse en el mismo tipo. Para obtener más información, vea [declaraciones y definiciones](declarations-and-definitions-cpp.md).|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|Los operadores [sizeof](../cpp/sizeof-operator.md) y [typeid](../extensions/typeid-cpp-component-extensions.md) no se pueden aplicar a un símbolo declarado con la palabra clave **auto** .|

## <a name="examples"></a>Ejemplos

Estos fragmentos de código muestran algunas de las formas en que se puede usar la palabra clave **auto** .

Las declaraciones siguientes son equivalentes. En la primera instrucción, la variable `j` se declara como de tipo **int**. En la segunda instrucción, se deduce que la variable `k` es de tipo **int** porque la expresión de inicialización (0) es un entero.

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

Las declaraciones siguientes son equivalentes, pero la segunda declaración es más sencilla que la primera. Uno de los motivos más atractivos para usar la palabra clave **auto** es la simplicidad.

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

En el fragmento de código siguiente se declara el tipo de variables `iter` y `elem` cuando se inician los bucles **for** y **for** .

```cpp
// cl /EHsc /nologo /W4
#include <deque>
using namespace std;

int main()
{
    deque<double> dqDoubleData(10, 0.1);

    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)
    { /* ... */ }

    // prefer range-for loops with the following information in mind
    // (this applies to any range-for with auto, not just deque)

    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples
    { /* ... */ }

    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE
    { /* ... */ }

    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE
    { /* ... */ }
}
```

En el fragmento de código siguiente se usa el operador **New** y la declaración de puntero para declarar punteros.

```cpp
double x = 12.34;
auto *y = new auto(x), **z = new auto(&x);
```

En el fragmento de código siguiente se declaran varios símbolos en cada instrucción de declaración. Observe que todos los símbolos de cada instrucción se resuelven en el mismo tipo.

```cpp
auto x = 1, *y = &x, **z = &y; // Resolves to int.
auto a(2.01), *b (&a);         // Resolves to double.
auto c = 'a', *d(&c);          // Resolves to char.
auto m = 1, &n = m;            // Resolves to int.
```

En este fragmento de código se utiliza el operador condicional (`?:`) para declarar la variable `x` como un entero que tiene un valor de 200:

```cpp
int v1 = 100, v2 = 200;
auto x = v1 > v2 ? v1 : v2;
```

El siguiente fragmento de código inicializa la variable `x` al tipo **int**, la variable `y` a una referencia al tipo **const int**y la variable `fp` a un puntero a una función que devuelve el tipo **int**.

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto& y = f(1);
    int (*p)(int x);
    p = f;
    auto fp = p;
    //...
}
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../cpp/auto-keyword.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[/Zc:auto (Deducir tipo de variable)](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof (Operador)](../cpp/sizeof-operator.md)<br/>
[typeid](../extensions/typeid-cpp-component-extensions.md)<br/>
[operator new](new-operator-cpp.md)<br/>
[Declaraciones y definiciones](declarations-and-definitions-cpp.md)<br/>
[Ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[Inicializadores](../cpp/initializers.md)<br/>
[decltype](../cpp/decltype-cpp.md)
