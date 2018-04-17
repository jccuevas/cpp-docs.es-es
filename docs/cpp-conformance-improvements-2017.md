---
title: Mejoras de conformidad de C++ | Microsoft Docs
ms.custom: ''
ms.date: 03/11/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce15db75d4d08ef128e561fa9671b643946c71c3
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="c-conformance-improvements-in-visual-studio-2017-versions-150-153improvements153-155improvements155-156improvements156-and-157improvements157"></a>Mejoras de conformidad de C++ en las versiones 15.0, [15.3](#improvements_153), [15.5](#improvements_155), [15.6](#improvements_156) y [15.7](#improvements_157) de Visual Studio 2017

Gracias a la compatibilidad de constexpr generalizado y NSDMI con los agregados, el compilador de Microsoft Visual C++ ya tiene la totalidad de las características que se agregaron en el estándar C++14. Tenga en cuenta que al compilador todavía le faltan algunas características de los estándares C++11 y C++98. Consulte [Visual C++ Language Conformance](visual-cpp-language-conformance.md) (Conformidad del lenguaje Visual C++) para ver una tabla que muestra el estado actual del compilador.

## <a name="c11"></a>C++11
### <a name="expression-sfinae-support-in-more-libraries"></a>Compatibilidad con expresiones SFINAE en más bibliotecas

El compilador sigue mejorando su compatibilidad con la expresión SFINAE, necesaria para la deducción y sustitución de argumentos de plantilla donde las expresiones decltype y constexpr puedan aparecer como parámetros de plantilla. Para más información, vea [Expression SFINAE improvements in Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3) (Mejoras de la expresión SFINAE en Visual Studio 2017 RC).

## <a name="c-14"></a>C++14

### <a name="nsdmi-for-aggregates"></a>NSDMI para agregados

Un agregado es una matriz o una clase sin ningún constructor proporcionado por el usuario, ningún miembro de datos no estático privado o protegido, ninguna clase base y ninguna función virtual. A partir de C++14, los agregados pueden contener inicializadores de miembro. Para más información, vea [Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html) (Inicializadores de miembro y agregados).

### <a name="extended-constexpr"></a>constexpr extendido
Las expresiones declaradas como constexpr ya pueden contener determinados tipos de declaraciones, instrucciones if y switch, instrucciones loop y mutación de objetos cuya duración se haya iniciado durante la evaluación de la expresión constexpr. Además, ya no es necesario que una función miembro no estática constexpr sea const de forma implícita. Para más información, vea [Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html) (Relajación de restricciones en funciones constexpr).

## <a name="c17"></a>C++17

### <a name="terse-staticassert"></a>static_assert breve

El parámetro de mensaje para static_assert es opcional. Para más información, vea [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf) (Extensión de static_assert, v2).

### <a name="fallthrough-attribute"></a>Atributo [[fallthrough]]

En el modo **/std:c++17**, el atributo [[fallthrough]] se puede usar en el contexto de las instrucciones switch como una sugerencia al compilador de que se prevé el comportamiento de paso explícito. Esto evita que el compilador emita advertencias en estos casos. Para más información, vea [Wording for [[fallthrough]] attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf) (Lenguaje para el atributo [[fallthrough]]).

### <a name="generalized-range-based-for-loops"></a>Bucles for basados en intervalos generalizados

Los bucles for basados en rangos ya no necesitan que las funciones begin() y end() devuelvan objetos del mismo tipo. Así, se permite que end() devuelva un valor de centinela tal como usan los rangos de [range-v3](https://github.com/ericniebler/range-v3) y la especificación técnica de rangos completada pero no publicada. Para obtener más información, vea [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) (Generalización del bucle for basado en rangos).

## <a name="improvements_153"></a> Mejoras de la versión 15.3 de Visual Studio 2017

### <a name="constexpr-lambdas"></a>Expresiones lambda de constexpr

Las expresiones lambda ahora se pueden usar en expresiones constantes. Para más información, consulte el artículo sobre [lambda de constexpr](http://open-std.org/JTC1/SC22/WG21/docs/papers/2015/n4487.pdf).

### <a name="if-constexpr-in-function-templates"></a>if constexpr en plantillas de función

Una plantilla de función puede contener instrucciones `if constexpr` que habilitan la creación de ramas de tiempo de compilación. Para más información, consulte el artículo sobre [if constexpr](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0128r1.html).

### <a name="selection-statements-with-initializers"></a>Instrucciones de selección con inicializadores

Una instrucción `if` puede incluir un inicializador que introduce una variable en el ámbito de bloque dentro de la instrucción misma. Para más información, consulte [Instrucciones de selección con inicializadores](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0305r1.html).

### <a name="maybeunused-and-nodiscard-attributes"></a>Atributos [[maybe_unused]] y [[nodiscard]]

Atributos nuevos para silenciar las advertencias cuando no se usa una entidad o para crear una advertencia si se descarta el valor devuelto de una llamada de función. Para más información, consulte la [redacción para el atributo maybe_unused](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0212r0.pdf) y la [propuesta de atributos unused, nodiscard y fallthrough](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf).

### <a name="using-attribute-namespaces-without-repetition"></a>Uso de espacios de nombres de atributo sin repetición

Nueva sintaxis para habilitar solo un identificador de espacio de nombres único en una lista de atributos. Para más información, consulte [Atributos en C++](cpp/attributes.md).

### <a name="structured-bindings"></a>Enlaces estructurados

En una sola declaración ahora es posible almacenar un valor con nombres individuales para sus componentes, cuando el valor es una matriz, un std::tuple o std::pair o tiene todos los miembros de datos no estáticos públicos. Para más información, consulte [Enlaces estructurados](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf).

### <a name="construction-rules-for-enum-class-values"></a>Reglas de construcción para valores de enum class

Ahora existe una conversión implícita y no restrictiva desde el tipo subyacente de una enumeración con ámbito a la enumeración misma, cuando su definición no introduce enumerador y el origen usa una sintaxis de inicialización de lista. Para más información, consulte [Reglas de construcción para valores de enum class](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf).

### <a name="capturing-this-by-value"></a>Captura de *this por valor

El objeto `*this` en una expresión lambda ahora se puede capturar por valor. Esto permite escenarios en los que se invoca la expresión lambda en operaciones asincrónicas y en paralelo, en particular en las arquitecturas de máquinas más recientes. Para más información, consulte la [captura de lambda de \*this por valor como [=,\*this]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

### <a name="removing-operator-for-bool"></a>Eliminación del operator++ para bool

`operator++` ya no se admite en tipos `bool`. Para más información, consulte el artículo sobre la [elimininación de operator++(bool) en desuso](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

### <a name="removing-deprecated-register-keyword"></a>Eliminación de la palabra clave "register" en desuso

La palabra clave `register`, anteriormente en desuso (e ignorada por el compilador), ahora se ha eliminado del idioma. Para más información, consulte el artículo sobre la [eliminación del uso de la palabra clave register en desuso](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

Para obtener una lista completa de las mejoras de conformidad hasta Visual Studio 2015, Update 3, vea [Visual C++ What's New 2003 through 2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx) (Novedades de Visual C++ de 2003 a 2015).

## <a name="improvements_155"></a> Mejoras de la versión 15.5 de Visual Studio 2017

Las características marcadas con [14] están disponibles sin condiciones, incluso en el modo **/std:c++14**.

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nuevo conmutador de compilador para extern constexpr

En versiones anteriores de Visual Studio, el compilador siempre proporcionaba una vinculación interna de variable de `constexpr` aunque la variable se marcase como `extern`. En la versión 15.5 de Visual Studio 2017, un nuevo conmutador de compilador, [/Zc:externConstexpr](build/reference/zc-externconstexpr.md), permite un comportamiento correcto que cumple con los estándares. Para obtener más información, vea [Extern constexpr linkage](#extern_linkage) (Vinculación de extern constexpr).

### <a name="removing-dynamic-exception-specifications"></a>Eliminación de las especificaciones de excepciones dinámicas

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html) Las especificaciones de excepción dinámica se dejaron en desuso en C++11. La característica se quitó de C++17, pero la especificación `throw()`, que (todavía) está en desuso, se conserva estrictamente como un alias de `noexcept(true)`. Para obtener más información, vea [Eliminación de las especificaciones de excepción dinámica y noexcept](#noexcept_removal). 

### <a name="notfn"></a>not_fn()

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` es un sustituto de `not1` y `not2`.

### <a name="rewording-enablesharedfromthis"></a>Nueva redacción de enable_shared_from_this

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` se agregó en C++11. En la versión estándar de C++17 se actualiza la especificación para controlar mejor determinados casos extremos. [14]

### <a name="splicing-maps-and-sets"></a>Inserción de asignaciones y conjuntos

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) Esta característica permite la extracción de nodos de los contenedores asociativos (por ejemplo, map, set, unordered\_map y unordered\_set) que posteriormente se pueden modificar y volver a insertar en el mismo contenedor o en otro que use el mismo tipo de nodo. Un caso de uso habitual es extraer un nodo de un `std::map`, cambiar la clave y volverlo a insertar.

### <a name="deprecating-vestigial-library-parts"></a>Desuso de vestigios de elementos de biblioteca

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) Varias características de la biblioteca estándar de C++ se han reemplazado por nuevas características a lo largo de los años, o bien se ha detectado que eran problemáticas o no eran muy útiles. Estas características están oficialmente en desuso en C++17. 

### <a name="removing-allocator-support-in-stdfunction"></a>Eliminación de la compatibilidad con el asignador en std::function

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) Antes de C++17, la plantilla de clase `std::function` tenía varios constructores que usaban un argumento allocator. Sin embargo, el uso de argumentos allocator en este contexto era problemático, y la semántica no era clara. Por lo tanto, estos constructores se quitaron.

### <a name="fixes-for-notfn"></a>Correcciones para not_fn()

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html) La nueva redacción de `std::not_fn` ofrece más posibilidades para la propagación de categorías de valor en caso de que haya una invocación de contenedores.

### <a name="sharedptrt-sharedptrtn"></a>shared_ptr\<T[]>, shared_ptr\<T[N]>

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) Los cambios de `shared_ptr` de Elementos fundamentales de biblioteca se combinan en C++17. [14]

### <a name="fixing-sharedptr-for-arrays"></a>Corrección de shared_ptr para matrices

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) Correcciones de la compatibilidad de shared_ptr con las matrices. [14]

### <a name="clarifying-insertreturntype"></a>Aclaración de insert_return_type

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) Los contenedores asociativos con claves únicas y los contenedores desordenados con claves únicas tienen una función de miembro `insert` que devuelve el tipo anidado `insert_return_type`. Ahora, este tipo de valor devuelto se define como la especialización de un tipo parametrizado en las propiedades Iterator y NodeType del contenedor.

### <a name="inline-variables-for-the-stl"></a>Variables alineadas para STL

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>Características de anexo D en desuso

El anexo D de la versión estándar de C++ contiene todas las características que están en desuso, como `shared_ptr::unique()`, `<codecvt>` y `namespace std::tr1`. Cuando se establece el compilador **/std:c++17**, casi todas las características de la biblioteca estándar que hay en el anexo D se marcan como en desuso. Para obtener más información, vea el artículo [Las características de la biblioteca estándar que hay en el anexo D se han marcado como en desuso](#annex_d).

El espacio de nombres `std::tr2::sys` de `<experimental/filesystem>` ahora emite una advertencia de desuso en **/std:c++14** de forma predeterminada, y se ha eliminado de **/std:c++17** de forma predeterminada.

Se ha mejorado la conformidad con iostreams evitando una extensión no estándar (especializaciones explícitas in-class).

La biblioteca estándar ahora usa plantillas de variables de forma interna.

La biblioteca estándar se ha actualizado de acuerdo con los cambios en el compilador de C++17. Por ejemplo, se ha agregado noexcept en el sistema de tipo y se han eliminado las especificaciones de excepción dinámica.

## <a name="improvements_156"></a> Mejoras de la versión 15.6 de Visual Studio 2017

### <a name="c17-library-fundamentals-v1"></a>Elementos fundamentales de biblioteca para C++17 V1

[P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) incorpora especificaciones técnicas de elementos fundamentales de biblioteca para C++17 en el estándar. Afecta a las actualizaciones de \<experimental/tuple>, \<experimental/optional>, \<experimental/functional>, \<experimental/any>, \<experimental/string_view> , \<experimental/memory>, \<experimental/memory_resource> y \<experimental/algorithm>.

### <a name="c17-improving-class-template-argument-deduction-for-the-stl"></a>Mejora de la deducción de argumentos de plantilla de clase para STL para C++17

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) desplaza `adopt_lock_t` al frente de la lista de parámetros para que `scoped_lock` pueda permitir un uso coherente de `scoped_lock`. También se permite que el constructor `std::variant` participe en la resolución de sobrecarga en más casos con el fin de habilitar la asignación de copias.

## <a name="improvements_157"></a> Mejoras de la versión 15.7 de Visual Studio 2017

### <a name="c17-rewording-inheriting-constructors"></a>Nueva redacción de constructores de herencia para C++17

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) especifica que una declaración **using** que designa a un constructor ahora hace que los constructores de la clase base correspondientes sean visibles para las inicializaciones de la clase derivada, en lugar de declarar constructores de la clase derivada adicionales. Este comportamiento es diferente con respecto a C++14. En la versión 15.7 de Visual Studio 2017 y en las posteriores, en el modo **/std:c++17**, el código válido en C++14 y que usa constructores de herencia puede no ser válido o es posible que tenga otras semánticas.

