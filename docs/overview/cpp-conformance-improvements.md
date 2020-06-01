---
title: Mejoras de conformidad de C++
ms.date: 05/18/2020
description: Microsoft C++ en Visual Studio avanza hacia la plena conformidad con el estándar de lenguaje C++20.
ms.technology: cpp-language
ms.openlocfilehash: c7c93de8b0e4c266290b858c76e7b34fccc0cabd
ms.sourcegitcommit: 3f91111c0350c0237fddb82766c290307f20e659
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2020
ms.locfileid: "83630507"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Mejoras de conformidad de C++ en Visual Studio

Microsoft C ++ hace mejoras de conformidad y corrige errores en cada versión. En este artículo se enumeran las mejoras por versión principal y luego por versión. También enumera las correcciones de errores principales por versión. Para saltar directamente a los cambios para una versión específica, la lista **En este artículo**.

::: moniker range="vs-2019"

## <a name="conformance-improvements-in-visual-studio-2019-rtw-version-160"></a><a name="improvements_160"></a> Mejoras de conformidad en Visual Studio 2019 RTW (versión 16.0)

Visual Studio 2019 RTW contiene las siguientes mejoras de conformidad, correcciones de errores y cambios de comportamiento del compilador de Microsoft C++ (MSVC).

**Nota:** Las características de C++20 estarán disponibles en modo **`/std:c++latest`** hasta que la implementación de C++20 sea completa tanto en el compilador como en IntelliSense. Llegado este momento, se incluirá el modo de compilador **`/std:c++20`** .

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Mejor compatibilidad de módulos en las plantillas y para la detección de errores

Ahora, los módulos están oficialmente en el estándar C++20. Se ha agregado mejor compatibilidad en la versión 15.9 de Visual Studio 2017. Para más información, vea [Better template support and error detection in C++ Modules with MSVC 2017 version 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/) (Mejor compatibilidad de plantilla y detección de errores en los módulos de C++ con MSVC 2017 versión 15.9).

### <a name="modified-specification-of-aggregate-type"></a>Especificación modificada de tipo de agregado

