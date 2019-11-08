---
title: Información general del preprocesador experimental de MSVC
description: El preprocesador MSVC se está actualizando para cumplir con los estándares C/C++ .
ms.date: 11/06/2019
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 446603b34d9309c256afba9abd7234ae2ab16f5c
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73797191"
---
# <a name="msvc-experimental-preprocessor-overview"></a>Información general del preprocesador experimental de MSVC

El preprocesador de Microsoft C++ se está actualizando para mejorar la conformidad con los estándares, corregir los errores que faltan y cambiar algunos comportamientos que están oficialmente indefinidos. Además, se han agregado nuevos diagnósticos para advertir sobre errores en las definiciones de macro.

Estos cambios en su estado actual están disponibles mediante el modificador de compilador [/experimental: preprocesador](../build/reference/experimental-preprocessor.md) en visual Studio 2017 o visual Studio 2019. El comportamiento predeterminado del preprocesador sigue siendo el mismo que en las versiones anteriores.

## <a name="new-predefined-macro"></a>Nueva macro predefinida

Puede detectar qué preprocesador está en uso en tiempo de compilación. Compruebe el valor de la macro predefinida [\_MSVC\_tradicional](predefined-macros.md) para saber si el preprocesador tradicional está en uso. Esta macro se establece incondicionalmente en las versiones del compilador que lo admiten, independientemente del preprocesador que se invoque. Su valor es 1 para el preprocesador tradicional. Es 0 para el preprocesador experimental correcto:

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Cambios de comportamiento en el preprocesador experimental

El trabajo inicial del preprocesador experimental se ha centrado en hacer que todas las expansiones de macros sean compatibles con el fin de permitir el uso del compilador MSVC con bibliotecas que están bloqueadas actualmente debido a comportamientos tradicionales. A continuación se muestra una lista de algunos de los cambios importantes más comunes que se ejecutaron al probar el preprocesador actualizado con proyectos reales.

### <a name="macro-comments"></a>Comentarios de macro

El preprocesador tradicional se basa en los búferes de caracteres en lugar de en los tokens de preprocesador. Esto permite un comportamiento inusual, como el siguiente truco de comentario del preprocesador, que no funcionará en el preprocesador compatible:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

La corrección compatible con los estándares es declarar `int myVal` dentro de las directivas de `#ifdef/#endif` apropiadas:

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L # Val

