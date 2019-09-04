---
title: '/experimental: preprocesador (habilitar el modo de cumplimiento del preprocesador)'
description: 'Use la opción del compilador/experimental: preprocesador para habilitar la compatibilidad experimental del compilador para un preprocesador compatible con el estándar.'
ms.date: 09/03/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 3055cfa2a32d1d668dbe0c51b5542415b5bb0af4
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294442"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/experimental: preprocesador (habilitar el modo de cumplimiento del preprocesador)

Esta opción habilita un preprocesador experimental basado en tokens que se ajusta a los estándares de C++ 11, incluidas las características del preprocesador de C99.

## <a name="syntax"></a>Sintaxis

> **/experimental: preprocesador** [ **-** ]

## <a name="remarks"></a>Comentarios

Use la opción del compilador **/experimental: preprocesador** para habilitar el preprocesador compatible con experimental. Puede usar **/experimental: preprocesser-** Option para especificar explícitamente el preprocesador tradicional.

La opción **/experimental: preprocesador** está disponible a partir de la versión 15,8 de Visual Studio 2017.

Puede detectar qué preprocesador está en uso en tiempo de compilación. Compruebe el valor de la macro [ \_predefinida MSVC\_tradicional](../../preprocessor/predefined-macros.md) para saber si el preprocesador tradicional está en uso. Esta macro se establece incondicionalmente en las versiones del compilador que lo admiten, independientemente del preprocesador que se invoque. Su valor es 1 para el preprocesador tradicional. Es 0 para el preprocesador experimental correcto:

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

### <a name="behavior-changes-in-the-experimental-preprocessor"></a>Cambios de comportamiento en el preprocesador experimental

Estos son algunos de los cambios importantes más comunes que se encuentran cuando se habilita el modo de cumplimiento del preprocesador:

#### <a name="macro-comments"></a>Comentarios de macro

El preprocesador tradicional utiliza búferes de caracteres en lugar de tokens de preprocesador. Esto permite cierto comportamiento inusual, como este truco de comentario del preprocesador, que no funciona en el preprocesador que cumple los siguientes pasos:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
// To make standards compliant, wrap the following line with the appropriate #if/#endif
DISAPPEARING_TYPE myVal;
```

#### <a name="string-prefixes-lval"></a>Prefijos de cadena (L # Val)

El preprocesador tradicional combina incorrectamente un prefijo de cadena con el resultado del [operador de cadena (#)](../../preprocessor/stringizing-operator-hash.md):

```cpp
#define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

El `L` prefijo no es necesario aquí, porque los literales de cadena adyacentes se combinan después de la expansión de la macro de todos modos. La corrección compatible con versiones anteriores es cambiar la definición a:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Este problema también se encuentra en prácticas macros que "cadena" el argumento a un literal de cadena ancho:

```cpp
// The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str

// Potential fixes:
// Use string concatenation of L"" and #str to add prefix
// This works because adjacent string literals are combined after macro expansion
#define STRING1(str) L""#str

// Add the prefix after #str is stringized with additional macro expansion
#define WIDE(str) L##str
#define STRING2(str) WIDE(#str)

// Use concatenation operator ## to combine the tokens.
// The order of operations for ## and # is unspecified, although all compilers
// checked perform the # operator before ## in this case.
#define STRING3(str) L## #str
```

#### <a name="warning-on-invalid"></a>ADVERTENCIA de no válida ##