La especificación de un tipo agregado ha cambiado en C++20; vea [Prohibit aggregates with user-declared constructors](https://wg21.link/p1008r1) (Prohibir agregados con constructores declarados por el usuario). En el modo **`/std:c++latest`** de Visual Studio 2019, una clase con cualquier constructor declarado por el usuario (por ejemplo, incluir un constructor declarado `= default` o `= delete`) no constituye un agregado. Antes, solo los constructores proporcionados por el usuario podían hacer que una clase no se cualificara como un agregado. Este cambio impone más restricciones sobre cómo se pueden inicializar estos tipos.

El siguiente código se compila sin errores en Visual Studio 2017, pero genera los errores C2280 y C2440 en el modo **`/std:c++latest`** de Visual Studio 2019:

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

### <a name="partial-support-for-operator-"></a>Compatibilidad parcial para `operator <=>`

[P0515R3](https://wg21.link/p0515r3)C++20 presenta el operador de comparación a tres sentidos `<=>`, también conocido como "operador de nave espacial". El modo **`/std:c++latest`** de Visual Studio 2019 tiene compatibilidad parcial con este operador al generar errores por usar una sintaxis que ahora no está permitida. Por ejemplo, el siguiente código se compila sin errores en Visual Studio 2017, pero genera varios errores en el modo **`/std:c++latest`** de Visual Studio 2019:

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

Para evitar estos errores, inserte un espacio en la línea incorrecta, antes del corchete angular: `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Referencias a tipos con calificadores CV discrepantes

Antes, MSVC permitía el enlace directo de una referencia de un tipo con calificadores CV discrepantes por debajo del nivel superior. Este enlace podía permitir la modificación de los datos supuestamente constantes a los que hace referencia la referencia. Ahora, el compilador crea a un archivo temporal, como requiere el estándar. En Visual Studio 2017, el código siguiente se compila sin advertencias. En Visual Studio 2019, el compilador genera la advertencia C4172: `<func:#1 "?PData@X@@QBEABQBXXZ"> returning address of local variable or temporary.`:

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

### <a name="reinterpret_cast-from-an-overloaded-function"></a>`reinterpret_cast` de una función sobrecargada

El argumento para `reinterpret_cast` no es uno de los contextos en los que se permite la dirección de una función sobrecargada. El siguiente código se compila sin errores en Visual Studio 2017, pero en Visual Studio 2019 genera correctamente el error C2440 `cannot convert from 'overloaded-function' to 'fp'`:

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

En C++14, los tipos de cierre de lambda no son literales. La principal consecuencia de esta regla es que una expresión lambda no se puede asignar a una variable **constexpr**. El siguiente código se compila sin errores en Visual Studio 2017, pero en Visual Studio 2019 genera correctamente el error C2127 `'l': illegal initialization of 'constexpr' entity with a non-constant expression`:

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Para evitar el error, quite el calificador **constexpr** o cambie el modo de conformidad a `/std:c++17`.

### <a name="stdcreate_directory-failure-codes"></a>Códigos de error `std::create_directory`

[P1164](https://wg21.link/p1164r1) implementado de C ++ 20 sin condiciones. Esto cambia `std::create_directory` en el sentido de que se comprueba si el destino ya es un directorio en caso de error. Antes, todos los errores de tipo ERROR_ALREADY_EXISTS se convertían en códigos que se ejecutaban correctamente, pero que no creaban un directorio.

### `operator<<(std::ostream, nullptr_t)`

Según [LWG 2221](https://cplusplus.github.io/LWG/issue2221), se ha agregado `operator<<(std::ostream, nullptr_t)` para escribir nullptrs en secuencias.

### <a name="additional-parallel-algorithms"></a>Algoritmos paralelos adicionales

Nuevas versiones en paralelo de `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap` y `is_heap_until`.

### <a name="atomic-initialization"></a>Inicialización atómica

[En el documento P0883 sobre fijación de la inicialización atómica](https://wg21.link/p0883r1) se cambia `std::atomic` de forma que el elemento T contenido se inicializa según su valor, y no de manera predeterminada. Esta corrección se habilita cuando se usa Clang/LLVM con la biblioteca estándar de Microsoft. Actualmente está deshabilitada en el compilador de Microsoft C++ como solución provisional a un error en el procesamiento de **constexpr**.

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` y `remove_cvref_t`

Se han implementado los rasgos de tipos `remove_cvref` y `remove_cvref_t` según el documento [P0550](https://wg21.link/p0550r2). Lo que hacen es quitar la capacidad de referencia y la cualificación CV de un tipo sin que las funciones y matrices a punteros decaigan (a diferencia de `std::decay` y `std::decay_t`).

### <a name="feature-test-macros"></a>Macros para la prueba de características

La característica [Macros de prueba de características (P0941R2)](https://wg21.link/p0941r2) está completa, con compatibilidad con `__has_cpp_attribute`. Ahora, las macros de prueba de características se admiten en todos los modos estándares.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Prohibición de agregados con constructores declarados por el usuario

El documento [P1008R1 de C++20 sobre la prohibición de agregados con constructores declarados por el usuario](https://wg21.link/p1008r1) está completo.

## <a name="conformance-improvements-in-161"></a><a name="improvements_161"></a> Mejoras de conformidad en la versión 16.1

### <a name="char8_t"></a>char8_t

[P0482r6](https://wg21.link/p0482r6). C++20 agrega un nuevo tipo de carácter que se utiliza para representar unidades de código UTF-8. Los literales de cadena `u8` en C++20 tienen un tipo `const char8_t[N]` en lugar de `const char[N]` que era lo que sucedía antes. Se han propuesto cambios similares para el estándar de C en [N2231](https://wg14.link/n2231). En [P1423r3](https://wg21.link/p1423r3) se proporcionan sugerencias para la corrección de compatibilidad con versiones anteriores de `char8_t`. El compilador de Microsoft C++ agrega compatibilidad con `char8_t` en Visual Studio 2019 versión 16.1 cuando se especifica la opción de compilador **`/Zc:char8_t`** . En el futuro, se admitirá en el modo [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) **, lo que puede revertirse al comportamiento de C++17 a través de `/Zc:char8_t-`** . El compilador EDG con tecnología IntelliSense todavía no lo admite, por lo que aparecerán errores falsos solo relativos a IntelliSense que no afectan a la compilación real.

#### <a name="example"></a>Ejemplo

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>Metafunción std::type_identity y objeto de función std::identity

[P0887R1 type_identity](https://wg21.link/p0887r1). La extensión de la plantilla de clase `std::identity` en desuso se ha quitado y se ha reemplazado por la metafunción `std::type_identity` y el objeto de función `std::identity` de C++20. Ambos están disponibles solo en el modo [/std:c++latest](../build/reference/std-specify-language-standard-version.md).

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

El nuevo procesador de lambdas permite realizar algunas comprobaciones sintácticas de modo de conformidad en las lambdas genéricas en el modo [/std:c++latest](../build/reference/std-specify-language-standard-version.md) o en cualquier otro modo de lenguaje con **`/experimental:newLambdaProcessor`** .

En Visual Studio 2017, este código se compila sin advertencias, pero en Visual Studio 2019 genera el error C2760 `syntax error: unexpected token '\<id-expr>', expected 'id-expression'`:

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

[P0846R0](https://wg21.link/p0846r0) (C++20) Se ha aumentado la capacidad de encontrar plantillas de función a través de la búsqueda dependiente de argumentos en expresiones de llamada de función con argumentos de plantilla explícitos. Requiere **`/std:c++latest`** .

### <a name="designated-initialization"></a>Inicialización designada

[P0329R4](https://wg21.link/p0329r4) (C++20) La inicialización designada permite seleccionar miembros específicos en la inicialización agregada usando la sintaxis `Type t { .member = expr }`. Requiere **`/std:c++latest`** .

### <a name="new-and-updated-standard-library-functions-c20"></a>Funciones de la biblioteca estándar nuevas y actualizadas (C++20)

- `starts_with()` y `ends_with()` para `basic_string` y `basic_string_view`.
- `contains()` para contenedores asociativos.
- `remove()`, `remove_if()` y `unique()` para `list` y `forward_list` ahora devuelven `size_type`.
- Se ha agregado `shift_left()` y `shift_right()` a \<algorithm>.

## <a name="conformance-improvements-in-162"></a><a name="improvements_162"></a> Mejoras de conformidad en la versión 16.2

### <a name="noexcept-constexpr-functions"></a>Funciones noexcept y constexpr

Las funciones contexpr ya no se consideran **noexcept** de manera predeterminada cuando se usan en una expresión constante. Este cambio de comportamiento procede de la resolución de [CWG 1351](https://wg21.link/cwg1351) y está habilitado en [/permissive-](../build/reference/permissive-standards-conformance.md). El ejemplo siguiente se compila en la versión 16.1 de Visual Studio 2019 y en versiones anteriores, pero se genera C2338 en la versión 16.2 de Visual Studio 2019:

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

Para corregir el error, agregue la expresión **noexcept** a la declaración de la función:

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>Expresiones binarias con distintos tipos de enumeración

La capacidad de aplicar las conversiones aritméticas habituales en los operandos donde uno es de tipo de enumeración y el otro es de otro tipo de enumeración o de tipo de punto flotante está en desuso en C++20 ([P1120R0](https://wg21.link/p1120r0)).

En la versión 16.2 de Visual Studio 2019 y posteriores, el código siguiente produce una advertencia de nivel 4 cuando la opción del compilador [/std:C++latest](../build/reference/std-specify-language-standard-version.md) está habilitada:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

Para evitar la advertencia, use [static_cast](../cpp/static-cast-operator.md) para convertir el segundo operando:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

El uso de una operación binaria entre un tipo de enumeración y un tipo de punto flotante ahora es una advertencia cuando la opción del compilador [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) está habilitada:

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

Para evitar la advertencia, use [static_cast](../cpp/static-cast-operator.md) para convertir el segundo operando:

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>Comparaciones relacionales y de igualdad de matrices

Las comparaciones relacionales y de igualdad entre dos operandos de tipo de matriz están en desuso en C++20 ([P1120R0](https://wg21.link/p1120r0)). En otras palabras, una operación de comparación entre dos matrices (a pesar de las similitudes de rango y extensión) ahora es una advertencia. A partir de la versión 16.2 de Visual Studio 2019, el código siguiente genera C5056: `operator '==': deprecated for array types` cuando la opción del compilador [/std:c++latest](../build/reference/std-specify-language-standard-version.md) está habilitada:

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (a == b) { return 1; }
}
```

Para evitar la advertencia, puede comparar las direcciones de los primeros elementos:

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (&a[0] == &b[0]) { return 1; }
}
```

Para determinar si el contenido de dos matrices es igual, use la función [std::equal](../standard-library/algorithm-functions.md#equal):

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>Efecto de la definición del "operador de nave espacial" en `==` y `!=`

Una definición del "operador de nave espacial" ( **`<=>`** ) por sí sola ya no reescribirá expresiones relacionadas con **`==`** o **`!=`** a menos que el "operador de nave espacial" se marque como **`= default`** ([P1185R2](https://wg21.link/p1185r2)). El ejemplo siguiente se compila en Visual Studio 2019 RTW y en la versión 16.1, pero se produce C2678 en la versión 16.2 de Visual Studio 2019:

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Para evitar el error, defina el operador == o declárelo como valor predeterminado:

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
  bool operator==(const S&) const = default;
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

### <a name="standard-library-improvements"></a>Mejoras de la biblioteca estándar

- \<charconv> `to_chars()` con precisión fija o científica. (La precisión general está planeada actualmente para la versión 16.4).
- [P0020R6](https://wg21.link/p0020r6): atomic\<float>, atomic\<double>, atomic\<long double>
- [P0463R1](https://wg21.link/p0463r1): endian
- [P0482R6](https://wg21.link/p0482r6): Compatibilidad de la biblioteca con char8_t
- [P0600R1](https://wg21.link/p0600r1): [\[nodiscard]] para STL, parte 1
- [P0653R2](https://wg21.link/p0653r2): to_address()
- [P0754R2](https://wg21.link/p0754r2): \<version>
- [P0771R1](https://wg21.link/p0771r1): noexcept para el constructor de movimiento de std::function

## <a name="conformance-improvements-in-visual-studio-2019-version-163"></a><a name="improvements_163"></a> Mejoras de conformidad en Visual Studio 2019 versión 16.3

### <a name="stream-extraction-operators-for-char-removed"></a>Quitados los operadores de extracción de secuencias para char*

Se han quitado los operadores de extracción de secuencias para puntero a caracteres y se han reemplazado por operadores de extracción para matriz de caracteres (por [P0487R1](https://wg21.link/p0487r1)). WG21 considera que las sobrecargas eliminadas no son seguras. En el modo [/std:c++latest](../build/reference/std-specify-language-standard-version.md), el ejemplo siguiente produce ahora C2679: `binary '>>': no operator found which takes a right-hand operand of type 'char*' (or there is no acceptable conversion)`:

```cpp
   char x[42];
   char* p = x;
   std::cin >> std::setw(42);
   std::cin >> p;
```

Para evitar el error, use el operador de extracción con una variable char[]:

```cpp
char x[42];
std::cin >> x;
```

### <a name="new-keywords-requires-and-concept"></a>Nuevas palabras clave **`requires`** y **`concept`**

Se han agregado nuevas palabras clave **`requires`** y **`concept`** al compilador de Microsoft C++. Si intenta usar cualquiera de ellos como identificador en el modo [/std:c++latest](../build/reference/std-specify-language-standard-version.md), el compilador generará el error C2059 `syntax error`.

### <a name="constructors-as-type-names-disallowed"></a>Los constructores como nombres de tipo no están permitidos

Los nombres de constructor ya no se consideran injected-class-names cuando aparecen en un nombre completo después de un alias de una especialización de plantilla de clase. Previamente permitía el uso de constructores como un nombre de tipo para declarar otras entidades. El siguiente ejemplo ahora genera el error C3646 `'TotalDuration': unknown override specifier`:

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{};
};

```

Para evitar el error, declare `TotalDuration` como se muestra aquí:

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>Comprobación más estricta de las funciones `extern "C"`

Si se declaraba una función **`extern "C"`** en espacios de nombres diferentes, las versiones anteriores del compilador de Microsoft C++ no comprobaban si las declaraciones eran compatibles. En Visual Studio 2019 versión 16.3, el compilador realiza una comprobación de este tipo. En [`/permissive-`](../build/reference/permissive-standards-conformance.md), el código siguiente produce los errores C2371 `redefinition; different basic types` y C2733 `you cannot overload a function with C linkage`:

```cpp
using BOOL = int;

namespace N
{
   extern "C" void f(int, int, int, bool);
}

void g()
{
   N::f(0, 1, 2, false);
}

extern "C" void f(int, int, int, BOOL){}
```

Para evitar los errores del ejemplo anterior, use **`bool`** en lugar de `BOOL` de forma coherente en ambas declaraciones de `f`.

### <a name="standard-library-improvements"></a>Mejoras de la biblioteca estándar

Se han quitado los encabezados no estándar \<stdexcpt.h> y \<typeinfo.h>. En su lugar, el código que los incluye debe incluir los encabezados estándar \<exception> y \<typeinfo>, respectivamente.

## <a name="conformance-improvements-in-visual-studio-2019-version-164"></a><a name="improvements_164"></a> Mejoras de conformidad en Visual Studio 2019 versión 16.4

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>Mejor aplicación de la búsqueda de nombres en dos fases para identificadores cualificados en `/permissive-`

La búsqueda de nombres en dos fases requiere que los nombres no dependientes que se usan en los cuerpos de las plantillas sean visibles para la plantilla en el momento de la definición. Anteriormente, es posible que estos nombres se hayan encontrado cuando se creaban instancias de las plantillas. Este cambio facilita la escritura de código portable y compatible en MSVC con la marca [`/permissive-`](../build/reference/permissive-standards-conformance.md).

En la versión 16.4 de Visual Studio 2019, con la marca **`/permissive-`** establecida, en el ejemplo siguiente se genera un error porque `N::f` no está visible cuando se define la plantilla `f<T>`:

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

Normalmente, este error se puede corregir al incluir los encabezados que faltan o las funciones o variables de declaración de reenvío, tal como se muestra en el ejemplo siguiente:

```cpp
namespace N {
    int f();
}

template <class T>
int f() {
    return N::f() + T{};
}

namespace N {
    int f() { return 42; }
}
```

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>Conversión implícita de expresiones constantes de tipo entero en puntero nulo

Ahora, el compilador de MSVC implementa el [problema 903 de CWF](https://wg21.link/cwg903) en modo de cumplimiento ( **`/permissive-`** ). Esta regla no permite la conversión implícita de expresiones constantes integrales (excepto el literal entero '0') a constantes de puntero nulo. En el ejemplo siguiente se produce C2440 en modo de cumplimiento:

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

Para corregir el error, use **nullptr** en lugar de **false**. El literal 0 sigue permitido:

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>Reglas estándar para tipos de literales enteros

En el modo de cumplimiento (habilitado por [`/permissive-`](../build/reference/permissive-standards-conformance.md)), MSVC utiliza las reglas estándar para los tipos de literales enteros. Anteriormente los literales decimales demasiado grandes para caber en un **`int`** con signo tenían el tipo **`unsigned int`** . Ahora, estos literales reciben el siguiente tipo de entero con signo más grande, **`long long`** . Además, los literales con el sufijo "ll", que son demasiado grandes para caber en un tipo con signo, reciben el tipo **`unsigned long long`** .

Este cambio puede dar lugar a que se generen diagnósticos de advertencia diferentes y diferencias de comportamiento para las operaciones aritméticas en los literales.

En el ejemplo siguiente se muestra el nuevo comportamiento en Visual Studio 2019 versión 16.4. La variable `i` es ahora de tipo **`unsigned int`** . Este es el motivo por el que se genera la advertencia. Los bits de orden superior de la variable `j` se establecen en 0.

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

En el ejemplo siguiente se muestra cómo mantener el comportamiento anterior y evitar las advertencias y el cambio de comportamiento en tiempo de ejecución:

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>Parámetros de función que reemplazan los parámetros de plantilla

El compilador MSVC ahora genera un error cuando un parámetro de función reemplaza un parámetro de plantilla:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T(&buffer)[Size], int& Size) // error C7576: declaration of 'Size' shadows a template parameter
{
    return f(buffer, Size, Size);
}
```

Para corregir el error, cambie el nombre de uno de los parámetros:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T (&buffer)[Size], int& size_read)
{
    return f(buffer, Size, size_read);
}
```

### <a name="user-provided-specializations-of-type-traits"></a>Especializaciones proporcionadas por el usuario de rasgos de tipo

De acuerdo con la subcláusula *meta.rqmts* del estándar, el compilador MSVC ahora genera un error cuando encuentra una especialización definida por el usuario de una de las plantillas `type_traits` especificadas en el espacio de nombres `std`. A menos que se especifique lo contrario, estas especializaciones producen un comportamiento indefinido. En el ejemplo siguiente se muestra un comportamiento indefinido porque infringe la regla y `static_assert` produce un error C2338.

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

Para evitar el error, defina una estructura que herede el elemento `type_trait` preferente y especialícela:

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>Cambios en los operadores de comparación proporcionados por el compilador

Ahora, el compilador de MSVC implementa los siguientes cambios en los operadores de comparación por [P1630R1](https://wg21.link/p1630r1) cuando la opción [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) está habilitada:

El compilador ya no volverá a escribir expresiones con `operator==` si implican un tipo de valor devuelto que no sea **booleano**. El código siguiente produce ahora el error C2088 `'!=': illegal for struct`:

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Para evitar el error, debe definir explícitamente el operador necesario:

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
    U operator!=(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

El compilador ya no definirá un operador de comparación predeterminado si es miembro de una clase union-like. El siguiente ejemplo genera ahora el error C2120 `'void' illegal with all types`:

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const = default;
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

Para evitar el error, defina un cuerpo para el operador:

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const { ... }
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

El compilador ya no definirá un operador de comparación predeterminado si la clase contiene un miembro de referencia. El código siguiente produce ahora el error C2120 `'void' illegal with all types`:

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const = default;
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

Para evitar el error, defina un cuerpo para el operador:

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const { ... };
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

## <a name="conformance-improvements-in-visual-studio-2019-version-165"></a><a name="improvements_165"></a> Mejoras de conformidad en Visual Studio 2019 versión 16.5

### <a name="explicit-specialization-declaration-without-an-initializer-isnt-a-definition"></a>La declaración de especialización explícita sin un inicializador no es una definición.

En `/permissive-`, MSVC ahora aplica una regla estándar que establece que las declaraciones de especialización explícita sin inicializadores no son definiciones. Anteriormente, la declaración se consideraría una definición con un inicializador predeterminado. El efecto es observable en el momento de la vinculación, ya que es posible que un programa que dependa de este comportamiento tenga ahora símbolos sin resolver. Este ejemplo genera ahora un error:

```cpp
template <typename> struct S {
    static int a;
};

// In permissive-, this declaration isn't a definition, and the program won't link.
template <> int S<char>::a;

int main() {
    return S<char>::a;
}
```

```Output
error LNK2019: unresolved external symbol "public: static int S<char>::a" (?a@?$S@D@@2HA) referenced in function _main
at link time.
```

Para resolver el problema, agregue un inicializador:

```cpp
template <typename> struct S {
    static int a;
};

// Add an initializer for the declaration to be a definition.
template <> int S<char>::a{};

int main() {
    return S<char>::a;
}
```

### <a name="preprocessor-output-preserves-newlines"></a>La salida del preprocesador conserva las nuevas líneas

El preprocesador experimental conserva ahora las nuevas líneas y los espacios en blanco al usar `/P` o `/E` con `/experimental:preprocessor`. Este cambio se puede deshabilitar mediante `/d1experimental:preprocessor:oldWhitespace`.

Dado este origen de ejemplo,

```cpp
#define m()
line m(
) line
```

El formato de salida anterior de `/E` era:

```Output
line line
#line 2
```

La nueva salida de `/E` ahora es:

```Output
line
 line
```

### <a name="import-and-module-keywords-are-context-dependent"></a>Las palabras clave "import" y "module" dependen del contexto.

De acuerdo con P1857R1, las directivas de preprocesador de módulos y de importación tienen restricciones adicionales en su sintaxis. Este ejemplo ya no se compila:

```cpp
import // Invalid
m;
```

Produce el mensaje de error siguiente:

```Output
error C2146: syntax error: missing ';' before identifier 'm'
```

Para resolver el problema, mantenga la importación en la misma línea:

```cpp
import m; // OK
```

### <a name="removal-of-stdweak_equality-and-stdstrong_equality"></a>Eliminación de std::weak_equality and std::strong_equality

La combinación de P1959R0 requiere que el compilador quite el comportamiento y las referencias a los tipos `std::weak_equality` y `std::strong_equality`.

El código de este ejemplo ya no se compila:

```cpp
#include <compare>

struct S {
    std::strong_equality operator<=>(const S&) const = default;
};

void f() {
    nullptr<=>nullptr;
    &f <=> &f;
    &S::operator<=> <=> &S::operator<=>;
}
```

El ejemplo ahora conduce a estos errores:

```Output
error C2039: 'strong_equality': is not a member of 'std'
error C2143: syntax error: missing ';' before '<=>'
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C7546: binary operator '<=>': unsupported operand types 'nullptr' and 'nullptr'
error C7546: binary operator '<=>': unsupported operand types 'void (__cdecl *)(void)' and 'void (__cdecl *)(void)'
error C7546: binary operator '<=>': unsupported operand types 'int (__thiscall S::* )(const S &) const' and 'int (__thiscall S::* )(const S &) const'
```

Para resolver el problema, realice una actualización para dar preferencia a los operadores relacionales integrados y reemplazar los tipos quitados:

```cpp
#include <compare>

struct S {
    std::strong_ordering operator<=>(const S&) const = default; // prefer 'std::strong_ordering'
};

void f() {
    nullptr != nullptr; // use pre-existing builtin operator != or ==.
    &f != &f;
    &S::operator<=> != &S::operator<=>;
}
```

### <a name="tls-guard-changes"></a>Cambios en TLS Guard

Anteriormente, las variables locales de subproceso en archivos DLL no se inicializaban correctamente antes de su primer uso en subprocesos que existían antes de que se cargara el archivo DLL, excepto el subproceso que cargaba el archivo DLL. Este defecto se ha corregido.
Las variables locales de subproceso de este tipo de archivo DLL se inicializan inmediatamente antes de su primer uso en esos subprocesos.

Este nuevo comportamiento de pruebas de inicialización en usos de variables locales de subproceso se puede deshabilitar mediante el modificador del compilador `/Zc:tlsGuards-`. O bien, agregando el atributo `[[msvc:no_tls_guard]]` a determinadas variables locales de subproceso.

### <a name="better-diagnosis-of-call-to-deleted-functions"></a>Mejor diagnóstico de la llamada a funciones eliminadas

Nuestro compilador era más permisivo en las llamadas a funciones eliminadas previamente. Por ejemplo, si las llamadas se producían en el contexto de un cuerpo de plantilla, no se diagnosticaría la llamada. Además, si hubiera varias instancias de llamadas a funciones eliminadas, solo se emitiría un diagnóstico. Ahora se emite un diagnóstico para cada una de ellas.

Una consecuencia del nuevo comportamiento puede producir un pequeño cambio importante: El código que llamaba a una función eliminada no se diagnosticaría si nunca era necesario para la generación de código. Ahora se diagnostica por adelantado.

En este ejemplo se muestra código que ahora genera un error:

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s{};
};

U u{ 0 };
```

```Output
error C2280: 'S::S(void)': attempting to reference a deleted function
note: see declaration of 'S::S'
note: 'S::S(void)': function was explicitly deleted
```

Para resolver el problema, quite las llamadas a funciones eliminadas:

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s;  // Do not call the deleted ctor of 'S'.
};

U u{ 0 };
```

## <a name="conformance-improvements-in-visual-studio-2019-version-166"></a><a name="improvements_166"></a> Mejoras de conformidad en Visual Studio 2019 versión 16.6

### <a name="standard-library-streams-reject-insertions-of-mis-encoded-character-types"></a>Las secuencias de la biblioteca estándar rechazan las inserciones de tipos de caracteres con codificación incorrecta

Tradicionalmente, al insertar `wchar_t` en `std::ostream` y al insertar `char16_t` o `char32_t` en `std::ostream` o `std::wostream`, se genera su valor entero. Al insertar punteros a esos tipos de caracteres, se genera el valor del puntero. Los programadores no encuentran ningún caso intuitivo. A menudo esperan que la biblioteca estándar transcodifique el carácter o la cadena de caracteres terminada en null en su lugar, y que genere el resultado.

La propuesta de C++20 [P1423R3](https://wg21.link/p1423r3) agrega sobrecargas de operador de inserción de secuencias eliminadas para estas combinaciones de secuencia y carácter o de tipos de puntero de carácter. En **`/std:c++latest`** , las sobrecargas hacen que estas inserciones estén mal formadas, en lugar de comportarse de manera probablemente no intencionada. El compilador genera el error C2280 cuando se encuentra una. Puede definir la macro "sombreado de escape" `_HAS_STREAM_INSERTION_OPERATORS_DELETED_IN_CXX20` a `1` para restaurar el comportamiento anterior. (La propuesta también elimina los operadores de inserción de secuencias para `char8_t`. Nuestra biblioteca estándar ha implementado sobrecargas similares cuando agregamos asistencia a `char8_t`, por lo que el comportamiento "incorrecto" nunca ha estado disponible para `char8_t`).

En este ejemplo se muestra el comportamiento de este cambio:

```cpp
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << cw << ' ' << pw << '\n';
    std::cout << c16 << ' ' << p16 << '\n';
    std::cout << c32 << ' ' << p32 << '\n';
    std::wcout << c16 << ' ' << p16 << '\n';
    std::wcout << c32 << ' ' << p32 << '\n';
}
```

El código genera ahora estos mensajes de diagnóstico:

```Output
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,wchar_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char32_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char32_t)': attempting to reference a deleted function
```

Puede lograr el efecto del comportamiento anterior en todos los modos de lenguaje al convertir los tipos de caracteres en `unsigned int` o los tipos de puntero a carácter para `const void*`:

```c++
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << (unsigned)cw << ' ' << (const void*)pw << '\n'; // Outputs "120 0052B1C0"
    std::cout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::cout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
    std::wcout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::wcout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
}
```

### <a name="changed-return-type-of-stdpow-for-stdcomplex"></a>Tipo de valor devuelto cambiado de `std::pow()` para `std::complex`

Anteriormente, la implementación de MSVC de las reglas de promoción para el tipo de valor devuelto de la plantilla de función `std::pow()` era incorrecta. Por ejemplo, anteriormente `pow(complex<float>, int)` devolvía `complex<float>`. Ahora devuelve `complex<double>` correctamente. La corrección se ha implementado de forma incondicional en todos los modos estándar de Visual Studio 2019, versión 16.6.

Este cambio puede provocar errores del compilador. Por ejemplo, antes podía multiplicar `pow(complex<float>, int)` por un **`float`** . Dado que `complex<T> operator*` espera argumentos del mismo tipo, el siguiente ejemplo emite ahora el error del compilador C2676: `binary '*': 'std::complex<double>' does not define this operator or a conversion to a type acceptable to the predefined operator`:

```cpp
// pow_error.cpp
// compile by using: cl /EHsc /nologo /W4 pow_error.cpp
#include <complex>

int main() {
    std::complex<float> cf(2.0f, 0.0f);
    (void) (std::pow(cf, -1) * 3.0f);
}
```

Hay muchas posibles correcciones:

- Cambie el tipo del multiplicando **`float`** a **`double`** . Este argumento se puede convertir directamente en un `complex<double>` para que coincida con el tipo devuelto por `pow`.

- Restrinja el resultado de `pow` a `complex<float>` diciendo `complex<float>{pow(ARG, ARG)}`. Después, puede seguir multiplicando por un valor **`float`** .

- Pase **`float`** en lugar de **`int`** a `pow`. Esta operación puede ser más lenta.

- En algunos casos, puede evitar `pow` completamente. Por ejemplo, `pow(cf, -1)` se puede reemplazar por la división.

### <a name="switch-related-warnings-for-c"></a>Advertencias relacionadas con el conmutador para C

A partir de la versión 16.6 de Visual Studio 2019, el compilador implementa algunas advertencias preexistentes C++ para el código compilado como C. Las siguientes advertencias se habilitan ahora en diferentes niveles: C4060, C4061, C4062, C4063, C4064, C4065, C4808 y C4809. Las advertencias C4065 y C4060 están deshabilitadas de forma predeterminada en C.

Las advertencias se desencadenan cuando faltan las instrucciones **`case`** , **`enum`** modificadores no definido y **`bool`** erróneos (es decir, aquellos que contienen demasiados casos). Por ejemplo:

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
        default: break; // C4809: switch statement has redundant 'default' label;
                        // all possible 'case' labels are given
    }
}
```

Para corregir este código, quite el caso **`default`** redundante:

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
    }
}
```

### <a name="unnamed-classes-in-typedef-declarations"></a>Clases sin nombre en declaraciones `typedef`

A partir de la versión 16.6 de Visual Studio 2019, el comportamiento de las declaraciones `typedef` se ha restringido para ajustarse a [P1766R1](https://wg21.link/P1766R1). Con esta actualización, las clases sin nombre dentro de una declaración `typedef` no pueden tener ningún miembro que no sean:

- miembros de datos no estáticos,
- clases de miembro,
- enumeraciones de miembros,
- e inicializadores de miembro predeterminados.

Las mismas restricciones se aplican de forma recursiva a cada clase anidada. La restricción está pensada para garantizar la simplicidad de las estructuras que tienen nombres `typedef` para la vinculación. Deben ser lo suficientemente simples como para que no sea necesario realizar cálculos de vinculación antes de que el compilador obtenga el nombre de `typedef` para la vinculación.

Este cambio afecta a todos los modos estándar del compilador. En los modos predeterminados ( **`/std:c++14`** ) y **`/std:c++17`** , el compilador emite la advertencia C5208 para el código que no es conforme. Si se especifica **`/permissive-`** , el compilador emite la advertencia C5208 como un error en **`/std:c++14`** y emite el error C7626 en **`/std:c++17`** . El compilador emite el error C7626 para el código no conforme cuando se especifica **`/std:c++latest`** .

En el ejemplo siguiente se muestran las construcciones que ya no se permiten en las estructuras sin nombre. Según el modo estándar especificado, se emiten errores o advertencias de C5208 o C7626:

```cpp
struct B { };
typedef struct : B { // inheriting from 'B'; ill-formed
    void f(); // ill-formed
    static int i; // ill-formed
    struct U {
        void f(); // nested class has non-data member; ill-formed
    };
    int j = 10; // default member initializer; ill-formed
} S;
```

El código anterior se puede corregir asignando un nombre a la clase sin nombre:

```cpp
struct B { };
typedef struct S_ : B {
    void f();
    static int i;
    struct U {
        void f();
    };
    int j = 10;
} S;
```

### <a name="default-argument-import-in-ccli"></a>Importación de argumentos predeterminados en C++ o CLI

Debido al creciente número de API que tienen argumentos predeterminados en .NET Core, ahora se admite la importación de argumentos predeterminados en C++ o CLI. Este cambio puede afectar al código existente en el que se declaran varias sobrecargas, como en este ejemplo:

```cpp
public class R {
    public void Func(string s) {}   // overload 1
    public void Func(string s, string s2 = "") {} // overload 2;
}
```

Cuando esta clase se importa en C++ o CLI, una llamada a una de las sobrecargas produce un error:

```cpp
    (gcnew R)->Func("abc"); // error C2668: 'R::Func' ambiguous call to overloaded function
```

El compilador emite el error C2668 porque ambas sobrecargas coinciden con esta lista de argumentos. En la segunda sobrecarga, el segundo argumento se rellena con el argumento predeterminado. Para solucionar este problema, puede eliminar la sobrecarga redundante (1). O bien, use la lista de argumentos completa y proporcione explícitamente los argumentos predeterminados.

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019"></a><a name="update_160"></a> Correcciones de errores y cambios de comportamiento en Visual Studio 2019

### <a name="reinterpret_cast-in-a-constexpr-function"></a>Reinterpret_cast en una función constexpr

**Reinterpret_cast** no es válido en una función **constexpr**. El compilador de Microsoft C++ anteriormente rechazaba **reinterpret_cast** solo si se usaba en un contexto de **constexpr**. En Visual Studio 2019, en todos los modos estándar de lenguaje, el compilador diagnostica correctamente **reinterpret_cast** en la definición de una función **constexpr**. El código siguiente genera ahora el error C3615 `constexpr function 'f' cannot result in a constant expression`.

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

Para evitar el error, quite el modificador **constexpr** de la declaración de función.

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>Diagnóstico correcto del constructor de rango de basic_string

En Visual Studio 2019, el constructor de rango `basic_string` ya no suprime los diagnósticos de compilador con `static_cast`. El siguiente código se compila sin advertencias en Visual Studio 2017, a pesar de la posible pérdida de datos de `wchar_t` a **char** al inicializar `out`:

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 genera correctamente la advertencia C4244: `'argument': conversion from 'wchar_t' to 'const _Elem', possible loss of data`. Para evitar la advertencia, puede inicializar std::string como se muestra en este ejemplo:

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Ahora las llamadas incorrectas a += y -= bajo /clr o/ZW se detectan debidamente

En Visual Studio 2017 se producía un error que hacía que el compilador ignorara los errores inadvertidamente y no generara ningún código para las llamadas no válidas a += y -= bajo `/clr` o `/ZW`. El siguiente código se compila sin errores en Visual Studio 2017, pero en Visual Studio 2019 genera correctamente el error C2845 `'System::String ^': pointer arithmetic not allowed on this type`:

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Para evitar el error del ejemplo, use el operador con el método ToString(): `s += E::e.ToString();`.

### <a name="initializers-for-inline-static-data-members"></a>Inicializadores de miembros de datos estáticos en línea

Los accesos de miembros no válidos dentro de los inicializadores **alineado** y **constexpr estático** ahora se detectan correctamente. El ejemplo siguiente se compila sin errores en Visual Studio 2017, pero en Visual Studio 2019 en el modo **`/std:c++17`** se genera el error C2248: `cannot access private member declared in class 'X'`.

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

MSVC solía tener una advertencia de rendimiento C4800 sobre la conversión implícita a **bool**. Era demasiado ruidosa y no se pudo eliminar, lo que nos llevó a quitarla en Visual Studio 2017. Sin embargo, durante el ciclo de vida de Visual Studio 2017 recibimos muchos comentarios sobre lo útil que era para resolver ciertos casos. En Visual Studio 2019 volvemos a incorporar una advertencia C4800 cuidadosamente diseñada, junto con la advertencia explicativa C4165. Ambas advertencias son fáciles de suprimir: mediante el uso de una conversión explícita o por comparación con 0 del tipo adecuado. C4800 es una advertencia de nivel 4 que está desactivada de forma predeterminada y C4165, una advertencia de nivel 3 que está desactivada de forma predeterminada. Ambas pueden detectarse con la opción de compilador `/Wall`.

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

En Visual Studio 2017, la advertencia C4822 `Local class member function doesn't have a body` solo se genera cuando la opción del compilador `/w14822` se establece explícitamente. No se muestra con `/Wall`. En Visual Studio 2019, C4822 es una advertencia desactivada de forma predeterminada que hace que sea detectable en `/Wall` sin tener que establecer `/w14822` explícitamente.

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Cuerpos de función de plantilla que contienen instrucciones if constexpr

Los cuerpos de función de plantilla que contienen instrucciones **if constexpr** tienen habilitadas algunas comprobaciones relacionadas con el análisis [/permissive-](../build/reference/permissive-standards-conformance.md). Por ejemplo, en Visual Studio 2017 el siguiente código genera el error C7510 `'Type': use of dependent type name must be prefixed with 'typename'` solo si no se establece la opción **`/permissive-`** . En Visual Studio 2019, el mismo código genera errores incluso cuando la opción **`/permissive-`** está establecida:

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

Para evitar el error, agregue la palabra clave **typename** a la declaración de `a`: `typename T::Type a;`.

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>El código de ensamblado en línea no se admite en una expresión lambda

Recientemente se puso en conocimiento del equipo de Microsoft C++ un problema de seguridad por el cual el uso de un ensamblador en línea en una expresión lambda podía provocar daños en `ebp` (el registro de remites) en tiempo de ejecución. Un atacante malintencionado podría sacar provecho de este escenario. El ensamblador alineado solo se admite en x86 y la interacción entre el ensamblador insertado y el resto del compilador es deficiente. Dados estos hechos y la naturaleza del problema, la solución más segura para este problema era impedir el ensamblador insertado en una expresión lambda.

El único uso del ensamblador en línea dentro de una expresión lambda que hemos encontrado de facto fue capturar el remite. En este escenario, se pueden capturar los remites de todas las plataformas utilizando tan solo una función intrínseca de compilador `_ReturnAddress()`.

El código siguiente genera el error C7552 `inline assembler is not supported in a lambda` en Visual Studio 2017 15.9 y en Visual Studio 2019:

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

### <a name="iterator-debugging-and-stdmove_iterator"></a>Depuración de iterador y `std::move_iterator`

La característica de depuración de iterador se ha diseñado para desajustar `std::move_iterator` correctamente. Por ejemplo, `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` ahora puede participar en el método rápido `memcpy`.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Correcciones para la aplicación de la palabra clave \<xkeycheck.h>

Se ha corregido la macro de la biblioteca estándar que reemplaza una aplicación de palabra clave \<xkeycheck.h> para emitir la palabra clave del problema real que se detecta, en lugar de un mensaje genérico. También admite palabras clave de C++20 y evita la falsa detección de IntelliSense de palabras clave aleatorias como macros.

### <a name="allocator-types-no-longer-deprecated"></a>Tipos de asignador que ya no está en desuso

`std::allocator<void>`, `std::allocator::size_type` y `std::allocator::difference_type` ya no están en desuso.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Advertencia correcta para restringir conversiones de cadena

Se ha quitado un elemento falso `static_cast` de `std::string` no convocado por el estándar y que suprimía por error las advertencias de restricción de C4244. Los intentos de llamar a `std::string::string(const wchar_t*, const wchar_t*)` ahora emiten correctamente la advertencia C4244 `narrowing a wchar_t into a char`.

### <a name="various-filesystem-correctness-fixes"></a>Varias correcciones de exactitud de \<filesystem>

- Se ha corregido el error `std::filesystem::last_write_time` que se producía al intentar cambiar la última hora de escritura de un directorio.
- Ahora, el constructor `std::filesystem::directory_entry` almacena un resultado erróneo (en lugar de producir una excepción) si se indica una ruta de acceso de destino que no existe.
- La versión de 2 parámetros `std::filesystem::create_directory` se ha cambiado para llamar a la versión de 1 parámetro, ya que la función `CreateDirectoryExW` subyacente usaría `copy_symlink` si `existing_p` fuera un vínculo simbólico.
- `std::filesystem::directory_iterator` ya no genera un error al encontrar un vínculo simbólico roto.
- Ahora, `std::filesystem::space` acepta rutas de acceso relativas.
- `std::filesystem::path::lexically_relative` ya no se confunde ante la presencia de barras diagonales finales, notificadas como [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Se ha solucionado el método `CreateSymbolicLinkW`, que rechazaba las rutas de acceso con barras diagonales en `std::filesystem::create_symlink`.
- Se ha solucionado la función `delete` de modo de eliminación de POSIX que existía en Windows 10 LTSB 1609, pero en realidad los archivos no se pueden eliminar.
- Ahora, los constructores de copia de `std::boyer_moore_searcher` y `std::boyer_moore_horspool_searcher` y los operadores de asignación de copia copian de verdad.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Algoritmos paralelos en Windows 8 y versiones posteriores

Ahora, la biblioteca de algoritmos paralelos usa correctamente la familia `WaitOnAddress` real en Windows 8 y en versiones posteriores, en lugar de usar siempre Windows 7 y versiones anteriores falsas.

### <a name="stdsystem_categorymessage-whitespace"></a>Espacio en blanco `std::system_category::message()`

Ahora, `std::system_category::message()` recorta los espacios en blanco finales en el mensaje devuelto.

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>Dividir por cero `std::linear_congruential_engine`

Se han corregido algunas situaciones en las que `std::linear_congruential_engine` desencadenaría una división entre 0.

### <a name="fixes-for-iterator-unwrapping"></a>Correcciones de desajuste de iteradores

Alguna maquinaria de desajuste de iteradores que se expuso por primera vez para la integración programador-usuario en la versión 15.8 de Visual Studio 2017, tal como se describe en el artículo del blog del equipo de C++ [Correcciones y características de STL en VS 2017 15.8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/). Esta maquinaria ya no desencapsula los iteradores derivados de los iteradores de la biblioteca estándar. Por ejemplo, un usuario que deriva de `std::vector<int>::iterator` e intenta personalizar el comportamiento, ahora obtendrá su comportamiento personalizado cuando llame a algoritmos de la biblioteca estándar, y no el comportamiento de un puntero.

Ahora, la función `reserve` de contenedor sin ordenar reserva de verdad para N elementos, como se describe en [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Control del tiempo

- Antes, algunos valores de tiempo que pasaban a la biblioteca de simultaneidad podían desbordarse, por ejemplo, `condition_variable::wait_for(seconds::max())`. Ahora corregidos, los desbordamientos cambiaban el comportamiento en un ciclo aparentemente aleatorio de 29 días (cuando Win32 subyacente aceptaba uint32_t milisegundos, las API se desbordaban).

- Ahora, el encabezado \<ctime> declara correctamente `timespec` y `timespec_get` en el espacio de nombres `std`, además de declararlos también en el espacio de nombres global.

### <a name="various-fixes-for-containers"></a>Varias correcciones de contenedores

- Muchas de las funciones de contenedor internas de la biblioteca estándar se han convertido en privadas para una mejor experiencia de IntelliSense. Se espera realizar más correcciones para marcar miembros como privados en las versiones posteriores de MSVC.

- Se han corregido varios problemas de exactitud de seguridad de excepción por los que los contenedores basados en nodos como `list`, `map` y `unordered_map` podrían resultar dañados. Durante una operación de reasignación `propagate_on_container_copy_assignment` o `propagate_on_container_move_assignment`, liberaríamos el nodo centinela del contenedor con el asignador anterior, realizaríamos la asignación de POCCA/POCMA sobre el asignador anterior y, a continuación, intentaríamos adquirir el nodo centinela del nuevo asignador. Si se producía un error en esta asignación, el contenedor se dañaba y ni siquiera se podía destruir, ya que un nodo centinela es una estructura de datos rígida invariable. Este código se ha corregido para asignar el nuevo nodo centinela del asignador del contenedor de origen antes de destruir el nodo centinela existente.

- Los contenedores se han corregido de forma que los asignadores siempre se copian/mueven/intercambian según `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment` y `propagate_on_container_swap`, incluso en el caso de los asignadores declarados como `is_always_equal`.

- Se han agregado sobrecargas para las funciones miembro de extracción y combinación de contenedores que aceptan contenedores rvalue según el documento [P0083 sobre la inserción de asignaciones y conjuntos](https://wg21.link/p0083r3).

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>`std::basic_istream::read` procesamiento de \\r\\n = > \\n

`std::basic_istream::read` se ha corregido para que no escriba en partes del búfer proporcionado temporalmente como parte del procesamiento de \\r\\n => \\n. Este cambio cede parte de la ventaja de rendimiento que se obtuvo en Visual Studio 2017 15.8 para lecturas con un tamaño superior a 4K. Sin embargo, las mejoras en la eficiencia de evitar tres llamadas virtuales por carácter todavía están presentes.

### <a name="stdbitset-constructor"></a>Constructor `std::bitset`

El constructor `std::bitset` ya no lee los unos y los ceros en orden inverso en los conjuntos de bits grandes.

### <a name="stdpairoperator-regression"></a>Regresión `std::pair::operator=`

Se ha corregido una regresión en el operador de asignación de `std::pair` que se producía al implementar [LWG 2729 "SFINAE ausente en std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729). Ahora, se vuelven a aceptar correctamente los tipos convertibles a `std::pair`.

### <a name="non-deduced-contexts-for-add_const_t"></a>Contextos no deducidos para `add_const_t`

Se ha corregido un error menor de rasgos de tipos, según el cual da por hecho que `add_const_t` y otras funciones relacionadas están un contexto no deducido. En otras palabras, `add_const_t` debe ser un alias para `typename add_const<T>::type`, no `const T`.

## <a name="bug-fixes-and-behavior-changes-in-162"></a><a name="update_162"></a> Correcciones de errores y cambios de comportamiento en la versión 16.2

### <a name="const-comparators-for-associative-containers"></a>Comparadores const para contenedores asociativos

El código para la búsqueda y la inserción en [set](../standard-library/set-class.md), [map](../standard-library/map-class.md), [multiset](../standard-library/multiset-class.md) y [multimap](../standard-library/multimap-class.md) se ha combinado para reducir el tamaño del código. Las operaciones de inserción ahora llaman a la comparación menor que en el functor de comparación **const**, del mismo modo en que actuaban previamente las operaciones de búsqueda. El código siguiente se compila en la versión 16.1 de Visual Studio 2019 y en versiones anteriores, pero genera C3848 en la versión 16.2 de Visual Studio 2019:

```cpp
#include <iostream>
#include <map>

using namespace std;

struct K
{
   int a;
   string b = "label";
};

struct Comparer  {
   bool operator() (K a, K b) {
      return a.a < b.a;
   }
};

map<K, double, Comparer> m;

K const s1{1};
K const s2{2};
K const s3{3};

int main() {

   m.emplace(s1, 1.08);
   m.emplace(s2, 3.14);
   m.emplace(s3, 5.21);

}
```

Para evitar el error, use el operador de comparación **const**:

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

::: moniker-end

::: moniker range="vs-2017"

## <a name="conformance-improvements-in-visual-studio-2017-rtw-version-150"></a><a name="improvements_150"></a> Mejoras de conformidad en Visual Studio 2017 RTW (versión 15.0)

Gracias a la compatibilidad de **constexpr** generalizado y a la inicialización de miembros de datos no estáticos (NSDMI) para agregados, el compilador de Microsoft C++ en Visual Studio 2017 ya tiene la totalidad de las características que se agregaron en el estándar C++14. Sin embargo, al compilador todavía le faltan algunas características de los estándares C++11 y C++98. Consulte [Tabla de conformidad del lenguaje Microsoft C++](../visual-cpp-language-conformance.md) para ver una tabla que muestra el estado actual del compilador.

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++11: Compatibilidad con expresiones SFINAE en más bibliotecas

El compilador continúa mejorando su compatibilidad con la expresión SFINAE. Se requiere para la deducción y sustitución de argumentos de plantilla donde las expresiones **decltype** y **constexpr** puedan aparecer como parámetros de plantilla. Para más información, vea [Expression SFINAE improvements in Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3) (Mejoras de la expresión SFINAE en Visual Studio 2017 RC).

### <a name="c14-nsdmi-for-aggregates"></a>C++14: NSDMI para agregados

Un agregado es una matriz o una clase que no tiene ningún constructor proporcionado por el usuario, ningún miembro de datos no estático privado o protegido, ninguna clase base y ninguna función virtual. A partir de C++14, los agregados pueden contener inicializadores de miembro. Para más información, vea [Member initializers and aggregates](https://wg21.link/n3605) (Inicializadores de miembro y agregados).

### <a name="c14-extended-constexpr"></a>C++14: **constexpr** extendido

Las expresiones declaradas como **constexpr** ya pueden contener determinados tipos de declaraciones, instrucciones if y switch, instrucciones loop y mutación de objetos cuya duración se haya iniciado durante la evaluación de la expresión constexpr. Ya no es necesario que una función miembro no estática **constexpr** sea **const** de forma implícita. Para más información, vea [Relaxing constraints on constexpr functions](https://wg21.link/n3652) (Relajación de restricciones en funciones constexpr).

### <a name="c17-terse-static_assert"></a>C++17: `static_assert` simplificado

El parámetro de mensaje para `static_assert` es opcional. Para más información, vea [Extending static_assert, v2](https://wg21.link/n3928) (Extensión de static_assert, v2).

### <a name="c17-fallthrough-attribute"></a>C++17: atributo `[[fallthrough]]`

En el modo **`/std:c++17`** , el atributo `[[fallthrough]]` se puede usar en el contexto de las instrucciones switch como una sugerencia al compilador de que se prevé el comportamiento de paso explícito. Este atributo evita que el compilador emita advertencias en estos casos. Para más información, vea [Wording for \[\[fallthrough\]\] attribute](https://wg21.link/p0188r0) (Redacción del atributo [[fallthrough]]).

### <a name="generalized-range-based-for-loops"></a>Bucles for basados en intervalos generalizados

Los bucles for basados en rangos ya no necesitan que `begin()` y `end()` devuelvan objetos del mismo tipo. Este cambio permite que `end()` devuelva un valor de centinela tal como usan los rangos de [range-v3](https://github.com/ericniebler/range-v3) y la especificación técnica de rangos completada pero no publicada. Para obtener más información, vea [Generalizing the Range-Based For Loop](https://wg21.link/p0184r0) (Generalización del bucle for basado en rangos).

## <a name="conformance-improvements-in-153"></a><a name="improvements_153"></a> Mejoras de conformidad en la versión 15.3

### <a name="constexpr-lambdas"></a>Expresiones lambda de constexpr

Las expresiones lambda ahora se pueden usar en expresiones constantes. Para más información, vea [constexpr lambda expressions in C++](../cpp/lambda-expressions-constexpr.md) (Expresiones lambda de constexpr en C++).

### <a name="if-constexpr-in-function-templates"></a>**if constexpr** en plantillas de función

Una plantilla de función puede contener instrucciones **if constexpr** que habilitan la creación de ramas de tiempo de compilación. Para más información, vea [if constexpr statements](../cpp/if-else-statement-cpp.md#if_constexpr) (Instrucciones if constexpr).

### <a name="selection-statements-with-initializers"></a>Instrucciones de selección con inicializadores

Una instrucción **if** puede incluir un inicializador que introduce una variable en el ámbito de bloque dentro de la instrucción misma. Para más información, vea [if statements with initializer](../cpp/if-else-statement-cpp.md#if_with_init) (Instrucciones if con inicializador).

### <a name="maybe_unused-and-nodiscard-attributes"></a>Atributos `[[maybe_unused]]` y `[[nodiscard]]`

El nuevo atributo `[[maybe_unused]]` silencia las advertencias cuando no se usa una entidad. El atributo `[[nodiscard]]` crea una advertencia si se descarta el valor devuelto de una llamada de función. Para más información, consulte [Atributos en C++](../cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Uso de espacios de nombres de atributo sin repetición

Nueva sintaxis para habilitar solo un identificador de espacio de nombres único en una lista de atributos. Para más información, consulte [Atributos en C++](../cpp/attributes.md).

### <a name="structured-bindings"></a>Enlaces estructurados

En una sola declaración ahora es posible almacenar un valor con nombres individuales para sus componentes, cuando el valor es una matriz, un `std::tuple` o `std::pair` o tiene todos los miembros de datos no estáticos públicos. Para más información, vea [Structured Bindings](https://wg21.link/p0144r0) (Enlaces estructurados) y [Returning multiple values from a function](../cpp/functions-cpp.md#multi_val) (Devolver varios valores de una función).

### <a name="construction-rules-for-enum-class-values"></a>Reglas de construcción para valores de **enum class**

Ahora hay una conversión implícita y no restrictiva desde el tipo subyacente de una enumeración con ámbito a la propia enumeración. La conversión está disponible cuando su definición no introduce un enumerador y cuando el origen usa una sintaxis de inicialización de lista. Para más información, vea [Construction Rules for enum class Values](https://wg21.link/p0138r2) (Reglas de construcción para valores enum class) y [Enumerations](../cpp/enumerations-cpp.md#no_enumerators) (Enumeraciones).

### <a name="capturing-this-by-value"></a>Captura de `*this` por valor

El objeto `*this` en una expresión lambda ahora se puede capturar por valor. Este cambio permite escenarios en los que se invoca la expresión lambda en operaciones asincrónicas y en paralelo, en particular en las arquitecturas de máquinas más recientes. Para más información, consulte la [captura de lambda de \*this por valor como \[=,\*this\]](https://wg21.link/p0018r3).

### <a name="removing-operator-for-bool"></a>Quitar `operator++` para **bool**

`operator++` ya no se admite en tipos **bool**. Para más información, consulte el artículo sobre la [elimininación de operator++(bool) en desuso](https://wg21.link/p0002r1).

### <a name="removing-deprecated-register-keyword"></a>Eliminación de la palabra clave **register** en desuso

La palabra clave **register**, anteriormente en desuso (e ignorada por el compilador), ahora se ha eliminado del idioma. Para más información, consulte el artículo sobre la [eliminación del uso de la palabra clave register en desuso](https://wg21.link/p0001r1).

## <a name="conformance-improvements-in-155"></a><a name="improvements_155"></a> Mejoras de conformidad en la versión 15.5

Las características marcadas con \[14] están disponibles sin condiciones, incluso en el modo **`/std:c++14`** .

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nuevo conmutador de compilador para **extern constexpr**

En versiones anteriores de Visual Studio, el compilador siempre proporcionaba una vinculación interna de variable de **constexpr** aunque la variable se marcase como **extern**. En la versión 15.5 de Visual Studio 2017, el nuevo conmutador de compilador, [`/Zc:externConstexpr`](../build/reference/zc-externconstexpr.md), permite un comportamiento correcto que cumple con los estándares. Para obtener más información, vea [Extern constexpr linkage](#extern_linkage) (Vinculación de extern constexpr).

### <a name="removing-dynamic-exception-specifications"></a>Eliminación de las especificaciones de excepciones dinámicas

[P0003R5](https://wg21.link/p0003r5) Las especificaciones de excepción dinámica se dejaron en desuso en C++11. La característica se quitó de C++17, pero la especificación `throw()`, que (todavía) está en desuso, se mantiene estrictamente como un alias de `noexcept(true)`. Para obtener más información, vea [Eliminación de las especificaciones de excepción dinámica y noexcept](#noexcept_removal).

### `not_fn()`

[P0005R4](https://wg21.link/p0005r4) `not_fn` es un sustituto de `not1` y `not2`.

### <a name="rewording-enable_shared_from_this"></a>Nueva redacción de `enable_shared_from_this`

[P0033R1](https://wg21.link/p0033r1)`enable_shared_from_this` se agregó en C++11. En la versión estándar de C++17 se actualiza la especificación para controlar mejor determinados casos extremos. \[14]

### <a name="splicing-maps-and-sets"></a>Inserción de asignaciones y conjuntos

[P0083R3](https://wg21.link/p0083r3) Esta característica permite la extracción de nodos de los contenedores asociativos (por ejemplo, `map`, `set`, `unordered_map` o `unordered_set`) que posteriormente se pueden modificar y volver a insertar en el mismo contenedor o en otro que use el mismo tipo de nodo. Un caso de uso habitual es extraer un nodo de un `std::map`, cambiar la clave y volverlo a insertar.

### <a name="deprecating-vestigial-library-parts"></a>Desuso de vestigios de elementos de biblioteca

[P0174R2](https://wg21.link/p0174r2) Varias características de la biblioteca estándar de C++ se han reemplazado por características nuevas a lo largo de los años, o bien se ha detectado que eran problemáticas o no eran útiles. Estas características están oficialmente en desuso en C++17.

### <a name="removing-allocator-support-in-stdfunction"></a>Eliminación de la compatibilidad con el asignador en `std::function`

[P0302R1](https://wg21.link/p0302r1) Antes de C++17, la plantilla de clase `std::function` tenía varios constructores que usaban un argumento asignador. Sin embargo, el uso de argumentos allocator en este contexto era problemático, y la semántica no era clara. Se han quitado los constructores del problema.

### <a name="fixes-for-not_fn"></a>Correcciones para `not_fn()`

[P0358R1](https://wg21.link/p0358r1) La nueva redacción de `std::not_fn` ofrece más posibilidades para la propagación de categorías de valor cuando se usa en una invocación de contenedores.

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](https://wg21.link/p0414r2) Los cambios de `shared_ptr` de Elementos fundamentales de biblioteca se combinan en C++17. \[14]

### <a name="fixing-shared_ptr-for-arrays"></a>Corrección de `shared_ptr` para las matrices

[P0497R0](https://wg21.link/p0497r0) Correcciones de la compatibilidad de shared_ptr con las matrices. \[14]

### <a name="clarifying-insert_return_type"></a>Aclaración de `insert_return_type`

[P0508R0](https://wg21.link/p0508r0) Los contenedores asociativos con claves únicas y los contenedores desordenados con claves únicas tienen una función de miembro `insert` que devuelve el tipo anidado `insert_return_type`. Ahora, este tipo de valor devuelto se define como la especialización de un tipo parametrizado en las propiedades Iterator y NodeType del contenedor.

### <a name="inline-variables-for-the-standard-library"></a>Variables insertadas para la biblioteca estándar

[P0607R0](https://wg21.link/p0607r0)

### <a name="annex-d-features-deprecated"></a>Características de anexo D en desuso

El anexo D de la versión estándar de C++ contiene todas las características que están en desuso, como `shared_ptr::unique()`, `<codecvt>` y `namespace std::tr1`. Cuando se establece el compilador **`/std:c++17`** , casi todas las características de la biblioteca estándar que hay en el anexo D se marcan como en desuso. Para más información, vea el artículo [Las características de la biblioteca estándar que hay en el anexo D se han marcado como en desuso](#annex_d).

El espacio de nombres `std::tr2::sys` de `<experimental/filesystem>` ahora emite una advertencia de desuso en **`/std:c++14`** de forma predeterminada, y ahora se ha eliminado en **`/std:c++17`** de forma predeterminada.

Se ha mejorado la conformidad en `<iostream>` evitando una extensión no estándar (especializaciones explícitas en clase).

La biblioteca estándar ahora usa plantillas de variables de forma interna.

La biblioteca estándar se actualizó en respuesta a los cambios del compilador de C++17. Las actualizaciones incluyen la adición de **noexcept** en el sistema de tipos y la eliminación de especificaciones de excepciones dinámicas.

## <a name="conformance-improvements-in-156"></a><a name="improvements_156"></a> Mejoras de conformidad en la versión 15.6

### <a name="c17-library-fundamentals-v1"></a>Elementos fundamentales de biblioteca para C++17 V1

[P0220R1](https://wg21.link/p0220r1) incorpora especificaciones técnicas de elementos fundamentales de biblioteca para C++17 en el estándar. Afecta a las actualizaciones de \<experimental/tuple>, \<experimental/optional>, \<experimental/functional>, \<experimental/any>, \<experimental/string_view>, \<experimental/memory>, \<experimental/memory_resource> y \<experimental/algorithm>.

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++17: Mejora de la deducción de argumentos de plantilla de clase para la biblioteca estándar

[P0739R0](https://wg21.link/p0739r0) desplaza `adopt_lock_t` al frente de la lista de parámetros para que `scoped_lock` pueda permitir un uso coherente de `scoped_lock`. También se permite que el constructor `std::variant` participe en la resolución de sobrecarga en más casos para habilitar la asignación de copias.

## <a name="conformance-improvements-in-157"></a><a name="improvements_157"></a> Mejoras de conformidad en la versión 15.7

### <a name="c17-rewording-inheriting-constructors"></a>C++17: Nueva redacción de constructores de herencia

[P0136R1](https://wg21.link/p0136r1) especifica que una declaración **using** que designa a un constructor ahora hace que los constructores de la clase base correspondientes sean visibles para las inicializaciones de la clase derivada, en lugar de declarar constructores de la clase derivada adicionales. Esta nueva redacción es un cambio con respecto a C ++ 14. En la versión 15.7 de Visual Studio 2017 y en las posteriores, en el modo **`/std:c++17`** , el código válido en C++14 y que usa constructores de herencia puede no ser válido o es posible que tenga otras semánticas.

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

En el ejemplo siguiente se muestra el comportamiento de **`/std:c++17`** en Visual Studio 15.7:

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

Para obtener más información, vea [Constructores](../cpp/constructors-cpp.md#inheriting_constructors).

### <a name="c17-extended-aggregate-initialization"></a>C++17: Inicialización de agregados extendidos

[P0017R1](https://wg21.link/p0017r1)

Si el constructor de una clase base no es público, pero es accesible para una clase derivada, en el modo **`/std:c++17`** de la versión 15.7 de Visual Studio 2017 ya no se pueden usar llaves vacías para inicializar un objeto del tipo derivado.
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

En C ++ 17, `Derived` ahora se considera un tipo de agregado. Eso significa que la inicialización de `Base` mediante el constructor privado predeterminado se produce directamente como parte de la regla de inicialización de agregados extendida. Anteriormente, el constructor privado `Base` se llamaba a través del constructor `Derived` y se realizaba correctamente debido a la declaración friend.
En el ejemplo siguiente se muestra el comportamiento de C++17 en la versión 15.7 de Visual Studio en el modo **`/std:c++17`** :

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

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17: Declaración de parámetros de plantilla sin tipo con auto

[P0127R2](https://wg21.link/p0127r2)

En el modo **`/std:c++17`** , el compilador ahora puede deducir el tipo de un argumento de plantilla que no sea del tipo que se declara con **auto**:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

Una de las consecuencias que presenta esta nueva característica es que el código válido para C++14 puede no ser válido o tener otra semántica. Por ejemplo, algunas sobrecargas que no eran válidas anteriormente ahora lo son. En el ejemplo siguiente se muestra código de C++14 que se compila porque la llamada a `example(p)` está enlazada a `example(void*);`. En la versión 15.7 de Visual Studio 2017, en el modo **`/std:c++17`** , la plantilla de función `example` es la mejor coincidencia.

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

En el ejemplo siguiente se muestra código de C++17 en Visual Studio 15.7 en el modo **`/std:c++17`** :

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17: Conversiones de cadena elementales (parcial)

[P0067R5](https://wg21.link/p0067r5) incluye funciones de bajo nivel e independientes de la configuración regional para las conversiones entre cadenas y enteros, así como entre cadenas y números de punto flotante.

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++20: Evitación de "decay" no necesarios para (parcial)

[P0777R1](https://wg21.link/p0777r1) agrega diferenciación entre el concepto de "decay" y el de la eliminación de los calificadores const o reference.  El nuevo rasgo de tipo `remove_reference_t` reemplaza `decay_t` en algunos contextos. La compatibilidad con `remove_cvref_t` se implementa en Visual Studio 2019.

### <a name="c17-parallel-algorithms"></a>C++17: Algoritmos paralelos

En [P0024R2](https://wg21.link/p0024r2), el TS de paralelismo se incorpora en el estándar con modificaciones menores.

### <a name="c17-hypotx-y-z"></a>C++17: `hypot(x, y, z)`

[P0030R1](https://wg21.link/p0030r1) agrega tres nuevas sobrecargas a `std::hypot`, para los tipos **float**, **double** y **long double**, cada uno de los cuales tiene tres parámetros de entrada.

### <a name="c17-filesystem"></a>C++17: \<filesystem>

[P0218R1](https://wg21.link/p0218r1) adopta el TS del sistema de archivos en el estándar con algunas modificaciones de redacción.

### <a name="c17-mathematical-special-functions"></a>C++17: Funciones matemáticas especiales

[P0226R1](https://wg21.link/p0220r1) adopta especificaciones técnicas anteriores para funciones matemáticas especiales en el encabezado \<cmath> estándar.

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++17: Guías de deducción para la biblioteca estándar

[P0433R2](https://wg21.link/p0433r2) se actualiza a STL para aprovechar las ventajas de la adopción de C++17 de [P0091R3](https://wg21.link/p0091r3), que agrega compatibilidad con la deducción de argumentos de plantilla de clase.

### <a name="c17-repairing-elementary-string-conversions"></a>C++17: Reparación de conversiones de cadenas elementales

[P0682R1](https://wg21.link/p0682r1) desplaza las nuevas funciones de conversión de cadenas elementales de P0067R5 a un nuevo encabezado \<charconv>. También presenta otras mejoras, incluido el cambio de control de errores para usar `std::errc` en lugar de `std::error_code`.

### <a name="c17-constexpr-for-char_traits-partial"></a>C++17: **constexpr** para `char_traits` (parcial)

[P0426R1](https://wg21.link/p0426r1) incluye cambios relativos a las funciones `length`, `compare` y `find` del miembro `std::traits_type` para que se pueda usar `std::string_view` en expresiones constantes. (En la versión 15.6 de Visual Studio 2017 solo se admite para Clang/LLVM. En la versión 15.7 Preview 2, la compatibilidad es casi completa con CIXX también).

## <a name="conformance-improvements-in-159"></a><a name="improvements_159"></a> Mejoras de conformidad en la versión 15.9

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>Orden de evaluación de izquierda a derecha para los operadores `->*`, `[]`, `>>` y `<<`

A partir de C++17, los operandos de los operadores `->*`, `[]`, `>>` y `<<` deben evaluarse en orden de izquierda a derecha. Hay dos casos en los que el compilador no puede garantizar este orden:

- cuando una de las expresiones del operando es un objeto que se pasa por valor o contiene un objeto que se pasa por valor, o

- cuando se compila con **`/clr`** y uno de los operandos es un campo de un objeto o un elemento de una matriz.

El compilador emite una advertencia [C4866](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017) cuando no puede garantizar la evaluación de izquierda a derecha. El compilador genera esta advertencia solo si se especifica **`/std:c++17`** o posterior, ya que el requisito de orden de izquierda a derecha de estos operadores se introdujo en C++17.

Para resolver esta advertencia, primero debe considerar si es necesario la evaluación de izquierda a derecha de los operandos. Por ejemplo, podría ser necesario cuando la evaluación de los operandos podría producir efectos secundarios dependientes del orden. El orden en que se evalúan los operandos no tiene un efecto observable en muchos casos. Si el orden de evaluación debe ser de izquierda a derecha, considere si puede pasar los operandos por referencia const en su lugar. Este cambio elimina la advertencia en el siguiente ejemplo de código:

```cpp
// C4866.cpp
// compile with: /w14866 /std:c++17

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x) : x(x) {}
    HasCopyConstructor(const HasCopyConstructor& h) : x(h.x) { }
};

int operator>>(HasCopyConstructor a, HasCopyConstructor b) { return a.x >> b.x; }

// This version of operator>> does not trigger the warning:
// int operator>>(const HasCopyConstructor& a, const HasCopyConstructor& b) { return a.x >> b.x; }

int main()
{
    HasCopyConstructor a{ 1 };
    HasCopyConstructor b{ 2 };

    a>>b;        // C4866 for call to operator>>
};
```

## <a name="bug-fixes-in-visual-studio-2017-rtw-version-150"></a><a name="update_150"></a> Correcciones de errores en Visual Studio 2017 RTW (versión 15.0)

### <a name="copy-list-initialization"></a>Inicialización de lista de copia

Visual Studio 2017 genera correctamente errores del compilador relacionados con la creación de objetos mediante listas de inicializadores. Estos errores no se detectaron en Visual Studio 2015 y podrían provocar bloqueos o un comportamiento indefinido en tiempo de ejecución. Conforme a N4594 13.3.1.7p1, en la inicialización de lista de copia el compilador debe tener en cuenta un constructor explícito para la resolución de sobrecarga, pero debe generar un error si se elige esa sobrecarga concreta.

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

### <a name="constexpr"></a>**constexpr**

Visual Studio 2017 genera correctamente un error si el operando izquierdo de una operación de evaluación condicional no es válido en un contexto constexpr. El siguiente código se compila en Visual Studio 2015, pero no en Visual Studio 2017, donde genera el error C3615 `constexpr function 'f' cannot result in a constant expression`:

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

Para corregir el error, declare la función `array::size()` como **constexpr** o quite el calificador **constexpr** de `f`.

### <a name="class-types-passed-to-variadic-functions"></a>Tipos de clase pasados a funciones variádicas

En Visual Studio 2017, las clases o structs pasados a una función variádica como `printf` se deben poder copiar trivialmente. Al pasar objetos de este tipo, el compilador simplemente realiza una copia bit a bit y no llama al constructor ni al destructor.

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

o bien usar una conversión estática para convertir el objeto antes de pasarlo:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

En el caso de las cadenas compiladas y administradas por medio de CString, se debe usar el `operator LPCTSTR()` proporcionado para convertir un objeto CString en el puntero C esperado por la cadena de formato.

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Calificadores cv en la construcción de clases

En Visual Studio 2015, el compilador a veces omite incorrectamente al calificador cv al generar un objeto de clase mediante una llamada al constructor. Este problema puede causar un bloqueo o un comportamiento inesperado en tiempo de ejecución. En el ejemplo siguiente se compila en Visual Studio 2015, pero se genera un error del compilador en Visual Studio 2017:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Para corregir el error, declare `operator int()` como **const**.

### <a name="access-checking-on-qualified-names-in-templates"></a>Comprobación de acceso en nombres completos en plantillas

Las versiones anteriores del compilador no comprueban el acceso a nombres completos en algunos contextos de plantilla. Este problema puede interferir con el comportamiento esperado de SFINAE, ya que se espera un error en la sustitución debido a la inaccesibilidad de un nombre. Podría haber provocado un bloqueo o un comportamiento inesperado en tiempo de ejecución, ya que el compilador habría llamado incorrectamente a la sobrecarga incorrecta del operador. En Visual Studio 2017, se genera un error del compilador. El error específico puede variar, pero normalmente es C2672 `no matching overloaded function found`. El siguiente código se compila en Visual Studio 2015, pero genera un error en Visual Studio 2017:

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

En Visual Studio 2015 y versiones anteriores, el compilador no diagnosticó las listas de argumentos de plantillas que faltaban cuando la plantilla aparecía en una lista de parámetros de plantilla: Por ejemplo, cuando falta parte de un argumento de plantilla predeterminado o un parámetro de plantilla sin tipo. Este problema puede provocar un comportamiento impredecible, como el bloqueo del compilador o un comportamiento inesperado en tiempo de ejecución. El siguiente código se compila en Visual Studio 2015, pero genera un error en Visual Studio 2017.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Expresión SFINAE

Para admitir la expresión SFINAE, el compilador ahora analiza argumentos **decltype** cuando las plantillas se declaran en lugar de crear instancias. Por consiguiente, si se encuentra una especialización no dependiente en el argumento decltype, no se aplaza al tiempo de creación de instancias. Se procesa inmediatamente y los errores resultantes se diagnostican en ese momento.

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

Según el estándar de C++, una clase que se declara dentro de un espacio de nombres anónimo tiene vinculación interna y, eso significa que no se puede exportar. En Visual Studio 2015 y versiones anteriores no se aplicó esta regla. En Visual Studio 2017 se aplica la regla de forma parcial. En Visual Studio 2017, el ejemplo siguiente genera el error C2201 `const anonymous namespace::S1::vftable: must have external linkage in order to be exported/imported.`.

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Inicializadores predeterminados para miembros de clase de valor (C++/CLI)

En Visual Studio 2015 y versiones anteriores, el compilador permitía (aunque omitía) un inicializador de miembro predeterminado para un miembro de una clase de valor. La inicialización predeterminada de una clase de valor siempre inicializa a cero a los miembros. No se permite un constructor predeterminado. En Visual Studio 2017, los inicializadores de miembro predeterminados generan un error del compilador, tal como se muestra en este ejemplo:

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Indizadores predeterminados (C++/CLI)

En Visual Studio 2015 y versiones anteriores, el compilador en algunos casos identificaba incorrectamente una propiedad predeterminada como un indizador predeterminado. Era posible solucionar el problema con el identificador **default** para acceder a la propiedad. La solución en sí misma se volvió problemática después de que se empezara a usar **default** como palabra clave en C++11. En Visual Studio 2017, se corrigieron los errores que requerían la solución. El compilador ahora genera un error cuando se utiliza **default** para acceder a la propiedad predeterminada de una clase.

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

## <a name="bug-fixes-in-153"></a><a name="update_153"></a> Correcciones de errores en la versión 15.3

### <a name="calls-to-deleted-member-templates"></a>Llamadas a plantillas de miembro eliminado

En versiones anteriores de Visual Studio, había ocasiones en que el compilador no podía emitir un error en las llamadas con un formato incorrecto a una plantilla de miembro eliminado. Estas llamadas podrían causar bloqueos en tiempo de ejecución. El código siguiente ahora produce el error C2280 `'int S<int>::f<int>(void)': attempting to reference a deleted function`:

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

Para corregir el error, declare `i` como **int**.

### <a name="pre-condition-checks-for-type-traits"></a>Comprobaciones de condición previa para type traits

La versión 15.3 de Visual Studio 2017 mejora las comprobaciones de condición previa para type-traits a fin de seguir el estándar de manera más estricta. Una de estas comprobaciones es para asignable. El código siguiente produce el error C2139 en la versión 15.3 de Visual Studio 2017:

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nuevas advertencias de compilador y comprobaciones en tiempo de ejecución en la serialización nativa a administrada

La llamada de funciones administradas a funciones nativas requiere la serialización. El CLR realiza la serialización, pero no comprende la semántica de C++. Si se pasa un objeto nativo por valor, CLR llama al constructor de copia del objeto o usa `BitBlt`, lo que puede provocar un comportamiento indefinido en tiempo de ejecución.

Ahora, el compilador emite una advertencia si determina en tiempo de compilación que se pasa un objeto nativo con el constructor de copia eliminada entre límites nativos y administrados por valor. En aquellos casos en los que el compilador no lo sepa en tiempo de compilación, se inyecta una comprobación en tiempo de ejecución para que el programa llame a `std::terminate` inmediatamente cuando se produzca una serialización con un formato incorrecto. En la versión 15.3 de Visual Studio 2017, el código siguiente produce la advertencia C4606 `'A': passing argument by value across native and managed boundary requires valid copy constructor. Otherwise, the runtime behavior is undefined.`.

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
    f(A()); // This call from managed to native requires marshaling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

Para corregir el error, quite la directiva `#pragma managed` para marcar el llamador como nativo y evitar la serialización.

### <a name="experimental-api-warning-for-winrt"></a>Advertencia de API experimental para WinRT

Las API de WinRT que se publican para experimentación y comentarios se decoran con `Windows.Foundation.Metadata.ExperimentalAttribute`. En la versión 15.3 de Visual Studio 2017, el compilador produce la advertencia C4698 para este atributo. Algunas API de versiones anteriores del SDK de Windows se han decorado con el atributo, y las llamadas a estas API ahora desencadenan esta advertencia del compilador. Los SDK de Windows más recientes tienen el atributo quitado de todos los tipos enviados. Si usa un SDK antiguo, deberá suprimir estas advertencias en todas las llamadas a tipos enviados.

El código siguiente produce la advertencia C4698 `'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' is for evaluation purposes only and is subject to change or removal in future updates`:

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

La versión 15.3 de Visual Studio 2017 produce un error para una definición fuera de línea de una función de miembro de plantilla que no se ha declarado en la clase. El código siguiente ahora produce el error C2039 `'f': is not a member of 'S'`:

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

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Intento de tomar la dirección del puntero **this**

En C++, **`this`** es un prvalue de puntero de tipo a X. No puede tomar la dirección de **`this`** ni enlazarlo a una referencia lvalue. En versiones anteriores de Visual Studio, el compilador le permitiría eludir esta restricción mediante el uso de una conversión. En la versión 15.3 de Visual Studio 2017, el compilador genera el error C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Conversión a una clase base inaccesible

La versión 15.3 de Visual Studio 2017 genera un error cuando se intenta convertir un tipo a una clase base que es inaccesible. El compilador ahora genera el error C2243 `'type cast': conversion from 'D *' to 'B *' exists, but is inaccessible`. El código siguiente es incorrecto y podría provocar un bloqueo en tiempo de ejecución. El compilador produce ahora el error C2243 cuando encuentra código como este:

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>No se permiten argumentos predeterminados en definiciones fuera de línea de funciones miembro

No se permiten argumentos predeterminados en definiciones fuera de línea de funciones miembro en clases de plantilla. El compilador emitirá una advertencia en **`/permissive`** y un error de hardware en [/permissive-](../build/reference/permissive-standards-conformance.md).

En versiones anteriores de Visual Studio, el siguiente código con formato incorrecto podría generar un bloqueo en tiempo de ejecución. En la versión 15.3 de Visual Studio 2017 se produce la advertencia C5034 `'A\<T>::f': an out-of-line definition of a member of a class template cannot have default arguments`:

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

### <a name="use-of-offsetof-with-compound-member-designator"></a>Uso de `offsetof` con el designador de miembro compuesto

En la versión 15.3 de Visual Studio 2017, el uso de `offsetof(T, m)`, donde *m* es un "designador de miembro compuesto", da lugar a una advertencia al compilar con la opción **`/Wall`** . El código siguiente tiene un formato incorrecto y podría provocar un bloqueo en tiempo de ejecución. En la versión 15.3 de Visual Studio 2017 se produce la advertencia C4841 `non-standard extension used: compound member designator in offsetof`:

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

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Uso de `offsetof` con un miembro de datos estático o una función miembro

En la versión 15.3 de Visual Studio 2017, el uso de `offsetof(T, m)`, donde *m* hace referencia a un miembro de datos estático o a una función miembro, da error. El código siguiente genera el error C4597 `undefined behavior: offsetof applied to member function 'example'` y el error C4597 `undefined behavior: offsetof applied to static data member 'sample'`:

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

Este código no tiene un formato correcto y podría ocasionar un bloqueo en tiempo de ejecución. Para corregir el error, cambie el código para que deje de invocar un comportamiento indefinido. Se trata de código no portable que no admite el estándar de C++.

### <a name="new-warning-on-__declspec-attributes"></a><a name="declspec"></a> Nueva advertencia en los atributos `__declspec`

En la versión 15.3 de Visual Studio 2017, el compilador ya no ignora los atributos si `__declspec(...)` se aplica antes de la especificación de vinculación de `extern "C"`. Anteriormente, el compilador ignoraría el atributo, lo que podría tener implicaciones para el tiempo de ejecución. Cuando se establecen las opciones **`/Wall`** y **`/WX`** , el código siguiente genera la advertencia C4768 `__declspec attributes before linkage specification are ignored`:

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Para corregir la advertencia, coloque primero `extern "C"`:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Esta advertencia está desactivada de forma predeterminada en la versión 15.3, pero activada de forma predeterminada en la versión 15.5, y solo afecta al código compilado con **`/Wall`** **`/WX`** .

### <a name="decltype-and-calls-to-deleted-destructors"></a>**decltype** y llamadas a destructores eliminados

En versiones anteriores de Visual Studio, el compilador no detectaba cuándo se producía una llamada a un destructor eliminado en el contexto de la expresión asociada a **decltype**. En la versión 15.3 de Visual Studio 2017, el código siguiente produce el error C2280 `'A<T>::~A(void)': attempting to reference a deleted function`:

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

La versión Visual Studio 2017 RTW tenía una regresión: el compilador de C++ no emitía un diagnóstico para una variable **const** no inicializada. Esta regresión se ha corregido en Visual Studio 2017 versión 15.3. El código siguiente ahora produce la advertencia C4132 `'Value': const object should be initialized`:

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

Para quitar las advertencias, conviértalas en comentario o quite las declaraciones vacías. En casos donde el objeto sin nombre no tenga que tener un efecto secundario (como RAII), se le debe proporcionar un nombre.

La advertencia se excluye en **`/Wv:18`** y está activada de forma predeterminada en el nivel de advertencia W2.

### <a name="stdis_convertible-for-array-types"></a>`std::is_convertible` para tipos de matriz

Las versiones anteriores del compilador daban resultados incorrectos para [std::is_convertible](../standard-library/is-convertible-class.md) con los tipos de matriz. Esto requería que los autores de bibliotecas distinguieran mayúsculas y minúsculas en el compilador de Microsoft C++ al usar el rasgo de tipo `std::is_convertible<...>`. En el siguiente ejemplo, las aserciones estáticas se validan en versiones anteriores de Visual Studio, pero no en Visual Studio 2017 versión 15.3:

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

### <a name="private-destructors-and-stdis_constructible"></a>Destructores privados y `std::is_constructible`

Las versiones anteriores del compilador omitían si un destructor era privado al decidir el resultado de [std::is_constructible](../standard-library/is-constructible-class.md). Ahora sí se tiene en cuenta. En el siguiente ejemplo, las aserciones estáticas se validan en versiones anteriores de Visual Studio, pero no en Visual Studio 2017 versión 15.3:

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

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: Ambiguous overload resolution (resolución de sobrecarga ambigua)

A veces, las versiones anteriores del compilador no eran capaces de detectar la ambigüedad cuando encontraban varios candidatos por medio tanto de declaraciones como de búsquedas dependientes de argumentos. Este error puede hacer que se elija la sobrecarga incorrecta y que ello derive en un comportamiento inesperado del entorno de ejecución. En el ejemplo siguiente, la versión 15.3 de Visual Studio 2017 genera correctamente la advertencia C2668 `'f': ambiguous call to overloaded function`:

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

Las declaraciones de función locales ocultan la declaración de función en el ámbito de inclusión y deshabilitan la búsqueda dependiente de argumentos. Sin embargo, en este caso, las versiones anteriores del compilador hacían que se realizara una búsqueda dependiente de argumentos. Esto podría hacer que se elija la sobrecarga incorrecta y que ello derive en un comportamiento inesperado del entorno de ejecución. Este error suele deberse a una firma incorrecta de la declaración de función local. En el ejemplo siguiente, la versión 15.3 de Visual Studio 2017 genera correctamente la advertencia C2660 `'f': function does not take two arguments`:

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

Los miembros de clase se inicializan en el orden en que se declaran, no en el orden en que aparecen en las listas de inicializadores. Las versiones anteriores del compilador no avisaban cuando el orden de la lista de inicializadores difería del orden de declaración. Este problema podía provocar un comportamiento indefinido del tiempo de ejecución cuando la inicialización de un miembro dependía de otro miembro de la lista ya en proceso de inicialización. En el ejemplo siguiente, la versión 15.3 de Visual Studio 2017 (con **`/Wall`** ) genera la advertencia C5038 `data member 'A::y' will be initialized after data member 'A::x'`:

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Para corregir el problema, organice la lista de inicializadores de forma que tenga el mismo orden que las declaraciones. Cuando uno o ambos inicializadores hacen referencia a miembros de clase base, se genera una advertencia similar.

Esta advertencia está desactivada de forma predeterminada y solo afecta al código compilado con **`/Wall`** .

## <a name="bug-fixes-and-other-behavior-changes-in-155"></a><a name="update_155"></a> Correcciones de errores y cambios de comportamiento en la versión 15.5

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

El problema del ejemplo anterior es que hay dos diferencias en los tipos (const frente a non-const y pack frente a non-pack). Quite una de las diferencias para eliminar el error del compilador. Después, el compilador puede ordenar inequívocamente las funciones.

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

Los controladores de las referencias a un tipo de matriz o función no coinciden nunca con ningún objeto de excepción. Ahora, el compilador respeta esta regla y emite una advertencia de nivel 4. Además, ya no coincide con un controlador de `char*` o `wchar_t*` en un literal de cadena cuando se usa **`/Zc:strictStrings`** .

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

### <a name="stdtr1-namespace-is-deprecated"></a>El espacio de nombres <a name="tr1"></a> `std::tr1` esta en desuso

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
warning C4996: 'std::tr1': warning STL4002: The non-standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
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

### <a name="standard-library-features-in-annex-d-are-marked-as-deprecated"></a><a name="annex_d"></a> Las características de la biblioteca estándar que hay en el anexo D se han marcado como en desuso

Cuando se establece el compilador del modo **`/std:c++17`** , casi todas las características de la biblioteca estándar que hay en el anexo D se marcan como en desuso.

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
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
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

### <a name="single-line-comments"></a>Comentarios en una sola línea

En la versión 15.5 de Visual Studio 2017, el compilador de C ya no emite las advertencias C4001 y C4179. Anteriormente, solo se emitían en el conmutador de compilador de **`/Za`** .  Las advertencias ya no son necesarias porque los comentarios de una sola línea han formado parte del estándar C desde C99.

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

Cuando ya no es necesario que el código sea compatible con versiones anteriores, puede quitar la supresión de C4001/C4179 para evitar la advertencia. De lo contrario, suprima solo C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="__declspec-attributes-with-extern-c-linkage"></a>Atributos `__declspec` con vinculación `extern "C"`

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

Esta nueva advertencia C4768 se muestra en algunos encabezados de Windows SDK que se enviaron con la versión 15.3 de Visual Studio 2017 o una posterior (por ejemplo, la versión 10.0.15063.0, también conocida como RS2 SDK). Sin embargo, las versiones posteriores de los encabezados de Windows SDK (concretamente, ShlObj.h y ShlObj_core.h) se han corregido para que no generen la advertencia. Cuando se le muestre esta advertencia en los encabezados de Windows SDK, puede hacer lo siguiente:

1. Cambie al Windows SDK más reciente incluido en la versión 15.5 de Visual Studio 2017.

1. Desactive la advertencia de #include de la instrucción del encabezado de Windows SDK:

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern-constexpr-linkage"></a><a name="extern_linkage"></a> Vinculación de extern constexpr

En versiones anteriores de Visual Studio, el compilador siempre proporcionaba una vinculación interna de variable de **constexpr** aunque la variable se marcase como **extern**. En la versión 15.5 de Visual Studio 2017, un nuevo conmutador de compilador ( **`/Zc:externConstexpr`** ) permite un comportamiento correcto que cumple con los estándares. Este comportamiento acabará convirtiéndose en el conmutador predeterminado.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Si un archivo de encabezado contiene una variable declarada como **extern constexpr**, tiene que marcarse como `__declspec(selectany)` para que tengan sus declaraciones duplicadas combinadas correctamente:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>No se puede usar **typeid** en tipos de clase incompleta

En versiones anteriores de Visual Studio, el compilador permitía de forma incorrecta el código siguiente, lo que podía generar información de tipo incorrecto. En la versión 15.5 de Visual Studio 2017, el compilador genera correctamente un error:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdis_convertible-target-type"></a>Tipo de destino `std::is_convertible`

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

### <a name="dynamic-exception-specification-removal-and-noexcept"></a><a name="noexcept_removal"></a> Eliminación de especificaciones de excepción dinámica y **noexcept**

En C++17, `throw()` es un alias de **noexcept**, `throw(<type list>)` y `throw(...)` se quitan, y determinados tipos pueden incluir **noexcept**. Este cambio puede generar problemas de compatibilidad de código fuente con código que sea conforme a C++14 o versiones anteriores. El conmutador **`/Zc:noexceptTypes-`** puede usarse para volver a la versión C++14 de **noexcept**, pero se seguirá usando el modo C++17 a nivel general. Esto le permite actualizar el código fuente para que sea conforme con C++17 sin tener que reescribir todo el código de `throw()` a la vez.

Ahora, el compilador también diagnostica más especificaciones de excepción no coincidentes en las declaraciones del modo C++17 o con la opción [/permissive-](../build/reference/permissive-standards-conformance.md) mediante la nueva advertencia C5043.

El código siguiente genera los errores C5043 y C5040 en la versión 15.5 de Visual Studio 2017 cuando se aplica el conmutador **`/std:c++17`** :

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

Para quitar los errores mientras sigue usando **`/std:c++17`** , agregue el conmutador **`/Zc:noexceptTypes-`** a la línea de comandos o bien actualice el código para que use **noexcept**, tal como se indica en el ejemplo siguiente:

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

Ahora, los miembros de datos de static constexpr están alineados de forma implícita, lo que significa que su declaración en una clase es ahora su definición. Usar definiciones fuera de línea para un miembro de datos de static constexpr es redundante y está en desuso. En la versión 15.5 de Visual Studio 2017, cuando se aplica el modificador **`/std:c++17`** , el código siguiente ahora genera la advertencia C5041 `'size': out-of-line definition for constexpr static data member is not needed and is deprecated in C++17`:

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>La advertencia C4768 `extern "C" __declspec(...)` ahora está activada de forma predeterminada

La advertencia se agregó en la versión 15.3 de Visual Studio 2017, pero estaba desactivada de forma predeterminada. En la versión 15.5 de Visual Studio 2017, la advertencia está activada de forma predeterminada. Para más información, vea [Nueva advertencia en los atributos \_\_declspec](#declspec).

### <a name="defaulted-functions-and-__declspecnothrow"></a>Funciones establecidas como valor predeterminado y `__declspec(nothrow)`

Anteriormente, el compilador permitía que las funciones predeterminadas se declarasen con `__declspec(nothrow)` cuando las funciones de base/miembro correspondientes permitían excepciones. Este comportamiento es contrario al estándar de C++ y puede provocar un comportamiento indefinido en el entorno de ejecución. El estándar requiere que estas funciones se definan como eliminadas si se produce un error de coincidencia en la especificación de excepciones.  En **`/std:c++17`** , el código siguiente genera la advertencia C2280 `attempting to reference a deleted function. Function was implicitly deleted because the explicit exception specification is incompatible with that of the implicit declaration.`.

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

### <a name="noexcept-and-partial-specializations"></a>Operador **noexcept** y especializaciones parciales

Con **noexcept** en el sistema de tipo, es posible que las especializaciones parciales para hacer coincidir tipos "callable" determinados no se puedan compilar o que no se pueda elegir la plantilla principal debido a que falte una especialización parcial para los punteros de función noexcept.

En tales casos, es posible que tenga que agregar más especializaciones parciales para controlar los punteros de función **noexcept** y los punteros **noexcept** en las funciones de miembro. Estas sobrecargas solo son lícitas en el modo **`/std:c++17`** . Si hay que conservar la compatibilidad de C++14 con versiones anteriores y está escribiendo código que utilizan otros usuarios, debe restringir estas nuevas sobrecargas a las directivas de `#ifdef`. Si está trabajando en un módulo autocontenido, en lugar de usar restricciones de `#ifdef`, puede compilar con el conmutador **`/Zc:noexceptTypes-`** .

El siguiente código se compila en **`/std:c++14`** , pero no en **`/std:c++17`** con `error C2027: use of undefined type 'A<T>'`:

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

El código siguiente se procesa correctamente en **`/std:c++17`** porque el compilador elige la nueva especialización parcial `A<void (*)() noexcept>`:

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

## <a name="bug-fixes-and-other-behavior-changes-in-157"></a><a name="update_157"></a> Correcciones de errores y cambios de comportamiento en la versión 15.7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17: Argumento predeterminado en la plantilla de clase principal

Este cambio de comportamiento es una condición previa para [Template argument deduction for class templates - P0091R3](https://wg21.link/p0091r3) (Deducción de argumento de plantilla para plantillas de clase: P0091R3).

Anteriormente, el compilador omitía el argumento predeterminado en la plantilla de clase principal:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

En el modo **`/std:c++17`** de la versión 15.7 de Visual Studio 2017 no se ignora el argumento predeterminado:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Resolución de nombres dependientes

Este cambio de comportamiento es una condición previa para [Template argument deduction for class templates - P0091R3](https://wg21.link/p0091r3) (Deducción de argumento de plantilla para plantillas de clase: P0091R3).

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

La versión 15.7 de Visual Studio 2017, en modo **`/std:c++17`** , requiere la palabra clave **typename** en la instrucción **using** de D. Sin **typename**, el compilador producirá la advertencia C4346`'B<T*>::type': dependent name is not a type` y el error C2061 `syntax error: identifier 'type'`:

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

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++17: Atributo `[[nodiscard]]`: aumento del nivel de advertencia

En la versión 15.7 de Visual Studio 2017 en el modo **`/std:c++17`** , el nivel de advertencia de C4834 `discarding return value of function with 'nodiscard' attribute` se incrementa de W3 a W1. Puede deshabilitar la advertencia con una conversión a **void**, o pasando **`/wd:4834`** al compilador.

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Lista de inicialización de la clase base de constructor de plantilla variádica

En ediciones anteriores de Visual Studio, se permitía erróneamente sin ningún error una lista de inicialización de la clase base de constructor de plantilla variádica en la que faltaban los argumentos de plantilla. En Visual Studio 2017 versión 15.7, se genera un error del compilador.

En el siguiente ejemplo de código en la versión 15.7 de Visual Studio 2017 se produce el error C2614 `D<int>: illegal member initialization: 'B' is not a base or member`:

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

### <a name="constexpr-aggregate-initialization"></a>Inicialización de agregado de **constexpr**

Las versiones anteriores del compilador de C++ administraban incorrectamente la inicialización de agregado de **constexpr**. El compilador aceptaba el código no válido en el que a lista de inicialización de agregado tenía demasiados elementos y generaba un codegen erróneo para él. El siguiente código es un ejemplo de esto:

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {
        { 1, 2 },
        { 3, 4 }
    };
    return 0;
}
```

En la versión 15.7 de Visual Studio 2017, actualización 3 y posteriores, con el ejemplo anterior ahora se genera la advertencia C2078 `too many initializers`. En el siguiente ejemplo se muestra cómo reparar el código. Al inicializar un `std::array` con listas de inicialización de llaves anidadas, asigne a la matriz interna una lista de llaves propia:

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {{ // note double braces
        { 1, 2 },
        { 3, 4 }
    }}; // note double braces
    return 0;
}
```

## <a name="bug-fixes-and-behavior-changes-in-158"></a><a name="update_158"></a> Correcciones de errores y cambios de comportamiento en la versión 15.8

Los cambios del compilador en la versión 15.8 de Visual Studio 2017 son correcciones de errores y cambios de comportamiento. Se enumeran a continuación:

### <a name="typename-on-unqualified-identifiers"></a>**typename** en identificadores incompletos

En el modo [`/permissive-`](../build/reference/permissive-standards-conformance.md), el compilador ya no acepta las palabras clave **typename** falsas en los identificadores incompletos de las definiciones de plantilla de alias. El código siguiente ahora genera la advertencia C7511 `'T': 'typename' keyword must be followed by a qualified name`:

```cpp
template <typename T>
using  X = typename T;
```

Para corregir el error, cambie la segunda línea por `using  X = T;`.

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>`__declspec()` en el lado derecho de las definiciones de plantilla de alias

[__declspec](../cpp/declspec.md) ya no se permite en el lado derecho de una definición de plantilla de alias. Anteriormente, el compilador lo aceptaba pero omitió este código. Nunca produciría una advertencia de desuso cuando se usaba el alias.

En su lugar, se puede usar el atributo estándar de C++ [\[\[en desuso\]\]](../cpp/attributes.md), que se respeta a partir de la versión 15.6 de Visual Studio 2017. El código siguiente ahora genera la advertencia C2760 `syntax error: unexpected token '__declspec', expected 'type specifier'`:

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

Para corregir el error, cambie el código por lo siguiente (con el atributo colocado antes del signo "=" de la definición de alias):

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>Diagnóstico de búsqueda de nombres en dos fases

La búsqueda de nombres en dos fases requiere que los nombres no dependientes que se usan en los cuerpos de las plantillas sean visibles para la plantilla en el momento de la definición. Antes, el compilador de Microsoft C++ podía dejar un nombre no encontrado como no buscado hasta el momento de crear las instancias. Ahora, por el contrario, requiere que los nombres no dependientes estén enlazados en el cuerpo de la plantilla.

Una forma de manifestarse es con una búsqueda en las clases base dependientes. Anteriormente, el compilador permitía el uso de nombres que se definían en clases base dependientes. Esto se debe a que se buscaban en el momento de la creación de instancias cuando se resolvían todos los tipos. Ahora, ese código se trata como un error. En estos casos, puede forzar la búsqueda de la variable en el momento de crear las instancias. Para ello, puede certificarla con el tipo de clase base o convertirla en dependiente (por ejemplo, agregando un puntero `this->`).

En el modo [/permissive](../build/reference/permissive-standards-conformance.md), el código siguiente ahora genera la advertencia C3861 `'base_value': identifier not found`:

```cpp
template <class T>
struct Base {
    int base_value = 42;
};

template <class T>
struct S : Base<T> {
    int f() {
        return base_value;
    }
};
```

Para corregir el error, cambie la instrucción `return` por `return this->base_value;`.

**Nota:** En la biblioteca Boost Python, ha habido una solución alternativa específica para MSVC para una declaración adelantada de plantilla en [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp). En modo [`/permissive-`](../build/reference/permissive-standards-conformance.md) a partir de Visual Studio 2017 versión 15.8 (\_MSC\_VER = 1915), el compilador MSVC realiza correctamente la búsqueda de nombres dependientes de argumentos (ADL). Ahora es coherente con otros compiladores, por lo que esta protección de la solución alternativa no es necesaria. Para evitar el error C3861 `'unwind_type': identifier not found`, consulte [PR 229](https://github.com/boostorg/python/pull/229) en el repositorio Boost para actualizar el archivo de encabezado. Hemos revisado y corregido el paquete [vcpkg](../build/vcpkg.md) de Boost, por lo que si obtiene o actualiza los orígenes de Boost desde vcpkg, no necesita aplicar las revisiones por separado.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>Declaraciones y definiciones de reenvío en el espacio de nombres `std`

El estándar de C++ no permite a los usuarios agregar declaraciones o definiciones de reenvío en el espacio de nombres `std`. Ahora, si se agregan declaraciones o definiciones al espacio de nombres `std` o a un espacio de nombres situado dentro del espacio de nombres `std`, se produce un comportamiento indefinido.

Microsoft tiene previsto trasladar en algún momento la ubicación donde se definen ciertos tipos de biblioteca estándar. Este cambio interrumpirá el código existente que agrega declaraciones de reenvío al espacio de nombres `std`. Una nueva advertencia, C4643, permite identificar estos problemas de origen. La advertencia se habilita en el modo **`/default`** y está desactivada de forma predeterminada. Afectará a los programas que se compilen con **`/Wall`** o **`/WX`** .

El código siguiente ahora produce la advertencia C4643 `Forward declaring 'vector' in namespace std is not permitted by the C++ Standard`:

```cpp
namespace std {
    template<typename T> class vector;
}
```

Para corregir el error, use una directiva **include** en vez de una declaración de reenvío:

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>Constructores que se delegan a sí mismos

El estándar de C++ sugiere que un compilador debería emitir un diagnóstico cuando un constructor de delegación se delegue a sí mismo. El compilador de Microsoft C++ en los modos [/std:c++17](../build/reference/std-specify-language-standard-version.md) y [/std:c++latest](../build/reference/std-specify-language-standard-version.md) ahora produce la advertencia C7535 `'X::X': delegating constructor calls itself`.

Sin este error, el programa siguiente se compilará, pero generará un bucle infinito:

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

Para evitar el bucle infinito, deléguelo a otro constructor:

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>`offsetof` con expresiones constantes

[offsetof](../c-runtime-library/reference/offsetof-macro.md) tradicionalmente se ha implementado con una macro que requiere un [reinterpret_cast](../cpp/reinterpret-cast-operator.md). Este uso no es válido en los contextos que requieran una expresión constante, pero el compilador de Microsoft C++ tradicionalmente lo ha permitido. La macro `offsetof` que se distribuye como parte de la biblioteca estándar usa correctamente una función intrínseca del compilador ( **__builtin_offsetof**), pero muchas personas han empleado el truco de la macro para definir su propio `offsetof`.

En la versión 15.8 de Visual Studio 2017, el compilador restringe las áreas en las que pueden aparecer estos operadores `reinterpret_cast` en el modo predeterminado para ayudar a que el código pueda ajustarse al comportamiento estándar de C++. En el modo [/permissive-](../build/reference/permissive-standards-conformance.md), las restricciones son aún más estrictas. El uso del resultado de `offsetof` en lugares que requieren expresiones constantes puede producir código que emite la advertencia C4644 `usage of the macro-based offsetof pattern in constant expressions is non-standard; use offsetof defined in the C++ standard library instead` o C2975 `invalid template argument, expected compile-time constant expression`.

El código siguiente genera la advertencia C4644 en los modos **`/default`** y **`/std:c++17`** , y una advertencia C2975 en el modo [/permissive](../build/reference/permissive-standards-conformance.md):

```cpp
struct Data {
    int x;
};

// Common pattern of user-defined offsetof
#define MY_OFFSET(T, m) (unsigned long long)(&(((T*)nullptr)->m))

int main()

{
    switch (0) {
    case MY_OFFSET(Data, x): return 0;
    default: return 1;
    }
}
```

Para corregir el error, use `offsetof` tal y como se define mediante \<cstddef>:

```cpp
#include <cstddef>

struct Data {
    int x;
};

int main()
{
    switch (0) {
    case offsetof(Data, x): return 0;
    default: return 1;
    }
}
```

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>Calificadores cv en las clases base sujetas a la expansión de paquete

Las versiones anteriores del compilador de Microsoft C++ no detectaban que una clase base tenía calificadores cv si esta también estaba sujeta a una expansión de paquete.

En la versión 15.8 de Visual Studio 2017, en el modo [/permissive-](../build/reference/permissive-standards-conformance.md), el código siguiente genera la advertencia C3770 `'const S': is not a valid base class`:

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>Palabra clave **template** y nested-name-specifiers

En el modo [/permissive-](../build/reference/permissive-standards-conformance.md), el compilador ahora requiere que la palabra clave **template** preceda a un template-name si va después de un nested-name-specifier dependiente.

El siguiente código del modo [/permissive](../build/reference/permissive-standards-conformance.md)ahora genera la advertencia C7510 `'example': use of dependent template name must be prefixed with 'template'. note: see reference to class template instantiation 'X<T>' being compiled`:

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        Base<T>::example<int>();
    }
};
```

Para corregir el error, agregue la palabra clave **template** a la instrucción `Base<T>::example<int>();`, como se muestra en el ejemplo siguiente:

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        // Add template keyword here:
        Base<T>::template example<int>();
    }
};
```

## <a name="bug-fixes-and-behavior-changes-in-159"></a><a name="update_159"></a> Correcciones de errores y cambios de comportamiento en la versión 15.9

### <a name="identifiers-in-member-alias-templates"></a>Identificadores en las plantillas de alias de miembro

Un identificador utilizado en una definición de plantilla de alias de miembro debe declararse antes de su uso.

En versiones anteriores del compilador, se permitía el código siguiente:

```cpp
template <typename... Ts>
struct A
{
  public:
    template <typename U>
    using from_template_t = decltype(from_template(A<U>{}));

  private:
    template <template <typename...> typename Type, typename... Args>
    static constexpr A<Args...> from_template(A<Type<Args...>>);
};

A<>::from_template_t<A<int>> a;
```

En la versión 15.9 de Visual Studio 2017, en el modo [`/permissive-`](../build/reference/permissive-standards-conformance.md), el compilador genera la advertencia C3861 `'from_template': identifier not found`.

Para corregir el error, declare `from_template` antes de `from_template_t`.

### <a name="modules-changes"></a>Cambios de módulos

En Visual Studio 2017, versión 15.9, el compilador genera la advertencia C5050 cuando las opciones de la línea de comandos para los módulos no son coherentes entre el lado de creación del módulo y el de consumo del módulo. En el ejemplo siguiente, hay dos problemas:

- En el consumo (main.cpp), la opción **`/EHsc`** no se ha especificado.

- La versión de C++ es **`/std:c++17`** en la creación y **`/std:c++14`** en el consumo.

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Para ambos casos, el compilador genera la advertencia C5050 `warning C5050: Possible incompatible environment while importing module 'm': mismatched C++ versions.  Current "201402" module version "201703"`.

El compilador también genera la advertencia C7536 cada vez que se modifica el archivo .ifc. El encabezado de la interfaz del módulo contiene un hash SHA2 del contenido debajo de él. En la importación, se aplica hash al archivo .ifc y luego se compara con el hash proporcionado en el encabezado. Si no coinciden, se produce el error C7536 `ifc failed integrity checks.  Expected SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'`.

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Ordenación parcial que incluye alias y contextos no deducidos

Las implementaciones divergen en la aplicación de las reglas de ordenación parcial que afectan a los alias en contextos no deducidos. En el ejemplo siguiente, GCC y el compilador de Microsoft C++ (en modo [`/permissive-`](../build/reference/permissive-standards-conformance.md)) producirán un error, mientras que Clang acepta el código.

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <class T, class Alloc>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

El ejemplo anterior genera la advertencia C2668:

```Output
partial_alias.cpp(32): error C2668: 'f': ambiguous call to overloaded function
partial_alias.cpp(18): note: could be 'int f<Alloc,void>(A<void> &,const AlignedBuffer<10,4> &)'
partial_alias.cpp(12): note: or       'int f<Alloc,A<void>>(Alloc &,const AlignedBuffer<10,4> &)'
        with
        [
            Alloc=A<void>
        ]
partial_alias.cpp(32): note: while trying to match the argument list '(A<void>, AlignedBuffer<10,4>)'
```

La divergencia de implementación se debe a una regresión en la redacción estándar de C++. La resolución al problema central 2235 quitó algún texto que permitiría ordenar estas sobrecargas. El actual estándar C++ no proporciona un mecanismo para ordenar parcialmente estas funciones, por lo que se consideran ambiguas.

Como solución alternativa, le recomendamos que no confíe en la ordenación parcial para resolver este problema. En su lugar, utilice SFINAE para quitar las sobrecargas particulares. En el ejemplo siguiente, se utiliza una clase auxiliar `IsA` para quitar la primera sobrecarga cuando `Alloc` es una especialización de `A`:

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <typename T> struct IsA : std::false_type {};
template <typename T> struct IsA<A<T>> : std::true_type {};

template <class T, class Alloc, typename = std::enable_if_t<!IsA<Alloc>::value>>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>Expresiones no válidas y tipos no literales en las definiciones de funciones basadas en un modelo

Las expresiones no válidas y los tipos no literales ahora se diagnostican correctamente en las definiciones de funciones basadas en un modelo que son especializadas de forma explícita. Antes, no se emitían estos errores para la definición de función. Aun así, la expresión no válida o el tipo no literal se diagnosticaban igualmente si se evaluaban como parte de una expresión constante.

En versiones anteriores de Visual Studio, el código siguiente se compilaba sin advertencias:

```cpp
void g();

template<typename T>
struct S
{
    constexpr void f();
};

template<>
constexpr void S<int>::f()
{
    g(); // C3615 in 15.9
}
```

En la versión 15.9 de Visual Studio 2017, el código siguiente genera este error:

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

Para evitar el error, quite el calificador **constexpr** de la creación de instancia explícita de la función `f()`.

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>Mejoras de conformidad de C++ en Visual Studio 2015

Tenemos una lista completa de las mejoras de conformidad hasta Visual Studio 2015 Update 3. Para obtener más información, consulte [Visual C++ What's New 2003 through 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015) (Novedades de Visual C++ desde 2003 hasta 2015).

::: moniker-end

## <a name="see-also"></a>Vea también

[Tabla de conformidad del lenguaje Microsoft C++](../visual-cpp-language-conformance.md)