El preprocesador tradicional combina incorrectamente un prefijo de cadena con el resultado del operador de [cadenas (#)](stringizing-operator-hash.md) :

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

En este caso, el prefijo `L` no es necesario porque los literales de cadena adyacentes se combinan después de la expansión de la macro de todos modos. La corrección compatible con versiones anteriores es cambiar la definición por lo siguiente:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

El mismo problema también se encuentra en macros de conveniencia que "cadena" el argumento a un literal de cadena ancho:

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

Puede corregir el problema de varias maneras:

- Utilice la concatenación de cadenas de `L""` y `#str` para agregar el prefijo. Esto funciona porque los literales de cadena adyacentes se combinan después de la expansión de macro:

   ```cpp
   #define STRING1(str) L""#str
   ```

- Agregar el prefijo después de que `#str` se cadena con expansión de macro adicional

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Use el operador de concatenación `##` para combinar los tokens. El orden de las operaciones de `##` y `#` no se especifica, aunque todos los compiladores parecen evaluar el operador de `#` antes de `##` en este caso.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>ADVERTENCIA en un \#no válido \#

Cuando el [operador de pegado de token (# #)](token-pasting-operator-hash-hash.md) no da como resultado un único token de preprocesamiento válido, el comportamiento es indefinido. El preprocesador tradicional no podrá combinar los tokens de forma silenciosa. El nuevo preprocesador coincidirá con el comportamiento de la mayoría de los compiladores y emitirá un diagnóstico.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Elisión de comas en macros variádicas

El preprocesador MSVC tradicional siempre quita las comas antes de que los reemplazos `__VA_ARGS__` vacíos. El preprocesador experimental sigue mejor el comportamiento de otros compiladores multiplataforma populares. En el caso de la coma que se va a quitar, el argumento variádicas debe estar ausente (no solo vacío) y debe marcarse con un operador `##`. Considere el ejemplo siguiente:

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor will replace the following macro with: func(1, ), which will result in a syntax error.
    FUNC(1, );
}
```

En el ejemplo siguiente, en la llamada a `FUNC2(1)` falta el argumento variádicas en la macro que se va a provocar. En la llamada a `FUNC2(1, )` el argumento variádicas está vacío, pero no falta (observe la coma en la lista de argumentos).

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

En el próximo estándar de C + + 2A, este problema se ha solucionado agregando `__VA_OPT__`, que aún no se ha implementado.

### <a name="macro-arguments-are-unpacked"></a>Los argumentos de macro están "desempaquetados"

En el preprocesador tradicional, si una macro reenvía uno de sus argumentos a otra macro dependiente, el argumento no se "desempaquetará" cuando se sustituya. Normalmente, esta optimización se queda sin aviso, pero puede dar lugar a un comportamiento inusual:

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conformant preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

Al expandir `A()`, el preprocesador tradicional reenvía todos los argumentos empaquetados en `__VA_ARGS__` al primer argumento de TWO_STRINGS, que deja el argumento variádicas de `TWO_STRINGS` vacío. Esto hace que el resultado de `#first` sea "1,2" en lugar de solo "1". Si está siguiendo en estrecha profundidad, es posible que se pregunte qué sucedió con el resultado de `#__VA_ARGS__` en la expansión del preprocesador tradicional: Si el parámetro variádicas está vacío, debe tener como resultado un literal de cadena vacío `""`. Debido a un problema independiente, no se generó el token literal de cadena vacío.

### <a name="rescanning-replacement-list-for-macros"></a>Volver a examinar la lista de reemplazo para macros

Una vez reemplazada una macro, se vuelven a examinar los tokens resultantes para buscar otros identificadores de macro que deban reemplazarse. El algoritmo utilizado por el preprocesador tradicional para realizar el nuevo examen no es compatible, como se muestra en este ejemplo en función del código real:

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
// Conformant preprocessor:
// IMPL1 ( "Hello","World");
```

Aunque este ejemplo parece un poco inventado, se ha detectado que se ha producido el código del mundo real. Para ver lo que está ocurriendo, podemos desglosar la expansión a partir de `DO_THING`:

1. `DO_THING(1, "World")` se expande a `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` se expande a `IMPL ## 1` que se expande a `IMPL1`
1. Ahora los tokens están en este estado: `IMPL1 ECHO(("Hello", "World"))`
1. El preprocesador busca el identificador de macro como `IMPL1`, pero no va seguido de un `(`, por lo que no se considera una invocación de macro como una función. 
1. Pasa a los tokens siguientes y busca la macro similar a la función `ECHO` que se invoca: `ECHO(("Hello", "World"))`, que se expande a `("Hello", "World")`
1. `IMPL1` nunca se considera de nuevo para la expansión, por lo que el resultado completo de las expansiones es: `IMPL1("Hello", "World");`

La macro se puede modificar para que se comporte de la misma manera en el preprocesador experimental y el preprocesador tradicional agregando otro nivel de direccionamiento indirecto:

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

El preprocesador experimental está totalmente completo, aunque algunas lógicas de la Directiva de preprocesador todavía recurren al comportamiento tradicional. Esta es una lista parcial de características incompletas:

- Compatibilidad con `_Pragma`
- Características de c++ 20
- Aumentar el error de bloqueo: los operadores lógicos en expresiones de constantes de preprocesador no están totalmente implementados en el nuevo preprocesador. En algunas directivas de `#if`, el nuevo preprocesador puede revertir al preprocesador tradicional. El efecto solo es evidente cuando se expanden las macros que no son compatibles con el preprocesador tradicional, lo que puede ocurrir al crear ranuras de preprocesador de Boost.
