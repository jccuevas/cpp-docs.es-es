---
title: Visión general del preprocesador experimental MSVC
description: El preprocesador MSVC se está actualizando para cumplir con los estándares C/C++.
ms.date: 02/09/2020
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 00c34ef75270e505d3781cf7eedf4d8aba95ee6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337485"
---
# <a name="msvc-experimental-preprocessor-overview"></a>Visión general del preprocesador experimental MSVC

::: moniker range="vs-2015"

Visual Studio 2015 usa el preprocesador tradicional, que no se ajusta a Standard C++. Un preprocesador experimental está disponible en Visual Studio 2017 y Visual Studio 2019 mediante el modificador del compilador [/experimental:preprocessor.](../build/reference/experimental-preprocessor.md) Para obtener más información sobre el uso del nuevo preprocesador en Visual Studio 2017 y Visual Studio 2019. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end

::: moniker range=">=vs-2017"

Estamos actualizando el preprocesador de Microsoft C++ para mejorar la conformidad de los estándares, corregir errores de larga data y cambiar algunos comportamientos que están oficialmente indefinidos. También hemos añadido nuevos diagnósticos para advertir sobre errores en las definiciones de macros.

Estos cambios están disponibles mediante el modificador del compilador [/experimental:preprocessor](../build/reference/experimental-preprocessor.md) en Visual Studio 2017 o Visual Studio 2019. El comportamiento predeterminado del preprocesador sigue siendo el mismo que en versiones anteriores.

A partir de Visual Studio 2019 versión 16.5, la compatibilidad con preprocesador experimental para el estándar C++20 es un complemento de características.

## <a name="new-predefined-macro"></a>Nueva macro predefinida

Puede detectar qué preprocesador está en uso en tiempo de compilación. Compruebe el valor de [ \_\_](predefined-macros.md) la macro predefinida MSVC TRADITIONAL para saber si el preprocesador tradicional está en uso. Esta macro se establece incondicionalmente por versiones del compilador que la admiten, independientemente del preprocesador que se invoque. Su valor es 1 para el preprocesador tradicional. Es 0 para el preprocesador conforme.

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Cambios de comportamiento en el preprocesador experimental

El trabajo inicial sobre el preprocesador experimental se ha centrado en hacer que todas las expansiones de macros se ajusten al estándar. Le permite usar el compilador MSVC con bibliotecas que actualmente están bloqueadas por los comportamientos tradicionales. Probamos el preprocesador actualizado en proyectos del mundo real. Estos son algunos de los cambios de última hora más comunes que encontramos:

### <a name="macro-comments"></a>Comentarios macro

El preprocesador tradicional se basa en búferes de caracteres en lugar de tokens de preprocesador. Permite un comportamiento inusual, como el siguiente truco de comentarios de preprocesador, que no funciona bajo el preprocesador conforme:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

La solución conforme a `int myVal` las normas `#ifdef/#endif` consiste en declarar dentro de las directivas apropiadas:

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L'val

El preprocesador tradicional combina incorrectamente un prefijo de cadena con el resultado del operador de [encadenamiento:](stringizing-operator-hash.md)

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

En este caso, el `L` prefijo es innecesario porque los literales de cadena adyacentes se combinan después de la expansión de macros de todos modos. La corrección compatible con versiones anteriores es cambiar la definición:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

El mismo problema también se encuentra en las macros de conveniencia que "stringizan" el argumento a un literal de cadena amplia:

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

Puede solucionar el problema de varias maneras:

- Utilice la concatenación de cadenas de `L""` y `#str` para agregar el prefijo. Los literales de cadena adyacentes se combinan después de la expansión de macros:

   ```cpp
   #define STRING1(str) L""#str
   ```

- Agregue el `#str` prefijo after is stringized con expansión de macro adicional

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Utilice el operador `##` de concatenación para combinar los tokens. El orden de `##` `#` las operaciones y no está especificado, `#` aunque `##` todos los compiladores parecen evaluar el operador antes en este caso.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Advertencia sobre inválidos\#\#

Cuando el operador de pegado de [tokens (-)](token-pasting-operator-hash-hash.md) no da como resultado un único token de preprocesamiento válido, el comportamiento es indefinido. El preprocesador tradicional no puede combinar los tokens de forma silenciosa. El nuevo preprocesador coincide con el comportamiento de la mayoría de los demás compiladores y emite un diagnóstico.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Elision de coma en macros variádicas

El preprocesador MSVC tradicional siempre elimina `__VA_ARGS__` comas antes de reemplazos vacíos. El preprocesador experimental sigue más de cerca el comportamiento de otros compiladores multiplataforma populares. Para quitar la coma, el argumento variadic debe faltar (no solo `##` vacío) y debe marcarse con un operador. Considere el ejemplo siguiente:

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the
    // following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the
    // following macro with: func(1, ), which
    // results in a syntax error.
    FUNC(1, );
}
```

En el ejemplo siguiente, `FUNC2(1)` en la llamada al argumento variadic falta en la macro que se está invocando. En la `FUNC2(1, )` llamada al argumento variadic está vacío, pero no falta (observe la coma en la lista de argumentos).

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
   // Expands to func(1)
   FUNC2(1);

   // Expands to func(1, )
   FUNC2(1, );
}
```