En el ejemplo siguiente se muestra el comportamiento de C++14:

```cpp

struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n) = delete; // Error C2280
};

B b(42L); // Calls B<long>(long), which calls A(int)
          //  due to substitution failure in A<long>(long).
```

En el ejemplo siguiente se muestra el comportamiento de **/std:c++17** en Visual Studio 15.7:

```cpp

struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n)
    {
        //do something
    }
};

B b(42L); // now calls B(int)

```

### <a name="c17-extended-aggregate-initialization"></a>Inicialización de agregados extendidos para C++17

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

Si el constructor de una clase base no es público, pero accesible para una clase derivada, en el modo **/std:c++17** de la versión 15.7 de Visual Studio ya no se pueden usar llaves vacías para inicializar un objeto del tipo derivado.

En el ejemplo siguiente se muestra el comportamiento correspondiente de C++14:

```cpp

struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived() 
               // which can call Base ctor.

```

En C++17, `Derived` ahora se considera un tipo de agregado. Así, la inicialización de `Base` mediante el constructor privado predeterminado se produce directamente como parte de la regla de inicialización de agregados extendida. Anteriormente, el constructor privado `Base` se llamaba a través del constructor `Derived` y se realizaba correctamente debido a la declaración friend.

En el ejemplo siguiente se muestra el comportamiento de C++17 en la versión 15.7 de Visual Studio en el modo **/std:c++17**:

