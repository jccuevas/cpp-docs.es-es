---
title: automático (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f38c4cdfcbb75cd4c2df4fadd10cfcaccda4540e
ms.sourcegitcommit: a88d228480d4bb5834e985d7b3ead2760be95572
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50203071"
---
# <a name="auto-c"></a>automático (C++)

Deduce el tipo de una variable declarada a partir de su expresión de inicialización.

## <a name="syntax"></a>Sintaxis

```
auto declarator initializer;
```

```
[](auto param1, auto param2) {};
```

## <a name="remarks"></a>Comentarios

El **automática** palabra clave indica al compilador que utilice la expresión de inicialización de una variable declarada o el parámetro de expresión lambda para deducir su tipo.

Se recomienda que use el **automática** palabra clave para la mayoría de los casos, a menos que desee realmente una conversión, porque proporciona estas ventajas:

- **Solidez:** si se cambia el tipo de expresión, esto incluye cuando se cambia un tipo de valor devuelto de función, simplemente funciona.

- **Rendimiento:** se garantiza que no habrá ninguna conversión.

- **Facilidad de uso:** no tiene que preocuparse por nombre tipo las dificultades y los errores tipográficos.

- **Eficiencia:** la codificación puede ser más eficaz.

Casos de conversión en el que es posible que no desea utilizar **automática**:

- Cuando se desea un tipo específico y es la única alternativa.

- Tipos de aplicación auxiliar de plantilla de expresión, por ejemplo, `(valarray+valarray)`.

Para usar el **automática** palabra clave, utilizarlo en lugar de un tipo para declarar una variable y especifique una expresión de inicialización. Además, puede modificar el **automática** palabra clave mediante especificadores y declaradores como **const**, **volátil**, puntero (`*`), referencia (`&`) y la referencia rvalue (`&&`). El compilador evalúa la expresión de inicialización y emplea esa información para deducir el tipo de la variable.

La expresión de inicialización puede ser una asignación (sintaxis de signo igual), una inicialización directa (sintaxis de estilo de función), un [new (operador)](new-operator-cpp.md) expresión o la expresión de inicialización puede ser el  *declaración de rango* parámetro en un [basada en intervalo para la instrucción (C++)](../cpp/range-based-for-statement-cpp.md) instrucción. Para obtener más información, consulte [inicializadores](../cpp/initializers.md) y los ejemplos de código más adelante en este documento.

El **automática** palabra clave es un marcador de posición para un tipo, pero no es sí misma un tipo. Por lo tanto, el **automática** palabra clave no se puede usar en conversiones o en operadores como [sizeof](../cpp/sizeof-operator.md) y [typeid](../windows/typeid-cpp-component-extensions.md).

## <a name="usefulness"></a>Utilidad

El **automática** palabra clave es una manera sencilla de declarar una variable que tiene un tipo complejo. Por ejemplo, puede usar **automática** para declarar una variable donde la expresión de inicialización implica plantillas, punteros a funciones o punteros a miembros.

También puede usar **automática** para declarar e inicializar una variable a una expresión lambda. No puede declarar el tipo de la variable porque solo el compilador conoce el tipo de una expresión lambda. Para obtener más información, consulte [ejemplos de expresiones Lambda](../cpp/examples-of-lambda-expressions.md).

## <a name="trailing-return-types"></a>Tipos de valor devuelto finales

Puede usar **automática**, junto con el **decltype** especificador, como ayuda para escribir bibliotecas de plantillas de tipo. Use **automática** y **decltype** para declarar una función de plantilla cuyo valor devuelto tipo depende de los tipos de sus argumentos de plantilla. O bien, use **automática** y **decltype** para declarar una función de plantilla que contiene una llamada a otra función y, a continuación, devuelve todo lo que es el tipo de valor devuelto de esa otra función. Para obtener más información, consulte [decltype](../cpp/decltype-cpp.md).

## <a name="references-and-cv-qualifiers"></a>Referencias y calificadores cv

Tenga en cuenta que el uso **automática** quita las referencias, los calificadores const y volatile calificadores. Considere el ejemplo siguiente:

```cpp
// cl.exe /analyze /EHsc /W4
#include <iostream>

using namespace std;

int main( )
{
    int count = 10;
    int& countRef = count;
    auto myAuto = countRef;

    countRef = 11;
    cout << count << " ";

    myAuto = 12;
    cout << count << endl;
}

```

En el ejemplo anterior, myAuto es un entero, no una referencia int, por lo que es la salida `11 11`, no `11 12` como sería el caso si no hubiera quitado el calificador de referencia **automática**.

## <a name="type-deduction-with-braced-initializers-c14"></a>Deducción de tipos con inicializadores entre llaves (C ++ 14)

El ejemplo de código siguiente muestra cómo inicializar una variable automática mediante llaves. Tenga en cuenta la diferencia entre B y C y entre A y E.

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

En la tabla siguiente se enumera las restricciones sobre el uso de la **automática** palabra clave y el correspondiente mensaje de error de diagnóstico que emite el compilador.

|Número de error|Descripción|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|El **automática** palabra clave no se puede combinar con ningún otro especificador de tipo.|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Un símbolo que se declara con el **automática** palabra clave debe tener un inicializador.|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Utilizó incorrectamente la **automática** palabra clave para declarar un tipo. Por ejemplo, declaró un tipo de valor devuelto de método o una matriz.|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|No se puede declarar un argumento de parámetro o de plantilla con el **automática** palabra clave.|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|No se puede declarar un parámetro de método o una plantilla con el **automática** palabra clave.|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|No se puede usar un símbolo antes de inicializarlo. En la práctica, esto significa que una variable no se puede usar para inicializarse a sí misma.|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|No se puede convertir a un tipo que se declara con el **automática** palabra clave.|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Todos los símbolos en una lista de declaradores que se declara con el **automática** palabra clave debe resolverse en el mismo tipo. Para obtener más información, consulte [declaraciones y definiciones](declarations-and-definitions-cpp.md).|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|El [sizeof](../cpp/sizeof-operator.md) y [typeid](../windows/typeid-cpp-component-extensions.md) operadores no se puede aplicar a un símbolo que se declara con el **automática** palabra clave.|

## <a name="examples"></a>Ejemplos

Estos fragmentos de código muestran algunas de las formas en que el **automática** se puede usar la palabra clave.

Las declaraciones siguientes son equivalentes. En la primera instrucción variable `j` se declara como tipo **int**. En la segunda instrucción variable `k` se deduce a ser de tipo **int** porque la expresión de inicialización (0) es un entero.

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

Las declaraciones siguientes son equivalentes, pero la segunda declaración es más sencilla que la primera. Una de las razones más atractivas para usar el **automática** palabra clave es la simplicidad.

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

El fragmento de código siguiente declara el tipo de variables `iter` y `elem` cuando el **para** e intervalo **para** bucles de inicio.

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

El siguiente fragmento de código utiliza el **nuevo** declaración del operador y el puntero para declarar punteros.

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

El siguiente fragmento de código inicializa la variable `x` escriba **int**variable `y` a una referencia al tipo **const int**y la variable `fp` a un puntero a una función que devuelve el tipo **int**.

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto & y = f(1);
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
[sizeof (operador)](../cpp/sizeof-operator.md)<br/>
[typeid](../windows/typeid-cpp-component-extensions.md)<br/>
[operator new](new-operator-cpp.md)<br/>
[Declaraciones y definiciones](declarations-and-definitions-cpp.md)<br/>
[Ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[Inicializadores](../cpp/initializers.md)<br/>
[decltype](../cpp/decltype-cpp.md)
