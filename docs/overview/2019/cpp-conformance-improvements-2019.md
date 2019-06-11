---
title: Mejoras de conformidad de C++
ms.date: 05/16/2019
description: Microsoft C++ en Visual Studio 2019 avanza hacia la plena conformidad con el estándar de lenguaje C++20.
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 02b778f10ad94342c922a4e79a856cc2a7d53076
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451220"
---
# <a name="c-conformance-improvements-in-visual-studio-2019-rtw-and-version-161improvements161"></a>Mejoras de conformidad de C++ en Visual Studio 2019 RTW y versión [16.1](#improvements_161)

## <a name="improvements-in-visual-studio-2019-rtw"></a>Mejoras en Visual Studio 2019 RTW

Visual Studio 2019 RTW contiene las siguientes mejoras de conformidad, correcciones de errores y cambios de comportamiento del compilador de Microsoft C++ (MSVC).

**Nota:** Las características de C++20 estarán disponibles en modo `/std:c++latest` hasta que la implementación de C++20 sea completa tanto en el compilador como en IntelliSense. Llegado este momento, se incluirá el modo de compilador `/std:c++20`.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Mejor compatibilidad de módulos en las plantillas y para la detección de errores

Ahora, los módulos están oficialmente en el estándar C++20. Se ha agregado mejor compatibilidad en la versión 15.9 de Visual Studio 2017. Para más información, vea [Better template support and error detection in C++ Modules with MSVC 2017 version 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/) (Mejor compatibilidad de plantilla y detección de errores en los módulos de C++ con MSVC 2017 versión 15.9).

### <a name="modified-specification-of-aggregate-type"></a>Especificación modificada de tipo de agregado