```cpp

struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor 
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access 
               // private member declared in class 'Base'

```

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>Declaración de parámetros de plantilla sin tipo con auto para C++17

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

En el modo **/std:c++17**, el compilador ahora puede deducir el tipo de un argumento de plantilla que no sea del tipo que se declara con **auto**:

```cpp

template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char

```

Una de las consecuencias que presenta esta nueva característica es que el código válido para C++14 puede no ser válido o tener otra semántica. Por ejemplo, algunas sobrecargas que no eran válidas anteriormente ahora lo son. En el ejemplo siguiente se muestra código de C++14 que se compila porque la llamada a `foo(p)` está enlazada a `foo(void*);`. En la versión 15.7 de Visual Studio 2017, en el modo **/std:c++17**, la plantilla de función `foo` es la mejor coincidencia. 

```c++

template <int N> struct A;
template <typename T, T N> int foo(A<N>*) = delete;

void foo(void *);

void bar(A<0> *p)
{
    foo(p); // OK in C++14
}

```

En el ejemplo siguiente se muestra código de C++17 en Visual Studio 15.7 en el modo **/std:c ++ 17**:


```cpp

template <int N> struct A;
template <typename T, T N> int foo(A<N>*);

void foo(void *);

void bar(A<0> *p)
{
    foo(p); // C2280: 'int foo<int,0>(A<0>*)': attempting to reference a deleted function
}

```

### <a name="c17-elementary-string-conversions-partial"></a>Conversiones de cadenas elementales para C++17 (parcial)

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html) incluye funciones de bajo nivel e independientes de la configuración regional para las conversiones entre cadenas y enteros, así como entre cadenas y números de punto flotante. (A partir de Visual Studio 15.7 Preview 2, solo es compatible con enteros).

### <a name="c20-avoiding-unnecessary-decay-partial"></a>Evitar "decay" no necesarios para C++20 (parcial)

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) agrega diferenciación entre el concepto de "decay" y el de la eliminación de los calificadores const o reference.  El nuevo rasgo de tipo `remove_reference_t` reemplaza `decay_t` en algunos contextos. Todavía no se ha implementado la compatibilidad con `remove_cvref_t` en la versión 15.7 Preview 2 de Visual Studio 2017.

### <a name="c17-parallel-algorithms"></a>Algoritmos paralelos para C++17

En [P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html), el TS de paralelismo se incorpora en el estándar con modificaciones menores.

### <a name="c17-hypotx-y-z"></a>hypot(x, y, z) para C++17

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf) agrega tres nuevas sobrecargas a `std::hypot`, para los tipos **float**, **double** y **long double**, cada uno de los cuales tiene tres parámetros de entrada.

### <a name="c17-filesystem"></a>\<filesystem> para C++17

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html) adopta el TS del sistema de archivos en el estándar con algunas modificaciones de redacción.

### <a name="c17-mathematical-special-functions"></a>Funciones matemáticas especiales para C++17

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) adopta especificaciones técnicas anteriores para funciones matemáticas especiales en el encabezado \<cmath> estándar.

### <a name="c17-deduction-guides-for-the-stl"></a>Guías de deducción para STL para C++17

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) se actualiza a STL para aprovechar las ventajas de la adopción de C++17 de [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), que agrega compatibilidad con la deducción de argumentos de plantilla de clase.

### <a name="c17-repairing-elementary-string-conversions"></a>Reparación de conversiones de cadenas elementales para C++17

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html) desplaza las nuevas funciones de conversión de cadenas elementales de P0067R5 a un nuevo encabezado \<charconv>. También presenta otras mejoras, incluido el cambio de control de errores para usar `std::errc` en lugar de `std::error_code`.

### <a name="c17-constexpr-for-chartraits-partial"></a>constexpr para char_traits para C++17 (parcial)

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html) incluye cambios relativos a las funciones `length`, `compare` y `find` del miembro `std::traits_type` con el fin de que se pueda usar `std::string_view` en expresiones constantes. (En la versión 15.6 de Visual Studio 2017 solo se admite para Clang/LLVM. En la versión 15.7 Preview 2, la compatibilidad es casi completa con CIXX también).

## <a name="bug-fixes-in-visual-studio-versions-150-153update153-155update155-and-157update157"></a>Correcciones de errores en las versiones 15.0, [15.3](#update_153), [15.5](#update_155) y [15.7](#update_157) de Visual Studio

### <a name="copy-list-initialization"></a>Inicialización de lista de copia

Visual Studio 2017 genera correctamente errores del compilador relacionados con la creación de objetos mediante listas del inicializador que en Visual Studio 2015 no se detectaban y podían provocar bloqueos o un comportamiento en tiempo de ejecución no definido. Conforme a N4594 13.3.1.7p1, en la inicialización de lista de copia el compilador debe tener en cuenta un constructor explícito para la resolución de sobrecarga, pero debe generar un error si se elige realmente esa sobrecarga.

Los dos ejemplos siguientes se compilan en Visual Studio 2015, pero no en Visual Studio 2017.

```cpp

struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}

```

Para corregir el error, use la inicialización directa:

```cpp

A a1{ 1 };
const A& a2{ 1 };

```

En Visual Studio 2015, el compilador trataba erróneamente la inicialización de lista de copia como si fuera inicialización de copia regular; solo consideraba la conversión de constructores para la resolución de sobrecarga. En el ejemplo siguiente, Visual Studio 2015 elige MyInt(23), pero Visual Studio 2017 genera correctamente el error.

```cpp

// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
    explicit MyStore(int initialCapacity);
};

struct MyInt {
    MyInt(int i);
};

struct Printer {
    void operator()(MyStore const& s);
    void operator()(MyInt const& i);
};

void f() {
    Printer p;
    p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}

```

Este ejemplo es similar al anterior, pero genera un error diferente. Se realiza correctamente en Visual Studio 2015 y genera un error en Visual Studio 2017 con C2668.

```cpp

struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}

```

### <a name="deprecated-typedefs"></a>Definiciones de tipo en desuso

Visual Studio 2017 ahora emite la advertencia correcta para las definiciones de tipo en desuso declaradas en una clase o struct. En el ejemplo siguiente, la compilación se realiza sin advertencias en Visual Studio 2015, pero se genera la advertencia C4996 en Visual Studio 2017.

```cpp

struct A
{
    // also for __declspec(deprecated)
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}

```

### <a name="constexpr"></a>constexpr

Visual Studio 2017 genera correctamente un error si el operando izquierdo de una operación de evaluación condicional no es válido en un contexto constexpr. El siguiente código se compila en Visual Studio 2015, pero no en Visual Studio 2017:(aparece el error C3615, que indica que la función constexpr 'f' no puede resultar en una expresión constante):