Cuando el [operador de pegado de token (# #)](../../preprocessor/token-pasting-operator-hash-hash.md) no da como resultado un único token de preprocesamiento válido, el comportamiento es indefinido. El preprocesador tradicional no puede combinar los tokens de forma silenciosa. El nuevo preprocesador coincide con el comportamiento de la mayoría de los compiladores y emite un diagnóstico.

```cpp
// The ## is unnecessary and doesn't result in a single preprocessing token.
#define ADD_STD(x) std::##x

// Declare a std::string
ADD_STD(string) s;
```

#### <a name="comma-elision-in-variadic-macros"></a>Elisión de comas en macros variádicas

Considere el ejemplo siguiente:

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // The following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the following macro with:
    // func(1, );
    // which results in a syntax error.
    FUNC(1, );
}
```

Todos los compiladores principales tienen una extensión de preprocesador que ayuda a solucionar este problema. El preprocesador MSVC tradicional siempre quita las comas antes de `__VA_ARGS__` los reemplazos vacíos. El preprocesador actualizado sigue mejor el comportamiento de otros compiladores multiplataforma populares. En el caso de la coma que se va a quitar, el argumento variádicas debe estar ausente, no solo vacío, y debe `##` marcarse con un operador:

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
    // The variadic argument is missing in the macro being evoked
    // The comma is removed and replaced with:
    // func(1)
    FUNC2(1);

    // The variadic argument is empty, but not missing. (Notice the
    // comma in the argument list.) The comma isn't removed
    // when the macro is replaced:
    // func(1, )
    FUNC2(1, );
}
```

En el próximo estándar de C + + 2A, este problema se ha solucionado `__VA_OPT__`agregando, que aún no se ha implementado.

#### <a name="macro-arguments-are-unpacked"></a>Los argumentos de macro están desempaquetados

En el preprocesador tradicional, si una macro reenvía uno de sus argumentos a otra macro dependiente, el argumento no se "desempaquetará" cuando se reemplace. Normalmente, esta optimización se queda sin aviso, pero puede dar lugar a un comportamiento inusual:

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

Al expandir `A()`, el preprocesador tradicional reenvía todos los argumentos empaquetados en `__VA_ARGS__` el primer argumento de `TWO_STRINGS`. El argumento variádicas de `TWO_STRINGS` está vacío, lo que hace que el `#first` resultado de `"1, 2"` sea en lugar `"1"`de simplemente. Es posible que se pregunte qué sucedió con el resultado `#__VA_ARGS__` de en la expansión del preprocesador tradicional. Si el parámetro variádicas está vacío, debe tener como resultado un literal de cadena vacío "". Debido a un problema independiente, no se generó el token literal de cadena vacío.

#### <a name="rescanning-replacement-list-for-macros"></a>Volver a examinar la lista de reemplazo para macros

Una vez reemplazada una macro, los tokens resultantes se vuelven a examinar para buscar los identificadores de macro adicionales que se van a reemplazar. El algoritmo de volver a examinar utilizado por el preprocesador tradicional no es compatible, como se muestra en este ejemplo en función del código real:

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

Para ver lo que está ocurriendo en este ejemplo, desglosamos la expansión a partir de `DO_THING`:

`DO_THING(1, "World")` ->
`CAT(IMPL, 1) ECHO(("Hello", "World"))`

En segundo lugar, CAT se expande:

`CAT(IMPL, 1)` -> `IMPL ## 1` -> `IMPL1`

Que coloca los tokens en este estado:

`IMPL1 ECHO(("Hello", "World"))`

El preprocesador busca el identificador `IMPL1`de la macro similar a la función, pero no va seguido de un "(", por lo que no se considera una invocación de macro similar a una función. Pasa a los tokens siguientes y busca la macro `ECHO` a la que se ha invocado la función:

`ECHO(("Hello", "World"))` -> `("Hello", "World")`

`IMPL1`nunca se considera de nuevo para la expansión, por lo que el resultado completo de las expansiones es:

`IMPL1("Hello", "World");`

La macro se puede modificar para que se comporte de la misma manera en el preprocesador experimental y el preprocesador tradicional. La solución consiste en agregar otra capa de direccionamiento indirecto:

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__

// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))

DO_THING_FIXED(1, "World");
// macro expanded to:
// do_thing_one( "Hello", "World");
```

### <a name="conformance-mode-conformance"></a>Conformidad del modo de cumplimiento

Todavía no se ha completado el preprocesador experimental y la lógica de la Directiva de preprocesador sigue recurre al comportamiento tradicional. Esta es una lista parcial de características incompletas:

- Compatibilidad con`_Pragma`
- Características de c++ 20
- Mejoras adicionales de diagnóstico
- Cambia para controlar la salida en/E y/P.
- Error al bloquear el bloqueo: Los operadores lógicos en expresiones de constantes de preprocesador no están totalmente implementados en el nuevo preprocesador. En algunas `#if` directivas, el nuevo preprocesador puede revertir al preprocesador tradicional. El efecto solo es evidente cuando se expanden las macros que no son compatibles con el preprocesador tradicional, lo que puede ocurrir al crear ranuras de preprocesador de Boost.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C/C++**  > **Línea de comandos**.

1. Modifique la propiedad **opciones adicionales** para incluir **/experimental: preprocesador** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](zc-conformance.md)
