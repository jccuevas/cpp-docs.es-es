---
title: Funciones (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
ms.openlocfilehash: 1425ddebffc150158e88e44b1d2c22e3f85e5a31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375739"
---
# <a name="functions-c"></a>Funciones (C++)

Una función es un bloque de código que realiza alguna operación. Una función puede definir opcionalmente parámetros de entrada que permiten a los llamadores pasar argumentos a la función. Una función también puede devolver un valor como salida. Las funciones son útiles para encapsular las operaciones comunes en un solo bloque reutilizable, idealmente con un nombre que describa claramente lo que hace la función. La siguiente función acepta dos enteros de un llamador y devuelve su suma; *a* y *b* son *parámetros* de tipo **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

La función se puede invocar, o *llamar*, desde cualquier número de lugares en el programa. Los valores que se pasan a la función son los *argumentos, cuyos*tipos deben ser compatibles con los tipos de parámetro en la definición de función.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

No hay ningún límite práctico para la longitud de la función, pero un buen diseño tiene como objetivo funciones que realizan una sola tarea bien definida. Los algoritmos complejos deben dividirse en funciones más sencillas y fáciles de comprender siempre que sea posible.

Las funciones definidas en el ámbito de clase se denominan funciones miembro. En C++, a diferencia de otros lenguajes, una función también pueden definirse en el ámbito de espacio de nombres (incluido el espacio de nombres global implícito). Estas funciones se denominan *funciones libres* o *funciones no miembro;* se utilizan ampliamente en la Biblioteca Estándar.

Las funciones pueden estar *sobrecargadas,* lo que significa que diferentes versiones de una función pueden compartir el mismo nombre si difieren por el número y/o tipo de parámetros formales. Para obtener más información, consulte [Sobrecarga de funciones](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Elementos de una declaración de función

Una *declaración* de función mínima consta del tipo de valor devuelto, el nombre de función y la lista de parámetros (que pueden estar vacíos), junto con palabras clave opcionales que proporcionan instrucciones adicionales al compilador. El ejemplo siguiente es una declaración de función:

```cpp
int sum(int a, int b);
```

Una definición de función consta de una declaración, más el *cuerpo*, que es todo el código entre las llaves:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Una declaración de función seguida de un punto y coma puede aparecer en varios lugares de un programa. Debe aparecer antes de cualquier llamada a esa función en cada unidad de traducción. La definición de función debe aparecer solo una vez en el programa, según la regla de una definición (ODR).

Los elementos necesarios de una declaración de función son los siguientes:

1. El tipo de valor devuelto, que especifica el tipo del valor que devuelve la función, o **void** si no se devuelve ningún valor. En C++11, **auto** es un tipo de valor devuelto válido que indica al compilador que deduzca el tipo de la instrucción return. En C++14, también se permite decltype(auto). Para obtener más información, consulte más adelante Deducción de tipos en tipos de valor devueltos.

1. El nombre de función, que debe comenzar con una letra o un carácter de subrayado y no puede contener espacios. En general, un carácter de subrayado inicial en los nombres de función de la biblioteca estándar indica funciones de miembro privado o funciones no miembro que no están pensadas para que las use el código.

1. La lista de parámetros, que es un conjunto delimitado por llaves y separado por comas de cero o más parámetros que especifican el tipo y, opcionalmente, un nombre local mediante el cual se puede acceder a los valores de dentro del cuerpo de la función.

Los elementos opcionales de una declaración de función son los siguientes:

1. `constexpr`, que indica que el valor devuelto de la función es un valor constante que se puede calcular en tiempo de compilación.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Su especificación de vinculación, **externa** o **estática.**

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   Para obtener más información, consulte Unidades de [traducción y vinculación](../cpp/program-and-linkage-cpp.md).

1. **en línea**, lo que indica al compilador que reemplace cada llamada a la función con el propio código de función. La inserción en línea puede mejorar el rendimiento en escenarios donde una función se ejecuta rápidamente y se invoca varias veces en una sección del código crítica para el rendimiento.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   Para obtener más información, consulte [Funciones en línea](../cpp/inline-functions-cpp.md).

1. Expresión, `noexcept` que especifica si la función puede producir una excepción o no. En el ejemplo siguiente, la función `is_pod` no produce una excepción si la expresión se evalúa como **true**.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   Para obtener más información, consulte [noexcept](../cpp/noexcept-cpp.md).

1. (Solo funciones miembro) Los calificadores cv, que especifican si la función es **const** o **volatile**.

1. (Solo funciones miembro) **virtual** `override`, `final`, o . **virtual** especifica que una función se puede invalidar en una clase derivada. `override` significa que una función de una clase derivada reemplaza una función virtual. `final` significa que una función no se puede reemplazar en ninguna otra clase derivada. Para obtener más información, consulte [Funciones virtuales](../cpp/virtual-functions.md).

1. (solo funciones miembro) **static** aplicado a una función miembro significa que la función no está asociada a ninguna instancia de objeto de la clase.

1. (Solo funciones miembro no estáticas) El ref-qualifier, que especifica al compilador qué sobrecarga de una función elegir cuando el parámetro de objeto implícito (esto)\*es una referencia rvalue frente a una referencia lvalue. Para obtener más información, consulte [Sobrecarga de funciones](function-overloading.md#ref-qualifiers).

La ilustración siguiente muestra las partes de una definición de función. El área sombreada es el cuerpo de la función.

![Elementos de una definición de función](../cpp/media/vc38ru1.gif "Elementos de una definición de función") <br/>
Elementos de una definición de función

## <a name="function-definitions"></a>Definiciones de función

Una definición de *función* consta de la declaración y el cuerpo de la función, entre llaves, que contiene declaraciones variables, instrucciones y expresiones. En el ejemplo siguiente se muestra una definición de función completa:

```cpp
    int foo(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       if(strcmp(s, "default") != 0)
       {
            value = mc.do_something(i);
       }
       return value;
    }
```

Las variables declaradas dentro del cuerpo se denominan variables locales. Se salen del ámbito cuando finaliza la función; por lo tanto, una función nunca debe devolver una referencia a una variable local.

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>funciones const y constexpr

Puede declarar una función miembro como **const** para especificar que la función no puede cambiar los valores de los miembros de datos de la clase. Al declarar una función miembro como **const**, ayuda al compilador a aplicar *const-correctness*. Si alguien intenta modificar por error el objeto mediante una función declarada como **const**, se genera un error del compilador. Para obtener más información, consulte [const](const-cpp.md).

Declare una `constexpr` función como cuando el valor que produce posiblemente se puede determinar en tiempo de compilación. Una función constexpr generalmente se ejecuta más rápido que una función normal. Para obtener más información, consulte [constexpr](constexpr-cpp.md).

## <a name="function-templates"></a>Plantillas de función

Una plantilla de función es parecida a una plantilla de clase; genera funciones concretas que se basan en los argumentos de plantilla. En muchos casos, la plantilla es capaz de inferir los argumentos de tipo, por lo que no es necesario especificarlos de forma explícita.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs;
}

auto a = Add2(3.13, 2.895); // a is a double
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string
```

Para obtener más información, consulte [Plantillas de función](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>Parámetros de función y argumentos

Una función tiene una lista de parámetros separados por comas de cero o más tipos, cada uno de los cuales tiene un nombre mediante el cual se puede acceder a ellos dentro del cuerpo de la función. Una plantilla de función puede especificar parámetros adicionales de tipo de valor. El llamador pasa argumentos, que son valores concretos cuyos tipos son compatibles con la lista de parámetros.

De forma predeterminada, los argumentos se pasan a la función por valor, lo que significa que la función recibe una copia del objeto que se pasa. En el caso de los objetos grandes, puede resultar costoso realizar una copia y no siempre es necesario. Para hacer que los argumentos se pasen por referencia (específicamente lvalue reference), agregue un cuantificador de referencia al parámetro:

```cpp
void DoSomething(std::string& input){...}
```

Cuando una función modifica un argumento que se pasa por referencia, modifica el objeto original, no una copia local. Para evitar que una función modifique un argumento de este tipo, califique el parámetro como const&:

```cpp
void DoSomething(const std::string& input){...}
```

**C++ 11:**  Para controlar explícitamente los argumentos que se pasan mediante rvalue-reference o lvalue-reference, utilice un double-ampersand en el parámetro para indicar una referencia universal:

```cpp
void DoSomething(const std::string&& input){...}
```

Una función declarada con la palabra clave single **void** en la lista de declaraciones de parámetros no toma ningún argumento, siempre y cuando la palabra clave **void** sea el primer y único miembro de la lista de declaraciones de argumento. Los argumentos de tipo **void** en otra parte de la lista producen errores. Por ejemplo:

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Tenga en cuenta que, aunque es ilegal especificar un argumento **void** excepto como se describe aquí, los tipos derivados del tipo **void** (como punteros a **void** y matrices de **void**) pueden aparecer en cualquier lugar de la lista de declaraciones de argumento.

### <a name="default-arguments"></a>Argumentos predeterminados

Es posible asignar un argumento predeterminado al último parámetro o parámetros de una firma de función, lo que significa que el llamador puede omitir el argumento cuando se llama a la función, a menos que desee especificar otro valor.

```cpp
int DoSomething(int num,
    string str,
    Allocator& alloc = defaultAllocator)
{ ... }

// OK both parameters are at end
int DoSomethingElse(int num,
    string str = string{ "Working" },
    Allocator& alloc = defaultAllocator)
{ ... }

// C2548: 'DoMore': missing default parameter for parameter 2
int DoMore(int num = 5, // Not a trailing parameter!
    string str,
    Allocator& = defaultAllocator)
{...}
```

Para obtener más información, vea [Argumentos predeterminados](../cpp/default-arguments.md).

## <a name="function-return-types"></a>Tipos de valor devuelto de función

Una función no puede devolver otra función o una matriz integrada; sin embargo, puede devolver punteros a estos tipos, o una *expresión lambda*, que genera un objeto de función. Excepto en estos casos, una función puede devolver un valor de cualquier tipo que esté en el ámbito, o puede devolver ningún valor, en cuyo caso el tipo de valor devuelto es **void**.

### <a name="trailing-return-types"></a>Tipos de valor devueltos finales

Un tipo de valor devuelto "normal" se encuentra en el lado izquierdo de la firma de función. Un tipo de *valor devuelto final* se encuentra en la parte derecha de la firma y va precedido por el operador ->. Los tipos de valor devueltos finales son especialmente útiles en plantillas de función cuando el tipo del valor devuelto depende de los parámetros de plantilla.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Cuando **auto** se utiliza junto con un tipo de valor devuelto final, solo sirve como marcador de posición para lo que produce la expresión decltype y no realiza por sí mismo la deducción de tipos.

## <a name="function-local-variables"></a>Variables locales de función

Una variable que se declara dentro de un cuerpo de función se denomina *variable local* o simplemente *local.* Las variables locales no estáticas solo son visibles dentro del cuerpo de función y, si se declaran en la pila, se salen del ámbito cuando finaliza la función. Cuando se construye una variable local y se devuelve por valor, el compilador normalmente puede realizar la *optimización* del valor devuelto con nombre para evitar operaciones de copia innecesarias. Si una variable local se devuelve por referencia, el compilador emitirá una advertencia, ya que cualquier intento por parte del llamador de usar esa referencia se producirá después de la destrucción de la variable local.

En C++, una variable local se puede declarar como estática. La variable solo es visible dentro del cuerpo de la función, pero existe una copia única de la variable para todas las instancias de la función. Los objetos estáticos locales se destruyen durante la finalización especificada por `atexit`. Si no se crea un objeto estático porque el flujo de control de programa omitió su declaración, no se realiza ningún intento de destruir ese objeto.

## <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>Deducción de tipo en tipos de valor devuelto (C++14)

En C++14, puede usar **auto** para indicar al compilador que deduzca el tipo de valor devuelto del cuerpo de la función sin tener que proporcionar un tipo de valor devuelto final. Tenga en cuenta que **auto** siempre deduce a un retorno por valor. Use `auto&&` para indicar al compilador que deduzca una referencia.

En este ejemplo, **auto** se deducirá como una copia del valor no const de la suma de lhs y rhs.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Tenga en cuenta que **auto** no conserva la const-ness del tipo que deduce. Para las funciones de reenvío cuyo valor devuelto necesita conservar la const-ness o ref-ness de sus argumentos, puede utilizar la palabra clave **decltype(auto),** que utiliza las reglas de inferencia de tipo **decltype** y conserva toda la información de tipo. **decltype(auto)** se puede utilizar como un valor devuelto normal en el lado izquierdo, o como un valor devuelto final.

En el ejemplo siguiente (basado en código de [N3493](https://wg21.link/n3493)), se muestra **decltype(auto)** que se utiliza para habilitar el reenvío perfecto de argumentos de función en un tipo de valor devuelto que no se conoce hasta que se crea una instancia de la plantilla.

```cpp
template<typename F, typename Tuple = tuple<T...>, int... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return std::forward<F>(f)(std::get<I>(std::forward<Tuple>(args))...);
}

template<typename F, typename Tuple = tuple<T...>,
    typename Indices = make_index_sequence<tuple_size<Tuple>::value >>
   decltype( auto)
    apply(F&& f, Tuple&& args)
{
    return apply_(std::forward<F>(f), std::forward<Tuple>(args), Indices());
}
```

## <a name="returning-multiple-values-from-a-function"></a><a name="multi_val"></a>Devolver varios valores de una función

Hay varias maneras de devolver más de un valor de una función:

1. Encapsular los valores en una clase con nombre o un objeto struct. Requiere que la definición de clase o estructura sea visible para el autor de la llamada:

    ```cpp
    #include <string>
    #include <iostream>

    using namespace std;

    struct S
    {
        string name;
        int num;
    };

    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }

    int main()
    {
        S s = g();
        cout << s.name << " " << s.num << endl;
        return 0;
    }
    ```

1. Devuelve un objeto std::tple o std::pair:

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>

    using namespace std;

    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }

    int main()
    {
        auto t = f();
        cout << get<0>(t) << " " << get<1>(t) << " " << get<2>(t) << endl;

        // --or--

        int myval;
        string myname;
        double mydecimal;
        tie(myval, myname, mydecimal) = f();
        cout << myval << " " << myname << " " << mydecimal << endl;

        return 0;
    }
    ```