```cpp

template<int N>
struct array
{
    int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615
}

```
Para corregir el error, declare la función `array::size()` como `constexpr` o quite el calificador `constexpr` de `f`.

### <a name="class-types-passed-to-variadic-functions"></a>Tipos de clase pasados a funciones variádicas

En Visual Studio 2017, las clases o structs pasados a una función variádica como printf se deben poder copiar trivialmente. Al pasar objetos de este tipo, el compilador simplemente realiza una copia bit a bit y no llama al constructor ni al destructor.

```cpp

#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function.
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}

```

Para corregir el error, puede llamar a una función miembro que devuelva un tipo que se pueda copiar trivialmente 

```cpp

    std::atomic<int> i(0);
    printf("%i\n", i.load());

```

o bien realizar una conversión estática para convertir el objeto antes de pasarlo:

```cpp

    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

En el caso de las cadenas compiladas y administradas mediante CStringW, debe usarse el `operator LPCWSTR()` proporcionado para convertir un objeto CStringW en el puntero C esperado por la cadena de formato.

```cpp

CStringW str1;
CStringW str2;
str1.Format(L"%s", static_cast<LPCWSTR>(str2));

```

### <a name="cv-qualifiers-in-class-construction"></a>Calificadores cv en la construcción de clases

En Visual Studio 2015, el compilador a veces omite incorrectamente al calificador cv al generar un objeto de clase mediante una llamada al constructor. Esto puede causar un bloqueo o un comportamiento inesperado en tiempo de ejecución. En el ejemplo siguiente se compila en Visual Studio 2015, pero se genera un error del compilador en Visual Studio 2017:

```cpp

struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440

```

Para corregir el error, declare `operator int()` como `const`.

### <a name="access-checking-on-qualified-names-in-templates"></a>Comprobación de acceso en nombres completos en plantillas

Las versiones anteriores del compilador no realizaban la comprobación de acceso en nombres completos en algunos contextos de plantilla. Esto puede interferir con el comportamiento esperado de SFINAE, ya que se espera un error en la sustitución debido a la inaccesibilidad de un nombre. Esto podría haber provocado un bloqueo o un comportamiento inesperado en tiempo de ejecución, ya que el compilador hubiera llamado incorrectamente a la sobrecarga incorrecta del operador. En Visual Studio 2017, se genera un error del compilador. El error concreto puede variar, pero normalmente es "C2672: no se encontró una función sobrecargada que coincida". El siguiente código se compila en Visual Studio 2015, pero genera un error en Visual Studio 2017:

```cpp

#include <type_traits>

template <class T> class S {
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
    f(10); // C2672: No matching overloaded function found.
}

```

### <a name="missing-template-argument-lists"></a>Listas de argumentos de plantilla que faltan

En Visual Studio 2015 y versiones anteriores, el compilador no diagnosticaba la falta de listas de argumentos de plantilla cuando la plantilla aparecía en una lista de parámetros de plantilla (por ejemplo, como parte de un argumento de plantilla predeterminado o un parámetro de plantilla sin tipo). Esto puede provocar un comportamiento impredecible, como el bloqueo del compilador o un comportamiento inesperado en tiempo de ejecución. El siguiente código se compila en Visual Studio 2015, pero genera un error en Visual Studio 2017.

```cpp

template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias 
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;

```

### <a name="expression-sfinae"></a>Expresión SFINAE

Para admitir la expresión SFINAE, el compilador ahora analiza argumentos decltype cuando las plantillas se declaran en lugar de crear instancias. Por consiguiente, si se detecta una especialización no dependiente en el argumento decltype, no se aplaza hasta el momento de la creación de instancias, sino que se procesa inmediatamente y los errores resultantes se diagnostican en ese momento.

En el ejemplo siguiente se muestra este tipo de error del compilador que se genera en el punto de declaración:

```cpp

#include <utility>
template <class T, class ReturnT, class... ArgsT>
class IsCallable
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

### <a name="classes-declared-in-anonymous-namespaces"></a>Clases declaradas en espacios de nombres anónimos

Según el estándar de C++, una clase que se declara dentro de un espacio de nombres anónimo tiene vinculación interna y, por lo tanto, no se puede exportar. En Visual Studio 2015 y versiones anteriores no se aplicó esta regla. En Visual Studio 2017 se aplica la regla de forma parcial. En el siguiente ejemplo se genera este error en Visual Studio 2017: "error C2201: const anonymous namespace::S1::vftable: debe tener una vinculación externa para exportarlo o importarlo".

```cpp

struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201

```

### <a name="default-initializers-for-value-class-members-ccli"></a>Inicializadores predeterminados para miembros de clase de valor (C++/CLI)

En Visual Studio 2015 y versiones anteriores, el compilador permitía (aunque omitía) un inicializador de miembro predeterminado para un miembro de una clase de valor. La inicialización predeterminada de una clase de valor siempre inicializa a cero a los miembros; no se permite un constructor predeterminado. En Visual Studio 2017, los inicializadores de miembro predeterminados generan un error del compilador, tal como se muestra en este ejemplo:

```cpp

value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // is not allowed for a member of a value class
};

```

### <a name="default-indexers-ccli"></a>Indizadores predeterminados (C++/CLI)

En Visual Studio 2015 y versiones anteriores, el compilador en algunos casos identificaba incorrectamente una propiedad predeterminada como un indizador predeterminado. Era posible solucionar el problema con el identificador `default` para acceder a la propiedad. La solución en sí misma se volvió problemática después de que se empezara a usar `default` como palabra clave en C++11. Por lo tanto, en Visual Studio 2017 se corrigieron los errores necesarios para la solución, y el compilador ahora genera un error cuando se usa `default` para acceder a la propiedad predeterminada de una clase.

```cpp

//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}

```

En Visual Studio 2017 se puede acceder a ambas propiedades Value por su nombre:

```cpp

#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}

```

## <a name="update_153"></a> Correcciones de errores en Visual Studio 2017 versión 15.3

### <a name="calls-to-deleted-member-templates"></a>Llamadas a plantillas de miembro eliminado

En versiones anteriores de Visual Studio, había ocasiones en que el compilador no podía emitir un error en las llamadas con un formato incorrecto a una plantilla de miembro eliminado, lo que podía provocar bloqueos en tiempo de ejecución. El código siguiente produce ahora el error C2280, "'int S\<int>::f\<int>(void)': se está intentando hacer referencia a una función eliminada":

```cpp

template<typename T>
struct S {
   template<typename U> static int f() = delete;
};

void g()
{
   decltype(S<int>::f<int>()) i; // this should fail
}

```

Para corregir el error, declare i como `int`.

### <a name="pre-condition-checks-for-type-traits"></a>Comprobaciones de condición previa para type traits

La versión 15.3 de Visual Studio 2017 mejora las comprobaciones de condición previa para type-traits a fin de seguir el estándar de manera más estricta. Una de estas comprobaciones es para asignable. El código siguiente produce el error C2139 en la versión 15.3 de Visual Studio 2017:

```cpp

struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3

```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nuevas advertencias de compilador y comprobaciones en tiempo de ejecución en la serialización nativa a administrada

Para llamar de funciones administradas a funciones nativas se requiere la serialización. El CLR realiza la serialización, pero no comprende la semántica de C++. Si se pasa un objeto nativo por valor, CLR llama al constructor de copia del objeto o usa BitBlt, lo que puede provocar un comportamiento indefinido en tiempo de ejecución.