La especificación de un tipo agregado ha cambiado en C++20; vea [Prohibit aggregates with user-declared constructors](https://wg21.link/p1008r1) (Prohibir agregados con constructores declarados por el usuario). En el modo `/std:c++latest` de Visual Studio 2019, una clase con cualquier constructor declarado por el usuario (por ejemplo, incluir un constructor declarado `= default` o `= delete`) no constituye un agregado. Antes, solo los constructores proporcionados por el usuario podían hacer que una clase no se cualificara como un agregado. Este cambio impone más restricciones sobre cómo se pueden inicializar estos tipos.

El siguiente código se compila sin errores en Visual Studio 2017, pero genera los errores C2280 y C2440 en el modo `/std:c++latest` Visual Studio 2019:

```cpp
struct A
{
    A() = delete; // user-declared ctor
};

struct B
{
    B() = default; // user-declared ctor
    int i = 0;
};

A a{}; // ill-formed in C++20, previously well-formed
B b = { 1 }; // ill-formed in C++20, previously well-formed
```

### <a name="partial-support-for-operator-"></a>Compatibilidad parcial con el operador <> =

[P0515R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0515r3.pdf)C++20 presenta el operador de comparación a tres sentidos `<=>`, también conocido como "operador de nave espacial". El modo `/std:c++latest` de Visual Studio 2019 tiene compatibilidad parcial con este operador al generar errores por usar una sintaxis que ahora no está permitida. Por ejemplo, el siguiente código se compila sin errores en Visual Studio 2017, pero genera varios errores en el modo `/std:c++latest` Visual Studio 2019:

```cpp
struct S
{
       bool operator<=(const S&) const { return true; }
};

template <bool (S::*)(const S&) const>
struct U { };
int main(int argc, char** argv)
{
       U<&S::operator<=> u; // In Visual Studio 2019 raises C2039, 2065, 2146.
}
```

Para evitar estos errores, inserte un espacio en la línea incorrecta, antes del corchete final: `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Referencias a tipos con calificadores CV discrepantes

Antes, MSVC permitía el enlace directo de una referencia de un tipo con calificadores CV discrepantes por debajo del nivel superior. Esto permitía modificar datos supuestamente constantes a los que remitía la referencia, mientras que ahora el compilador crea un archivo temporal, como requiere el estándar. En Visual Studio 2017, el código siguiente se compila sin advertencias. En Visual Studio 2019, el compilador genera la *advertencia C4172: \<func:#1 "?PData@X@@QBEABQBXXZ"> devolución de dirección de la variable local o temporal*.

```cpp
struct X
{
    const void* const& PData() const
    {
        return _pv;
    }

    void* _pv;
};

int main()
{
    X x;
    auto p = x.PData(); // C4172
}
```
### <a name="reinterpretcast-from-an-overloaded-function"></a>`reinterpret_cast` de una función sobrecargada

El argumento `reinterpret_cast` no es uno de los contextos en los que se permite la dirección de una función sobrecargada. El siguiente código se compila sin errores en Visual Studio 2017, pero en Visual Studio 2019 genera el error *C2440: no se puede realizar la conversión de 'overloaded-function' a 'fp'* :

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

Para evitar el error, use una conversión permitida en este escenario:

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Cierres de lambda

En C++14, los tipos de cierre de lambda no son literales. La principal consecuencia de esta regla es que una expresión lambda no se puede asignar a una variable `constexpr`. El siguiente código se compila sin errores en Visual Studio 2017, pero en Visual Studio 2019 genera el error *C2127: 'l': inicialización no válida de la entidad 'constexpr' con una expresión no constante*:

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Para evitar el error, quite el calificador `constexpr` o cambie el modo de conformidad a `/std:c++17`.

### <a name="stdcreatedirectory-failure-codes"></a>Códigos de error de std::create_directory

[P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf) implementado de C ++ 20 sin condiciones. Esto cambia `std::create_directory` en el sentido de que se comprueba si el destino ya es un directorio en caso de error. Antes, todos los errores de tipo ERROR_ALREADY_EXISTS se convertían en códigos que se ejecutaban correctamente, pero que no creaban un directorio.

### <a name="operatorstdostream-nullptrt"></a>Operador <<(std::ostream, nullptr_t)

Según [LWG 2221](https://cplusplus.github.io/LWG/issue2221), se ha agregado `operator<<(std::ostream, nullptr_t)` para escribir nullptrs en secuencias. 

### <a name="additional-parallel-algorithms"></a>Algoritmos paralelos adicionales

Nuevas versiones en paralelo de `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap` y `is_heap_until`.

### <a name="atomic-initialization"></a>Inicialización atómica

[En el documento P0883 sobre fijación de la inicialización atómica](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) se cambia `std::atomic` de forma que el elemento T contenido se inicializa según su valor, y no de manera predeterminada. Esta corrección se habilita cuando se usa Clang/LLVM con la biblioteca estándar de Microsoft. Actualmente está deshabilitada en el compilador de Microsoft C++ como solución provisional a un error en el procesamiento de constexpr.

### <a name="removecvref-and-removecvreft"></a>remove_cvref y remove_cvref_t

Se han implementado los rasgos de tipos `remove_cvref` y `remove_cvref_t` según el documento [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf). Lo que hacen es quitar la capacidad de referencia y la cualificación CV de un tipo sin que las funciones y matrices a punteros decaigan (a diferencia de `std::decay` y `std::decay_t`).

### <a name="feature-test-macros"></a>Macros para la prueba de características

La característica [Macros de prueba de características (P0941R2)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) está completa, con compatibilidad con `__has_cpp_attribute`. Ahora, las macros de prueba de características se admiten en todos los modos estándares.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Prohibición de agregados con constructores declarados por el usuario

El documento [P1008R1 de C++20 sobre la prohibición de agregados con constructores declarados por el usuario](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) está completo.

## <a name="improvements_161"></a> Mejoras en Visual Studio 2019 versión 16.1

### <a name="char8t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html). C++20 agrega un nuevo tipo de carácter que se utiliza para representar unidades de código UTF-8. Los literales de cadena u8 en C++20 tienen un tipo `const char8_t[N]` en lugar de `const char[N]`, que era lo que sucedía antes. Se han propuesto cambios similares para el estándar de C en [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm). En [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html) se proporcionan sugerencias para la corrección de compatibilidad con versiones anteriores de char8_t. El compilador de Microsoft C++ agrega compatibilidad con char8_t en Visual Studio 2019 versión 16.1 cuando se especifica la opción de compilador **/Zc:char8_t**. En el futuro, se admitirá en el modo [/std:c++latest](../../build/reference/std-specify-language-standard-version.md), lo que puede revertirse al comportamiento de C++17 a través de **/Zc:char8_t-** . El compilador EDG con tecnología IntelliSense no está admitido aún, por lo que aparecerán errores falsos solo relativos a IntelliSense, lo cual no afecta a la compilación real.

#### <a name="example"></a>Ejemplo

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtypeidentity-metafunction-and-stdidentity-function-object"></a>Metafunción std::type_identity y objeto de función std::identity

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). La extensión de la plantilla de clase `std::identity` en desuso se ha quitado y se ha reemplazado por la metafunción `std::type_identity` y el objeto de función `std::identity` de C++20. Ambos están disponibles solo en el modo [/std:c++latest](../../build/reference/std-specify-language-standard-version.md). 

En el siguiente ejemplo se genera una advertencia C4996 de elemento en desuso relativa al objeto `std::identity` (definido en \<type_traits>) en Visual Studio 2017: 

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

En el siguiente ejemplo se muestra cómo usar el nuevo objeto `std::identity` (definido en \<functional>) junto con la nueva metafunción `std::type_identity`:

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Comprobaciones de sintaxis en lambdas genéricas

El nuevo procesador de lambdas permite realizar algunas comprobaciones sintácticas de modo de conformidad en las lambdas genéricas en el modo [/std:c++latest](../../build/reference/std-specify-language-standard-version.md) o en cualquier otro modo de lenguaje con **/experimental:newLambdaProcessor**. 

En Visual Studio 2017, este código se compila sin advertencias, pero en Visual Studio 2019 se genera el error de sintaxis *C2760: token inesperado '\<id-expr>', se esperaba 'id-expression'* :

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

En el siguiente ejemplo se muestra la sintaxis correcta, que el compilador aplica obligatoriamente:

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>Búsqueda dependiente de argumentos en llamadas de función

[P0846R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0846r0.html) (C++20) Se ha aumentado la capacidad de encontrar plantillas de función a través de la búsqueda dependiente de argumentos en expresiones de llamada de función con argumentos de plantilla explícitos. Se requiere **/std:c++latest**.

### <a name="designated-initialization"></a>Inicialización designada

[P0329R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf) (C++20) La inicialización designada permite seleccionar miembros específicos en la inicialización agregada usando la sintaxis `Type t { .member = expr }`. Se requiere **/std:c++latest**.

### <a name="new-and-updated-standard-library-functions-c20"></a>Funciones de la biblioteca estándar nuevas y actualizadas (C++20)

- `starts_with()` y `ends_with()` para `basic_string` y `basic_string_view`.
- `contains()` para contenedores asociativos.
- `remove()`, `remove_if()` y `unique()` para ` list` y `forward_list` ahora devuelven `size_type`.
- Se ha agregado `shift_left()` y `shift_right()` a \<algorithm>.

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019-rtw"></a>Correcciones de errores y cambios de comportamiento en Visual Studio 2019 RTW

### <a name="correct-diagnostics-for-basicstring-range-constructor"></a>Diagnóstico correcto del constructor de rango de basic_string

En Visual Studio 2019, el constructor de rango `basic_string` ya no suprime los diagnósticos de compilador con `static_cast`. El siguiente código se compila sin advertencias en Visual Studio 2017, a pesar de la posible pérdida de datos de `wchar_t` a `char` al inicializar `out`:

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 genera correctamente *C4244: 'argument': conversión de 'wchar_t' a 'const _Elem', posible pérdida de datos*. Para evitar la advertencia, puede inicializar std::string como se muestra en este ejemplo:

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Ahora las llamadas incorrectas a += y -= bajo /clr o/ZW se detectan debidamente

En Visual Studio 2017 se producía un error que hacía que el compilador ignorara los errores inadvertidamente y no generara ningún código para las llamadas no válidas a += y -= bajo `/clr` o `/ZW`. El siguiente código se compila sin errores en Visual Studio 2017, pero en Visual Studio 2019 genera correctamente el *error C2845: 'System::String ^': no se puede realizar aritmética con punteros en este tipo*:

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Para evitar el error del ejemplo, use el operador con el método ToString(): `s += E::e.ToString();`.

### <a name="initializers-for-inline-static-data-members"></a>Inicializadores de miembros de datos estáticos en línea

Los accesos de miembros no válidos dentro de los inicializadores `inline` y `static constexpr` ahora se detectan correctamente. El ejemplo siguiente se compila sin errores en Visual Studio 2017, pero en el modo `/std:c++17` de Visual Studio 2019 se genera el *error C2248: no se puede acceder al miembro privado declarado en la clase 'X'* .

```cpp
struct X
{
    private:
        static inline const int c = 1000;
};

struct Y : X
{
    static inline int d = c; // C2248 in Visual Studio 2019
};
```

Para evitar el error, declare el miembro `X::c` como protegido:

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 restablecido

MSVC solía tener una advertencia de rendimiento C4800 relativa a una conversión implícita a booleano demasiado ruidosa y que no podía eliminarse, algo que nos llevó a quitarlo de Visual Studio 2017. Sin embargo, durante el ciclo de vida de Visual Studio 2017 recibimos muchos comentarios sobre lo útil que era para resolver ciertos casos. Por lo tanto, volvemos a incluir en Visual Studio 2019 una C4800 cuidadosamente adaptada junto con su C4165 correspondiente; ambos se pueden suprimir fácilmente con una conversión explícita o mediante una comparación con 0 del tipo adecuado. C4800 es una advertencia de nivel 4 que está desactivada de forma predeterminada y C4165, una advertencia de nivel 3 que está desactivada de forma predeterminada. Ambas pueden detectarse con la opción de compilador `/Wall`.

El siguiente ejemplo genera las advertencias C4800 y C4165 en `/Wall`:

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

Para evitar las advertencias en el ejemplo anterior, puede escribir un código similar al siguiente:

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>La función miembro de clase local no tiene cuerpo

En Visual Studio 2017, se muestra *C4822: la función miembro de clase local no tiene cuerpo* solo cuando la opción de compilador `/w14822` se establece explícitamente; no se muestra con `/Wall`. En Visual Studio 2019, C4822 es una advertencia desactivada de forma predeterminada que hace que sea detectable en `/Wall` sin tener que establecer `/w14822` explícitamente.

```cpp
void foo()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Cuerpos de función de plantilla que contienen instrucciones if constexpr

Los cuerpos de función de plantilla que contienen instrucciones `if constexpr` tienen habilitadas algunas comprobaciones relacionadas con el análisis `/permissive-`. Por ejemplo, en Visual Studio 2017, el siguiente código genera C*7510: 'Type': el uso del nombre de tipo dependiente debe ir precedido de 'typename'* solo si la opción `/permissive-` no está establecida. En Visual Studio 2019, el mismo código genera errores independientemente de si la opción `/permissive-` está establecida o no:

```cpp
template <typename T>

int f()
{
    T::Type a; // error C7510

    if constexpr (T::val)
    {
        return 1;
    }
    else
    {
        return 2;
    }
}

struct X
{
    using Type = X;
    constexpr static int val = 1;
};

int main()
{
    return f<X>();
}

```

Para evitar el error, agregue la palabra clave `typename` a la declaración de `a`: `typename T::Type a;`.

### <a name="inline-assembly-code-is-not-supported-in-a-lambda-expression"></a>El código de ensamblado en línea no se admite en una expresión lambda

Recientemente se puso en conocimiento del equipo de Visual C++ un problema de seguridad por el cual el uso de un ensamblador en línea en una expresión lambda podía provocar daños en 'ebp' (el registro de remites) en tiempo de ejecución. Un atacante malintencionado podría aprovechar esta ventaja de este escenario. Dada la naturaleza del problema, el hecho de que los ensambladores en línea solo se admitan en x86 y la interacción deficiente de estos con el resto del compilador, pensamos que la forma más segura de solucionar este problema era no permitiendo los ensambladores en línea dentro de una expresión lambda.

Nota: el único uso del ensamblador en línea dentro de una expresión lambda que hemos encontrado de facto fue uno cuyo objetivo era capturar el remite. En este escenario, se pueden capturar los remites de todas las plataformas utilizando tan solo una función intrínseca de compilador `_ReturnAddress()`.

El siguiente código genera *C7552: no se admite un ensamblador en línea en una expresión lambda* tanto en la versión 15.9 de Visual Studio 2017 como en Visual Studio 2019:

```cpp
#include <cstdio>

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;

    auto lambda = [&]
    {
        __asm {

            mov eax, x
            mov y, eax
        }
    };

    lambda();
    return y;
}
```

Para evitar el error, mueva el código del ensamblado a una función con nombre, tal como se muestra en el ejemplo siguiente:

```cpp
#include <cstdio>

void g(int& x, int& y)
{
    __asm {
        mov eax, x
        mov y, eax
    }
}

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;
    auto lambda = [&]
    {
        g(x, y);
    };
    lambda();
    return y;
}

int main()
{
    std::printf("%d\n", f());
}
```

### <a name="iterator-debugging-and-stdmoveiterator"></a>Depuración de iterador y std::move_iterator

La característica de depuración de iterador se ha diseñado para desajustar `std::move_iterator` correctamente. Por ejemplo, `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` ahora puede participar en el método rápido `memcpy`.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Correcciones para la aplicación de la palabra clave \<xkeycheck.h>

La aplicación de la palabra clave de tipo macro de la biblioteca estándar \<xkeycheck.h> se ha corregido para emitir la palabra clave del problema real detectada, en lugar de un mensaje genérico. También admite palabras clave de C++20 y evita la falsa detección de IntelliSense de palabras clave aleatorias como macros.

### <a name="allocator-types-un-deprecated"></a>Desuso de los tipos de asignador cancelado

El desuso de `std::allocator<void>`, `std::allocator::size_type` y `std::allocator::difference_type` se ha cancelado.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Advertencia correcta para restringir conversiones de cadena

Se ha quitado de std::string un elemento `static_cast` falso no convocado por el estándar que suprimía por error las advertencias de restricción C4244. Ahora, al intentar llamar a `std::string::string(const wchar_t*, const wchar_t*)`, se emite correctamente la advertencia *C4244 "restricción de wchar_t a un carácter".*

### <a name="various-filesystem-correctness-fixes"></a>Varias correcciones de exactitud de \<filesystem>

- Se ha corregido un error de `std::filesystem::last_write_time` que se producía al intentar cambiar la última hora de escritura de un directorio.
- Ahora, el constructor `std::filesystem::directory_entry` almacena un resultado erróneo (en lugar de producir una excepción) si se indica una ruta de acceso de destino que no existe.
- La versión de 2 parámetros `std::filesystem::create_directory` se ha cambiado para llamar a la versión de 1 parámetro, ya que la función `CreateDirectoryExW` subyacente realizaría `copy_symlink` si existing_p fuera un vínculo simbólico.
- `std::filesystem::directory_iterator` ya no genera un error al encontrar un vínculo simbólico roto.
- Ahora, `std::filesystem::space` acepta rutas de acceso relativas.
- `std::filesystem::path::lexically_relative` ya no se confunde ante la presencia de barras diagonales finales, notificadas como [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Se ha solucionado el método `CreateSymbolicLinkW`, que rechazaba las rutas de acceso con barras diagonales en `std::filesystem::create_symlink`.
- Se ha solucionado la función `delete` de modo de eliminación de POSIX existente en Windows 10 LTSB 1609, pero los archivos no se han podido eliminar de facto.
- Ahora, los constructores de copia de `std::boyer_moore_searcher` y `std::boyer_moore_horspool_searcher` y los operadores de asignación de copia copian de verdad.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Algoritmos paralelos en Windows 8 y versiones posteriores

Ahora, la biblioteca de algoritmos paralelos usa correctamente la familia `WaitOnAddress` real en Windows 8 y en versiones posteriores, en lugar de usar siempre Windows 7 y versiones anteriores falsas.

### <a name="stdsystemcategorymessage-whitespace"></a>Espacios en blanco en std::system_category::message()

Ahora, `std::system_category::message()` recorta los espacios en blanco finales en el mensaje devuelto.

### <a name="stdlinearcongruentialengine-divide-by-zero"></a>División entre cero en std::linear_congruential_engine

Se han corregido algunas situaciones en las que `std::linear_congruential_engine` desencadenaría una división entre 0.

### <a name="fixes-for-iterator-unwrapping"></a>Correcciones de desajuste de iteradores

La maquinaria de desajuste de iteradores que se expuso por primera vez para la integración programador-usuario en la versión 15.8 de Visual Studio 2017 (como se describe en https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/) ya no desajusta los iteradores derivados de los iteradores de la biblioteca estándar. Por ejemplo, un usuario que deriva de `std::vector<int>::iterator` e intenta personalizar el comportamiento, ahora obtendrá su comportamiento personalizado cuando llame a algoritmos de la biblioteca estándar, y no el comportamiento de un puntero.
Ahora, la función de reserva de contenedor sin ordenar reserva de verdad para N elementos, como se describe en [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Control del tiempo

- Antes, algunos valores de tiempo que pasaban a la biblioteca de simultaneidad podían desbordarse, por ejemplo, `condition_variable::wait_for(seconds::max())`. Estos desbordamientos, que ahora se han corregido, cambiaban el comportamiento en un ciclo aparentemente aleatorio de 29 días (cuando Win32 subyacente aceptaba uint32_t milisegundos, las API se desbordaban).

- Ahora, el encabezado <ctime> declara correctamente timespec y timespec_get en el espacio de nombres std, además de declararlos también en el espacio de nombres global.

### <a name="various-fixes-for-containers"></a>Varias correcciones de contenedores

- Muchas de las funciones de contenedor internas de la biblioteca estándar se han convertido en privadas para una mejor experiencia de IntelliSense. Se espera realizar más correcciones para marcar miembros como privados en las siguientes versiones de MSVC.

- Se han corregido varios problemas de exactitud de seguridad de excepción por los que los contenedores basados en nodos como `list`, `map` y `unordered_map` podrían resultar dañados. Durante una operación de reasignación `propagate_on_container_copy_assignment` o `propagate_on_container_move_assignment`, liberaríamos el nodo centinela del contenedor con el asignador anterior, realizaríamos la asignación de POCCA/POCMA sobre el asignador anterior y, a continuación, intentaríamos adquirir el nodo centinela del nuevo asignador. Si se produjera un error en esta asignación, el contenedor se dañará y ni siquiera se podrá destruir, ya que un nodo centinela es una invariable de estructura de datos rígida. Esto se ha corregido asignando el nuevo nodo centinela desde el asignador del contenedor de origen antes de destruir el nodo centinela existente.

- Los contenedores se han corregido de forma que los asignadores siempre se copian/mueven/intercambian según `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment` y `propagate_on_container_swap`, incluso en el caso de los asignadores declarados como `is_always_equal`.

- Se han agregado sobrecargas para las funciones miembro de extracción y combinación de contenedores que aceptan contenedores rvalue según el documento [P0083 sobre la inserción de asignaciones y conjuntos"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)

### <a name="stdbasicistreamread-processing-of-rn--n"></a>Procesamiento de std::basic_istream::read de \r\n => \n

`std::basic_istream::read` se ha corregido para que no escriba en partes del búfer proporcionado temporalmente como parte del procesamiento de \r\n = > \n. Esto va en detrimento de algunas de las ventajas de rendimiento obtenidas en la versión 15.8 de Visual Studio 2017 en lecturas mayores de 4 K de tamaño, pero las mejoras de eficiencia de por las que se evitan 3 llamadas virtuales por carácter siguen estando presentes.

### <a name="stdbitset-constructor"></a>Constructor std::bitset

El constructor `std::bitset` ya no lee los unos y los ceros en orden inverso en los conjuntos de bits grandes.

### <a name="stdpairoperator-regression"></a>Regresión std::pair::operator=

Se ha corregido una regresión en el operador de asignación de `std::pair` que se producía al implementar [LWG 2729 "SFINAE ausente en std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729). Ahora, se vuelven a aceptar correctamente los tipos convertibles a `std::pair`.

### <a name="non-deduced-contexts-for-addconstt"></a>Contextos no deducidos para add_const_t

Se ha corregido un error menor de rasgos de tipos, según el cual da por hecho que `add_const_t` y otras funciones relacionadas están un contexto no deducido. En otras palabras, `add_const_t` debe ser un alias para `typename add_const<T>::type`, no `const T`.

## <a name="see-also"></a>Vea también

[Novedades de Visual Studio 2019](../what-s-new-for-visual-cpp-in-visual-studio.md)