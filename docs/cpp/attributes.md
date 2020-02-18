---
title: Atributos deC++
ms.date: 05/06/2019
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: b3ed21b033c0e606d02d3aa845f09f72118a3c5e
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416075"
---
# <a name="attributes-in-c"></a>Atributos deC++

El C++ estándar define un conjunto de atributos y también permite a los proveedores de compiladores definir sus propios atributos (dentro de un espacio de nombres específico del proveedor), pero los compiladores son necesarios para reconocer solo los atributos definidos en el estándar.

En algunos casos, los atributos estándar se superponen con los parámetros declspec específicos del compilador. En Visual C++, puede usar el atributo `[[deprecated]]` en lugar de usar `declspec(deprecated)` y el atributo será reconocido por cualquier compilador compatible. En el caso de todos los demás parámetros declspec como dllimport y dllexport, todavía no hay ningún atributo equivalente, por lo que debe seguir usando la sintaxis declspec. Los atributos no afectan al sistema de tipos y no cambian el significado de un programa. Los compiladores omiten los valores de atributo que no reconocen.

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): en el ámbito de una lista de atributos, puede especificar el espacio de nombres para todos los nombres con un único **mediante** el presentador:

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C++Atributos estándar

En C++ 11, los atributos proporcionan una manera estandarizada de C++ anotar construcciones (incluidas, entre otras, las clases, las funciones, las variables y los bloques) con información adicional que puede ser o no específica del proveedor. Un compilador puede utilizar esta información para generar mensajes informativos o para aplicar lógica especial al compilar el código con atributos. El compilador omite cualquier atributo que no reconozca, lo que significa que no puede definir sus propios atributos personalizados mediante esta sintaxis. Los atributos se incluyen entre corchetes dobles:

```cpp
[[deprecated]]
void Foo(int);
```

Los atributos representan una alternativa normalizada a las extensiones específicas del proveedor, como las directivas de #pragma, C++__declspec () &#95; &#95;(&#95; &#95; visual) o el atributo (GNU). Sin embargo, todavía necesitará usar las construcciones específicas del proveedor para la mayoría de los propósitos. El estándar especifica actualmente los siguientes atributos que debe reconocer un compilador compatible:

- `[[noreturn]]` especifica que una función no devuelve nunca; en otras palabras, siempre produce una excepción. El compilador puede ajustar sus reglas de compilación para entidades `[[noreturn]]`.

- `[[carries_dependency]]` especifica que la función propaga la ordenación de las dependencias de datos con respecto a la sincronización de subprocesos. El atributo se puede aplicar a uno o varios parámetros, para especificar que el argumento pasado incluye una dependencia en el cuerpo de la función. El atributo se puede aplicar a la propia función, para especificar que el valor devuelto incluye una dependencia de la función. El compilador puede utilizar esta información para generar código más eficaz.

- `[[deprecated]]` **Visual Studio 2015 y versiones posteriores:** especifica que una función no está diseñada para utilizarse y puede que no exista en versiones futuras de una interfaz de biblioteca. El compilador puede utilizar esto para generar un mensaje informativo cuando el código de cliente intenta llamar a la función. Se puede aplicar a la declaración de una clase, un nombre de TypeDef, una variable, un miembro de datos no estático, una función, un espacio de nombres, una enumeración, un enumerador o una especialización de plantilla.

- `[[fallthrough]]` **Visual Studio 2017 y versiones posteriores:** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)) el atributo de `[[fallthrough]]` se puede usar en el contexto de las instrucciones [Switch](switch-statement-cpp.md) como una sugerencia para el compilador (o cualquier persona que lea el código) para el que está previsto el comportamiento de fallthrough. Actualmente, C++ el compilador de Microsoft no advierte del comportamiento de fallthrough, por lo que este atributo no tiene ningún efecto en el comportamiento del compilador.

- `[[nodiscard]]` **Visual Studio 2017 versión 15,3 y versiones posteriores:** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)) especifica que el valor devuelto de una función no está diseñado para descartarse. Genera una advertencia C4834, como se muestra en este ejemplo:

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]` **Visual Studio 2017 versión 15,3 y posterior:** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)) especifica que no se puede usar intencionadamente una variable, función, clase, TypeDef, miembro de datos no estático, enumeración o especialización de plantilla. El compilador no advierte cuando no se usa una entidad marcada como `[[maybe_unused]]`. Una entidad que se declara sin el atributo se puede volver a declarar más adelante con el atributo y viceversa. Una entidad se considera marcada después de la primera declaración que está marcada como analizada y para el resto de la traducción de la unidad de traducción actual.

## <a name="microsoft-specific-attributes"></a>Atributos específicos de Microsoft

- `[[gsl::suppress(rules)]]` este atributo específico de Microsoft se usa para suprimir las advertencias de los comprobadores que aplican las reglas de la [biblioteca de compatibilidad de directrices (GSL)](https://github.com/Microsoft/GSL) en el código. Por ejemplo, considere este fragmento de código:

    ```cpp
    int main()
    {
        int arr[10]; // GSL warning C26494 will be fired
        int* p = arr; // GSL warning C26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning C26481 suppressed
            p = q--; // GSL warning C26481 suppressed
        }
    }
    ```

  En el ejemplo se generan estas advertencias:

  - 26494 (regla de tipo 5: inicializar siempre un objeto).

  - 26485 (regla de límites 3: no se decadencia de matriz a puntero).

  - 26481 (regla de límites 1: no usar aritmética de punteros. En su lugar, use span).

  Las dos primeras advertencias se activan al compilar este código con la herramienta de análisis de código CppCoreCheck instalada y activada. Pero la tercera ADVERTENCIA no se desencadena debido al atributo. Puede suprimir el perfil de límite completo escribiendo [[GSL:: Suppress (Bounds)]] sin incluir un número de regla específico. Las C++ directrices básicas están diseñadas para ayudarle a escribir código mejor y más seguro. El atributo Suppress facilita la desactivación de las advertencias cuando no se desean.
  