Ahora, el compilador emite una advertencia si puede saber en tiempo de compilación que se pasa un objeto nativo con el constructor de copia eliminada entre límites nativos y administrados por valor. En aquellos casos en los que el compilador no lo sepa en tiempo de compilación, se inyecta una comprobación en tiempo de ejecución para que el programa llame a `std::terminate` inmediatamente cuando se produzca una serialización con un formato incorrecto. En la versión 15.3 de Visual Studio 2017, el siguiente código produce la advertencia C4606 "A": el paso de un argumento por valor entre los límites nativo y administrado requiere un constructor de copia válido. De lo contrario, el comportamiento en tiempo de ejecución es indefinido.

```cpp

class A
{
public:
   A() : p_(new int) {}
   ~A() { delete p_; }

   A(A const &) = delete;
   A(A &&rhs) {
   p_ = rhs.p_;
}

private:
   int *p_;
};

#pragma unmanaged

void f(A a)
{
}

#pragma managed

int main()
{
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}

```

Para corregir el error, quite la directiva `#pragma managed` para marcar el llamador como nativo y evitar la serialización.

### <a name="experimental-api-warning-for-winrt"></a>Advertencia de API experimental para WinRT

Las API de WinRT que se publican para experimentación y comentarios se decoran con `Windows.Foundation.Metadata.ExperimentalAttribute`. En la versión 15.3 de Visual Studio 2017, el compilador produce la advertencia C4698 cuando encuentra el atributo. Algunas API de versiones anteriores del SDK de Windows se han decorado con el atributo, y las llamadas a estas API ahora desencadenan esta advertencia del compilador. Los SDK más recientes de Windows tienen quitado el atributo de todos los tipos enviados, pero si usa un SDK antiguo, deberá suprimir estas advertencias en todas las llamadas a tipos enviados.

El código siguiente produce la advertencia C4698: "'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' solo se usa con fines de evaluación y está sujeto a cambio o eliminación en futuras actualizaciones":

```cpp

Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698

```

Para deshabilitar la advertencia, agregue #pragma:

```cpp

#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Definición fuera de línea de una función de miembro de plantilla

La versión 15.3 de Visual Studio 2017 produce un error cuando encuentra una definición fuera de línea de una función de miembro de plantilla que no se ha declarado en la clase. El código siguiente produce ahora el error C2039: "f": no es miembro de "S":

```cpp

struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Para corregir el error, agregue una declaración a la clase:

```cpp

struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}

```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Intento de tomar la dirección del puntero "this"

En C++, `this` es un prvalue de puntero de tipo a X. No puede tomar la dirección de `this` ni enlazarlo a una referencia lvalue. En versiones anteriores de Visual Studio, el compilador le permitiría eludir esta restricción mediante la realización de una conversión. En la versión 15.3 de Visual Studio 2017, el compilador genera el error C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Conversión a una clase base inaccesible

La versión 15.3 de Visual Studio 2017 genera un error cuando intenta convertir un tipo a una clase base que es inaccesible. El compilador ahora genera el "error C2243: "conversión de tipo": la conversión de "D *" a "B *" existe, pero no es accesible". El código siguiente es incorrecto y podría provocar un bloqueo en tiempo de ejecución. El compilador produce ahora el error C2243 cuando encuentra código como este:

```cpp

#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}

```

### <a name="default-arguments-are-not-allowed-on-out-of-line-definitions-of-member-functions"></a>No se permiten argumentos predeterminados en definiciones fuera de línea de funciones miembro

No se permiten argumentos predeterminados en definiciones fuera de línea de funciones miembro en clases de plantilla. El compilador emitirá una advertencia en **/permissive** y un error en **/permissive-**.

En versiones anteriores de Visual Studio, el siguiente código con formato incorrecto podría generar un bloqueo en tiempo de ejecución. La versión 15.3 de Visual Studio 2017 produce la advertencia C5034: 'A\<T>::f': una definición fuera de línea de un miembro de una plantilla de clase no puede tener argumentos predeterminados:

```cpp

template <typename T>
struct A {
    T f(T t, bool b = false);
};

template <typename T>
T A<T>::f(T t, bool b = false) // C5034
{
    // ...
}

```

Para corregir el error, quite el argumento predeterminado `= false`.

### <a name="use-of-offsetof-with-compound-member-designator"></a>Uso de offsetof con el designador de miembro compuesta

En la versión 15.3 de Visual Studio 2017, el uso de `offsetof(T, m)`, donde *m* es un "designador de miembro compuesto", da lugar a una advertencia al compilar con la opción **/Wall**. El código siguiente tiene un formato incorrecto y podría provocar un bloqueo en tiempo de ejecución. La versión 15.3 de Visual Studio 2017 produce la advertencia C4841: "extensión no estándar utilizada: designador de miembro compuesto en offsetof":

```cpp

struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);

```

Para corregir el código, deshabilite la advertencia con una pragma o cambie el código para que no se use `offsetof`:

```cpp

#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Uso de offsetof con un miembro de datos estático o una función miembro

En la versión 15.3 de Visual Studio 2017, el uso de `offsetof(T, m)`, donde *m* hace referencia a un miembro de datos estático o a una función miembro, da error. El siguiente código genera el "error C4597: comportamiento indefinido: offsetof aplicado a la función de miembro "foo'" y "error C4597: comportamiento indefinido: offsetof aplicado al miembro de datos estático "bar"":

```cpp

#include <cstddef>

struct A {
   int foo() { return 10; }
   static constexpr int bar = 0;
};

constexpr auto off = offsetof(A, foo);
constexpr auto off2 = offsetof(A, bar);

```

Este código no tiene un formato correcto y podría ocasionar un bloqueo en tiempo de ejecución. Para corregir el error, cambie el código para que deje de invocar un comportamiento indefinido. Se trata de código no portable que no admite el estándar de C++.

### <a name="declspec"></a> Nueva advertencia en los atributos declspec

En la versión 15.3 de Visual Studio 2017, el compilador ya no ignora los atributos si `__declspec(...)` se aplica antes de la especificación de vinculación de `extern "C"`. Anteriormente, el compilador ignoraría el atributo, lo que podría tener implicaciones para el tiempo de ejecución. Cuando las opciones **/Wall** y **/WX** están configuradas, el siguiente código produce la "advertencia C4768: los atributos __declspec anteriores a la especificación de la vinculación se ignoran":

```cpp

__declspec(noinline) extern "C" HRESULT __stdcall //C4768

```

Para corregir la advertencia, coloque primero la "C" externa:

```cpp

extern "C" __declspec(noinline) HRESULT __stdcall

```

Esta advertencia está desactivada de forma predeterminada en la versión 15.3, pero activada de forma predeterminada en la versión 15.5, y solo afecta al código compilado con **/Wall** **/WX**.

### <a name="decltype-and-calls-to-deleted-destructors"></a>decltype y llamadas a destructores eliminados

En versiones anteriores de Visual Studio, el compilador no detectaba cuándo se produce una llamada a un destructor eliminado en el contexto de la expresión asociada a "decltype". En la versión 15.3 de Visual Studio 2017, el siguiente código produce el error C2280: "'A\<T>::~A(void)': se está intentando hacer referencia a una función eliminada":

```cpp