1. **Visual Studio 2017 versión 15.3 y versiones posteriores** (disponible con [/std:c++17](../build/reference/std-specify-language-standard-version.md)): Usar enlaces estructurados. La ventaja de los enlaces estructurados es que las variables que almacenan los valores devueltos se inicializan al mismo tiempo que se declaran, lo que en algunos casos puede ser significativamente más eficaz. En esta`auto[x, y, z] = f();`instrucción -- -- los corchetes introducen e inicializan nombres que están en el ámbito de todo el bloque de funciones.

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>

    using namespace std;

    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }
    struct S
    {
        string name;
        int num;
    };

    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }

    int main()
    {
        auto[x, y, z] = f(); // init from tuple
        cout << x << " " << y << " " << z << endl;

        auto[a, b] = g(); // init from POD struct
        cout << a << " " << b << endl;
        return 0;
    }
    ```

1. Además de utilizar el propio valor devuelto, puede "devolver" valores definiendo cualquier número de parámetros para usar el paso por referencia para que la función pueda modificar o inicializar los valores de los objetos que proporciona el llamador. Para obtener más información, vea Argumentos de [función de tipo de referencia](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Punteros de función

C++ admite punteros de función de la misma manera que el lenguaje C. Sin embargo, una alternativa con mayor seguridad de tipos suele ser usar un objeto de función.

Se recomienda que **typedef** se use para declarar un alias para el tipo de puntero de función si se declara una función que devuelve un tipo de puntero de función.  Por ejemplo

```cpp
typedef int (*fp)(int);
fp myFunction(char* s); // function returning function pointer
```

Si no es así, la sintaxis correcta para la declaración de la función se puede deducir de la sintaxis de declarador del puntero a función, mediante la sustitución del identificador (`fp` en el ejemplo anterior) por el nombre y la lista de argumentos de las funciones, como sigue:

```cpp
int (*myFunction(char* s))(int);
```

La declaración anterior es equivalente a la otra declaración con typedef.

## <a name="see-also"></a>Consulte también

[Sobrecarga de funciones](../cpp/function-overloading.md)<br/>
[Funciones con listas de argumentos variables](../cpp/functions-with-variable-argument-lists-cpp.md)<br/>
[Funciones establecidas como valor predeterminado y eliminadas explícitamente](../cpp/explicitly-defaulted-and-deleted-functions.md)<br/>
[Búsqueda de nombres dependientes de argumentos (Koenig) en las funciones](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)<br/>
[Argumentos predeterminados](../cpp/default-arguments.md)<br/>
[Funciones insertadas](../cpp/inline-functions-cpp.md)