En el próximo estándar C++20, este problema `__VA_OPT__`se ha solucionado agregando . La compatibilidad con `__VA_OPT__` preprocesador experimental está disponible a partir de Visual Studio 2019 versión 16.5.

### <a name="c20-variadic-macro-extension"></a>C++20 extensión de macro variádica

El preprocesador experimental admite la elision de argumentos de macro variádico C++20:

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

Este código no se ajusta antes del estándar C++20. En MSVC, el preprocesador experimental extiende este comportamiento C++20 a modos estándar de idioma inferior (**`/std:c++14`**, **`/std:c++17`**). Esta extensión coincide con el comportamiento de otros compiladores C++ multiplataforma principales.

### <a name="macro-arguments-are-unpacked"></a>Los argumentos macro son "desempaquetados"

En el preprocesador tradicional, si una macro reenvía uno de sus argumentos a otra macro dependiente, el argumento no se "desempaqueta" cuando se inserta. Por lo general, esta optimización pasa desapercibida, pero puede conducir a un comportamiento inusual:

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conforming preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

Al expandir `A()`, el preprocesador tradicional reenvía todos `__VA_ARGS__` los argumentos empaquetados al primer argumento `TWO_STRINGS` de TWO_STRINGS, que deja vacío el argumento variádico. Eso hace que `#first` el resultado sea "1, 2" en lugar de simplemente "1". Si está siguiendo de cerca, es posible que se `#__VA_ARGS__` pregunte qué pasó con el resultado de la expansión del preprocesador tradicional: si el parámetro varisódico está vacío, debería dar lugar a un literal `""`de cadena vacío. Un problema independiente impidió que se generara el token literal de cadena vacío.

### <a name="rescanning-replacement-list-for-macros"></a>Reescaneo de la lista de reemplazo para macros

Después de reemplazar una macro, los tokens resultantes se vuelven a examinar en busca de identificadores de macro adicionales que se van a reemplazar. El algoritmo utilizado por el preprocesador tradicional para realizar el reescaneo no es conforme, como se muestra en este ejemplo basado en el código real:

```cpp
#define CAT(a,b) a ## b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

// MACRO chooses the expansion behavior based on the value passed to macro_switch
#define DO_THING(macro_switch, b) CAT(IMPL, macro_switch) ECHO(( "Hello", b))
DO_THING(1, "World");

// Traditional preprocessor:
// do_thing_one( "Hello", "World");
// Conforming preprocessor:
// IMPL1 ( "Hello","World");
```

Aunque este ejemplo puede parecer un poco inventado, lo hemos visto en el código del mundo real. Para ver lo que está pasando, podemos desglosar la expansión a partir `DO_THING`de:

1. `DO_THING(1, "World")`se expande a`CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)`se expande a `IMPL ## 1`, que se expande a , que se expande a`IMPL1`
1. Ahora los tokens están en este estado:`IMPL1 ECHO(("Hello", "World"))`
1. El preprocesador busca el identificador `IMPL1`de macro de tipo función. Dado que no va `(`seguido de una , no se considera una invocación de macro similar a una función.
1. El preprocesador pasa a los siguientes tokens. Encuentra que la macro `ECHO` de tipo `ECHO(("Hello", "World"))`función se invoca: , que se expande a`("Hello", "World")`
1. `IMPL1`nunca se considera de nuevo para la expansión, por lo que el resultado completo de las expansiones es:`IMPL1("Hello", "World");`

Para modificar la macro para que se comporte de la misma manera tanto en el preprocesador experimental como en el preprocesador tradicional, agregue otra capa de direccionamiento indirecto:

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)
#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))
DO_THING_FIXED(1, "World");

// macro expands to:
// do_thing_one( "Hello", "World");
```

## <a name="incomplete-features"></a>Características incompletas

A partir de Visual Studio 2019 versión 16.5, el preprocesador experimental está completo para C++20. En versiones anteriores de Visual Studio, el preprocesador experimental es principalmente completo, aunque algunalógica de directiva de preprocesador todavía vuelve al comportamiento tradicional. Esta es una lista parcial de características incompletas en las versiones de Visual Studio anteriores a 16.5:

- Compatibilidad con `_Pragma`
- Características de C++20
- Aumentar el error de bloqueo: los operadores lógicos de expresiones constantes de preprocesador no se implementan completamente en el nuevo preprocesador antes de la versión 16.5. En `#if` algunas directivas, el nuevo preprocesador puede volver al preprocesador tradicional. El efecto sólo se nota cuando las macros incompatibles con el preprocesador tradicional se expanden. Puede suceder al crear ranuras de preprocesador Boost.

::: moniker-end