template<typename T>
struct A
{
   ~A() = delete;
};

template<typename T>
auto f() -> A<T>;

template<typename T>
auto g(T) -> decltype((f<T>()));

void h()
{
   g(42);
}

```

### <a name="uninitialized-const-variables"></a>Variables const no inicializadas

La versión Visual Studio 2017 RTW tenía una regresión en la que el compilador de C++ no emitía un diagnóstico si no se inicializaba una variable "const". Esta regresión se ha corregido en Visual Studio 2017 versión 15.3. El siguiente código produce ahora la "advertencia C4132: "Valor": se debe inicializar el objeto const:

```cpp

const int Value; //C4132

```

Para corregir el error, asigne un valor a `Value`.

### <a name="empty-declarations"></a>Declaraciones vacías

La versión 15.3 de Visual Studio 2017 ahora advierte sobre declaraciones vacías para todos los tipos, no solo los integrados. El código siguiente produce ahora una advertencia C4091 de nivel 2 para las cuatro declaraciones:

```cpp

struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared

```

Para quitar las advertencias, simplemente conviértalas en comentario o quite las declaraciones vacías. En casos donde el objeto sin nombre no tenga que tener un efecto secundario (como RAII), se le debe proporcionar un nombre.

La advertencia se excluye en **/Wv:18** y está activada de forma predeterminada en el nivel de advertencia W2.

### <a name="stdisconvertible-for-array-types"></a>std::is_convertible para tipos de matriz

Las versiones anteriores del compilador daban resultados incorrectos para [std::is_convertible](standard-library/is-convertible-class.md) con los tipos de matriz. Esto requería que los autores de bibliotecas distinguieran mayúsculas y minúsculas en el compilador de Microsoft Visual C++ al usar el rasgo de tipo `std::is_convertible<...>`. En el siguiente ejemplo, las aserciones estáticas se validan en versiones anteriores de Visual Studio, pero no en Visual Studio 2017 versión 15.3:

```cpp

#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");

```

`std::is_convertible<From, To>` se calcula comprobando si una definición de función imaginaria está bien formada:

```cpp

   To test() { return std::declval<From>(); }

```

### <a name="private-destructors-and-stdisconstructible"></a>Destructores privados y std::is_constructible

Las versiones anteriores del compilador omitían si un destructor era privado al decidir el resultado de [std::is_constructible](standard-library/is-constructible-class.md). Ahora sí se tiene en cuenta. En el siguiente ejemplo, las aserciones estáticas se validan en versiones anteriores de Visual Studio, pero no en Visual Studio 2017 versión 15.3:

```cpp

#include <type_traits>

class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};

// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);

```

Los destructores privados hacen que un tipo sea no construible. `std::is_constructible<T, Args...>` se calcula como si se hubiera escrito la declaración siguiente:

```cpp

   T obj(std::declval<Args>()...)
```

Esta llamada implica una llamada al destructor.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: Resolución de sobrecarga ambigua del compilador

A veces, las versiones anteriores del compilador no eran capaces de detectar la ambigüedad cuando encontraban varios candidatos por medio tanto de declaraciones como de búsquedas dependientes de argumentos. Esto puede hacer que se elija la sobrecarga incorrecta y que ello derive en un comportamiento inesperado del entorno de ejecución. En el siguiente ejemplo, Visual Studio 2017 versión 15.3 muestra correctamente el error C2668, que informa de una llamada ambigua a una función sobrecargada:

```cpp

namespace N {
   template<class T>
   void f(T&, T&);

   template<class T>
   void f();
}

template<class T>
void f(T&, T&);

struct S {};
void f()
{
   using N::f; 

   S s1, s2;
   f(s1, s2); // C2668
}

```

Para corregir el código, prescinda del uso de la instrucción `N::f` si lo que quiere es llamar a `::f()`.

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: Declaraciones de función locales y búsquedas dependientes de argumentos

Las declaraciones de función locales ocultan la declaración de función en el ámbito de inclusión y deshabilitan la búsqueda dependiente de argumentos. Sin embargo, en este caso, las versiones anteriores del compilador realizaban búsquedas dependientes de argumentos, lo que podía dar lugar a que se eligiera la sobrecarga incorrecta y que se produjera un comportamiento inesperado del entorno de ejecución. Este error suele deberse a una firma incorrecta de la declaración de función local. En el siguiente ejemplo, Visual Studio 2017 versión 15.3 muestra correctamente el error C2660, que informa de que la función "f" no puede tomar dos argumentos:

```cpp

struct S {};
void f(S, int);

void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}

```

Para corregir el problema, cambie la firma `f(S)` o quítela.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: Orden de inicialización en las listas de inicializadores

Los miembros de clase se inicializan en el orden en que se declaran, no en el orden en que aparecen en las listas de inicializadores. Las versiones anteriores del compilador no avisaban cuando el orden de la lista de inicializadores difería del orden de declaración. Esto podía provocar un comportamiento indefinido del entorno de ejecución cuando la inicialización de un miembro dependía de otro miembro de la lista ya en proceso de inicialización. En el siguiente ejemplo, Visual Studio 2017 versión 15.3 (con **/Wall**) genera la "advertencia C5038, que indica que el miembro de datos 'A::y' se inicializará después del miembro de datos 'A::x'":

```cpp

struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};

```

Para corregir el problema, organice la lista de inicializadores de forma que tenga el mismo orden que las declaraciones. Cuando uno o ambos inicializadores hacen referencia a miembros de clase base, se genera una advertencia similar.

Cabe decir que esta advertencia está desactivada de forma predeterminada y solo afecta al código compilado con **/Wall**.

## <a name="update_155"></a> Correcciones de errores y otros cambios de comportamiento en la versión 15.5 de Visual Studio 2017

### <a name="partial-ordering-change"></a>Cambio de orden parcial

El compilador ahora rechaza correctamente el código siguiente y muestra el mensaje de error correcto:

```cpp

template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(const T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);    // C2668
}

```

```Output
t161.cpp
t161.cpp(16): error C2668: 'f': ambiguous call to overloaded function
t161.cpp(8): note: could be 'int f<int*>(const T &)'
        with
        [
            T=int*
        ]
t161.cpp(2): note: or       'int f<int>(int*)'
t161.cpp(16): note: while trying to match the argument list '(int*)'
```

El problema del ejemplo anterior es que hay dos diferencias en los tipos (const frente a non-const y pack frente a non-pack). Quite una de las diferencias para eliminar el error del compilador. De esta forma, el compilador podrá ordenar las funciones de forma inequívoca.

```cpp

template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);
}

```

### <a name="exception-handlers"></a>Controladores de excepciones

Los controladores de las referencias a un tipo de matriz o función no coinciden nunca con ningún objeto de excepción. Ahora, el compilador respeta esta regla y emite una advertencia de nivel 4. Además, ya no coincide con un controlador de `char*` o `wchar_t*` en un literal de cadena cuando se usa **/Zc:strictStrings**.

```cpp

int main()
{
    try {
        throw "";
    }
    catch (int (&)[1]) {} // C4843 (This should always be dead code.)
    catch (void (&)()) {} // C4843 (This should always be dead code.)
    catch (char*) {} // This should not be a match under /Zc:strictStrings
}

```

```Output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead

```
Este código evita el error:

```cpp

catch (int (*)[1]) {}

```

### <a name="tr1"></a>El espacio de nombres std::tr1 está en desuso

El espacio de nombres `std::tr1` no estándar se ha marcado como en desuso en los modos de C++14 y C++17. En la versión 15.5 de Visual Studio 2017, el código siguiente genera el error C4996:

```cpp

#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::tr1::function<int (int, int)> f = std::plus<int>(); //C4996
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}

```

```Output
warning C4996: 'std::tr1': warning STL4002: The non-Standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

Para corregirlo, quite la referencia al espacio de nombres `tr1`:

```cpp

#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::function<int (int, int)> f = std::plus<int>();
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}

```

### <a name="annex_d"></a>Las características de la biblioteca estándar que hay en el anexo D se han marcado como en desuso

Cuando se establece el compilador del modo **/std:c++17**, casi todas las características de la biblioteca estándar que hay en el anexo D se marcan como en desuso.

En la versión 15.5 de Visual Studio 2017, el código siguiente genera el error C4996:

```cpp

#include <iterator>

class MyIter : public std::iterator<std::random_access_iterator_tag, int> {
public:
    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");

```

```Output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ Standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

Para corregirlo, siga las instrucciones que hay en el texto de advertencia, tal como se indica en el código siguiente:

```cpp

#include <iterator>

class MyIter {
public:
    typedef std::random_access_iterator_tag iterator_category;
    typedef int value_type;
    typedef ptrdiff_t difference_type;
    typedef int* pointer;
    typedef int& reference;

    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");

```

### <a name="unreferenced-local-variables"></a>Variables locales sin referencias

En la versión 15.5 de Visual Studio, se emite una advertencia de C4189 en más casos, tal como se indica en el código siguiente:

```cpp

void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}

```

```Output
warning C4189: 's': local variable is initialized but not referenced

```

Para corregirlo, quite la variable que no se use.

### <a name="single-line-comments"></a>Comentarios de una sola línea

En la versión 15.5 de Visual Studio 2017, el compilador de C ya no emite las advertencias C4001 y C4179. Anteriormente, solo se emitían en el conmutador de compilador de **/Za**.  Las advertencias ya no son necesarias porque los comentarios de una sola línea han formado parte del estándar C desde C99.

```cpp

/* C only */
#pragma warning(disable:4001) //C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```Output
warning C4619: #pragma warning: there is no warning number '4001'
```

Si ya no es necesario que el código sea compatible con versiones anteriores, puede quitar la supresión de C4001/C4179 para evitar la advertencia. De lo contrario, suprima solo C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */

```

### <a name="declspec-attributes-with-extern-c-linkage"></a>Atributos __declspec con vinculación extern "C" 

En versiones anteriores de Visual Studio, el compilador ignoraba los atributos `__declspec(...)` cuando `__declspec(...)` se aplicaba antes de la especificación de vinculación `extern "C"`. Este comportamiento provocaba que se generase código que los usuarios no tenían intención de generar, con posibles implicaciones en el tiempo de ejecución. La advertencia se agregó en la versión 15.3 de Visual Studio, pero estaba desactivada de forma predeterminada. En la versión 15.5 de Visual Studio 2017, la advertencia está habilitada de forma predeterminada.

```cpp

__declspec(noinline) extern "C" HRESULT __stdcall //C4768

```

```Output
warning C4768: __declspec attributes before linkage specification are ignored

```

Para corregir el error, coloque la especificación de vinculación antes del atributo __declspec:

```cpp

extern "C" __declspec(noinline) HRESULT __stdcall

```

Esta nueva advertencia C4768 se muestra en algunos encabezados de Windows SDK que se enviaron con la versión 15.3 de Visual Studio 2017 o una posterior (por ejemplo, la versión 10.0.15063.0, también conocida como RS2 SDK). Sin embargo, las versiones posteriores de los encabezados de Windows SDK (concretamente, ShlObj.h y ShlObj_core.h) se han corregido para que no generen esta advertencia. Cuando se le muestre esta advertencia en los encabezados de Windows SDK, puede hacer lo siguiente:

1. Cambie al Windows SDK más reciente incluido en la versión 15.5 de Visual Studio 2017.
2. Desactive la advertencia de #include de la instrucción del encabezado de Windows SDK:

```cpp

   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern_linkage"></a>Vinculación de extern constexpr

En versiones anteriores de Visual Studio, el compilador siempre proporcionaba una vinculación interna de variable de `constexpr` aunque la variable se marcase como `extern`. En la versión 15.5 de Visual Studio 2017, un nuevo conmutador de compilador (**/Zc:externConstexpr**) permite un comportamiento correcto que cumple con los estándares. Este acabará convirtiéndose en el conmutador predeterminado.

```cpp

extern constexpr int x = 10;

```

```Output
error LNK2005: "int const x" already defined
```

Si un archivo de encabezado contiene una variable declarada como `extern constexpr`, tiene que marcarse como `__declspec(selectany)` para que se puedan combinar correctamente sus declaraciones duplicadas:

```cpp

extern constexpr __declspec(selectany) int x = 10;

```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>No se puede usar typeid en tipos de clase incompleta

En versiones anteriores de Visual Studio, el compilador permitía de forma incorrecta el código siguiente, lo que podía generar información de tipo incorrecto. En la versión 15.5 de Visual Studio 2017, el compilador genera correctamente un error:

```cpp

#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5

```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdisconvertible-target-type"></a>Tipo de destino std::is_convertible

`std::is_convertible` requiere que el tipo de destino sea un tipo de valor devuelto válido. En versiones anteriores de Visual Studio, el compilador permitía incorrectamente los tipos abstractos, lo que podía provocar una resolución de sobrecarga incorrecta y un comportamiento no intencionado del tiempo de ejecución.  El código siguiente ahora genera correctamente el error C2338:

```cpp

#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5

```

Para evitarlo, al usar `is_convertible` debe comparar los tipos de puntero, ya que una comparación de un tipo que no sea de puntero podría provocar errores si uno de los tipos es abstracto:

```cpp

#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");

```

### <a name="noexcept_removal"></a> Eliminación de especificaciones de excepción dinámica y noexcept

En C++17, `throw()` es un alias de `noexcept`, `throw(<type list>)` y `throw(...)` se quitan, y determinados tipos pueden incluir `noexcept`. Esto puede generar problemas de compatibilidad de código fuente con código que sea conforme a C++14 o versiones anteriores. El conmutador **/Zc:noexceptTypes-** se puede usar para revertir a la versión C++14 de `noexcept` al usar el modo C++17 en general. Esto le permite actualizar el código fuente para que sea conforme con C++17 sin tener que reescribir todo el código de `throw()` a la vez.

Ahora, el compilador también diagnostica más especificaciones de excepción no coincidentes en las declaraciones del modo C++17 o con la opción **/permissive-** mediante la nueva advertencia C5043.

El código siguiente genera los errores C5043 y C5040 en la versión 15.5 de Visual Studio 2017 cuando se aplica el conmutador **/std:c++17**:

```cpp

void f() throw(); // equivalent to void f() noexcept;
void f() {} // warning C5043
void g() throw(); // warning C5040

struct A {
    virtual void f() throw();
};

struct B : A {
    virtual void f() { } // error C2694
};

```
Para quitar los errores mientras sigue usando **/std:c++17**, agregue el conmutador **/Zc:noexceptTypes-** a la línea de comandos o bien actualice el código para que use `noexcept`, tal como se indica en el ejemplo siguiente:

```cpp

void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A {
    virtual void f() noexcept;
};

struct B : A {
    virtual void f() noexcept { }
};

```

### <a name="inline-variables"></a>Variables alineadas

Ahora, los miembros de datos de static constexpr están alineados de forma implícita, lo que significa que su declaración en una clase es ahora su definición. Usar definiciones fuera de línea para un miembro de datos de static constexpr es redundante y está en desuso. En la versión 15.5 de Visual Studio 2017, cuando se aplica el conmutador **/std:c++17**, el código siguiente ahora genera la advertencia C5041 *'size': las definiciones fuera de línea de un miembro de datos de static constexpr no son necesarias y en C++17 están en desuso*:

```cpp

struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041

```

### <a name="extern-c-declspec-warning-c4768-now-on-by-default"></a>La advertencia C4768 extern "C" __declspec(...) ahora está activada de forma predeterminada.

La advertencia se agregó en la versión 15.3 de Visual Studio 2017, pero estaba desactivada de forma predeterminada. En cambio, en la versión 15.5 de Visual Studio 2017 está activada de forma predeterminada. Vea [Nueva advertencia en los atributos declspec](#declspec) para obtener más información.

### <a name="defaulted-functions-and-declspecnothrow"></a>Funciones predeterminadas y __declspec(nothrow)

Anteriormente, el compilador permitía que las funciones predeterminadas se declarasen con `__declspec(nothrow)` cuando las funciones de base/miembro correspondientes permitían excepciones. Este comportamiento es contrario al estándar de C++ y puede provocar un comportamiento indefinido en el entorno de ejecución. El estándar requiere que estas funciones se definan como eliminadas si se produce un error de coincidencia en la especificación de excepciones.  En **/std:c++17**, el código siguiente genera el error C2280 *al intentar hacer referencia a una función eliminada. La función se ha eliminado de forma implícita porque la especificación de excepciones explícita no es compatible con la de la declaración implícita*:


```cpp

struct A {
    A& operator=(const A& other) { // No exception specification; this function may throw.
        ...
    }
};

struct B : public A {
    __declspec(nothrow) B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1; // error C2280
}

```

Para corregir este código, elimine __declspec(nothrow) de la función predeterminada, o bien elimine `= default` y proporcione una definición para la función junto con el control de excepciones que sea necesario:

```cpp

struct A {
    A& operator=(const A& other) {
        // ...
    }
};

struct B : public A {
    B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1;
}

```
### <a name="noexcept-and-partial-specializations"></a>Operador noexcept y especializaciones parciales
Con el operador noexcept en el sistema de tipo, es posible que las especializaciones parciales para hacer coincidir tipos "callable" determinados no se puedan compilar o que no se pueda elegir la plantilla principal debido a que falte una especialización parcial para los punteros de función noexcept.

En tales casos, es posible que tenga que agregar más especializaciones parciales para controlar los punteros de función noexcept y los punteros noexcept en las funciones de miembro. Estas sobrecargas solo son lícitas en el modo **/std:c++17**. Si hay que conservar la compatibilidad de C++14 con versiones anteriores y está escribiendo código que utilizan otros usuarios, debe restringir estas nuevas sobrecargas a las directivas de `#ifdef`. Si está trabajando en un módulo autocontenido, en lugar de usar restricciones de `#ifdef`, puede compilar con el conmutador **/Zc:noexceptTypes-**.

El código siguiente compila en **/std:c++14**, pero falla en **/std:c++17**, con el error C2027: "use of undefined type 'A\<T>'":

```cpp

template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // C2027
}

```

El código siguiente se procesa correctamente en **/std:c++17** porque el compilador elige la nueva especialización parcial `A<void (*)() noexcept>`:

```cpp

template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <>
struct A<void(*)() noexcept>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // OK
}

```

## <a name="update_157"></a> Correcciones de errores y otros cambios de comportamiento en la versión 15.7 de Visual Studio 2017

### <a name="c17-default-argument-in-the-primary-class-template"></a>Argumento predeterminado en la plantilla de clase principal para C++17

Este cambio de comportamiento es una condición previa para [Template argument deduction for class templates - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) (Deducción de argumentos de plantilla para plantillas de clase - P0091R3), cuya compatibilidad completa está planeada para una futura versión preliminar de la versión 15.7 de Visual Studio 2017.

Anteriormente, el compilador omitía el argumento predeterminado en la plantilla de clase principal.

```cpp

template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary

```

En el modo **/std:c++17** de la versión 15.7 de Visual Studio 2017 no se ignora el argumento predeterminado:

```cpp

template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used

```

### <a name="dependent-name-resolution"></a>Resolución de nombres dependientes

Este cambio de comportamiento es una condición previa para [Template argument deduction for class templates - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) (Deducción de argumentos de plantilla para plantillas de clase - P0091R3), cuya compatibilidad completa está planeada para una futura versión preliminar de la versión 15.7 de Visual Studio 2017.

En el ejemplo siguiente, el compilador de Visual Studio 15.6 y versiones anteriores resuelve `D::type` como `B<T>::type` en la plantilla de clase principal.

```cpp

template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = B<T*>::type;
};

```

En la versión 15.7 de Visual Studio 2017, en el modo **/std:c++17**, se requiere la palabra clave `typename` en la instrucción `using` en D. Sin `typename`, se produce la advertencia del compilador C4346: *'B<T\*>::type': dependent name is not a type* (el nombre dependiente no es un tipo) y el error C2061: *syntax error: identifier 'type'* (error de sintaxis: identificador "tipo"):

```cpp

template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = typename B<T*>::type;
};

```

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>Atributo [[nodiscard]]: aumento del nivel de advertencia para C++17

En la versión 15.7 de Visual Studio 2017, en el modo **/std:c++17**, el nivel de advertencia de C4834 ("discarding return value of function with 'nodiscard' attribute" ["descartando el valor devuelto de la función con el atributo 'nodiscard'"]) se aumenta de W3 a W1. Puede deshabilitar la advertencia con una conversión a `void`, o pasando **/wd:4834** al compilador.

```cpp

[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value 
         // of function with 'nodiscard'
}

```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Lista de inicialización de la clase base de constructor de plantilla variádica

En ediciones anteriores de Visual Studio, se permitía erróneamente sin ningún error una lista de inicialización de la clase base de constructor de plantilla variádica en la que faltaban los argumentos de plantilla. En Visual Studio 2017 versión 15.7, se genera un error del compilador.

El siguiente ejemplo de código de Visual Studio de 2017 versión 15.7 genera el *error C2614: D.\<int>: inicialización de miembro no válida: "B" no es una base o miembro*

```cpp
template<typename T>
struct B {};

template<typename T>
struct D : B<T>
{

    template<typename ...C>
    D() : B() {} // C2614. Missing template arguments to B.
};

D<int> d;

```

Para corregir el error, cambie la expresión B() a B\<T>().



## <a name="see-also"></a>Vea también

[Conformidad del lenguaje Visual C++](visual-cpp-language-conformance.md)
