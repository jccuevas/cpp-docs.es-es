---
title: Atributos de C++
ms.date: 06/01/2018
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: a4d24324165f3cce60d259adf6e3d21638296cf8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471830"
---
# <a name="attributes-in-c"></a>Atributos de C++

El estándar de C++ define un conjunto de atributos y también permite a los proveedores de compiladores definir sus propios atributos (dentro de un espacio de nombres específicos del proveedor), pero los compiladores deben reconocer solamente los atributos definidos en el estándar.

En algunos casos, los atributos estándar se superponen con los parámetros de modificador declspec específicas del compilador. En Visual C++, puede usar el `[[deprecated]]` atributo en lugar de usar `declspec(deprecated)` y cualquier compilador conforme reconocerá el atributo. Para todos los demás parámetros de modificador declspec como dllimport y dllexport, hay todavía ningún atributo equivalente por lo que debe seguir usar la sintaxis del modificador declspec. Los atributos no afectan el sistema de tipos y no cambian el significado de un programa. Los compiladores omiten los valores de atributo que no reconocen.

**Visual Studio 2017 versión 15.3 y versiones posterior** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): en el ámbito de una lista de atributos, puede especificar el espacio de nombres para todos los nombres con una sola **mediante** introducer:

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>Atributos estándar de C++

En C ++ 11, los atributos proporcionan una forma estandarizada para anotar las construcciones de C++ (incluyendo, pero sin limitarse a las clases, funciones, variables y bloques) con información adicional que puede o no ser específicas del proveedor. Un compilador puede usar esta información para generar los mensajes informativos, o para aplicar una lógica especial al compilar el código con atributos. El compilador omite todos los atributos que no reconoce, lo que significa que no se puede definir sus propios atributos personalizados con esta sintaxis. Los atributos se incluyan entre corchetes dobles:

```cpp
[[deprecated]]
void Foo(int);
```

Los atributos representan una alternativa a las extensiones específicas del proveedor como __declspec () (Visual C++), las directivas #pragma, estandarizada o &#95; &#95;atributo&#95; &#95; (GNU). Sin embargo, todavía deberá usar las construcciones específicas del proveedor para la mayoría de los casos. El estándar especifica actualmente los siguientes atributos que se debería reconocer un compilador adecuado:

- `[[noreturn]]` Especifica que nunca se devuelve una función; en otras palabras siempre produce una excepción. El compilador puede ajustar sus reglas de compilación para `[[noreturn]]` entidades.

- `[[carries_dependency]]` Especifica que la función propaga la dependencia de datos de ordenación con respecto a la sincronización de subprocesos. El atributo puede aplicarse a uno o varios parámetros para especificar que el argumento pasado lleva a cabo una dependencia en el cuerpo de la función. El atributo puede aplicarse a la propia función, para especificar que el valor devuelto incluye una dependencia fuera de la función. El compilador puede usar esta información para generar código más eficaz.

- `[[deprecated]]` **Visual Studio 2015 y versiones posterior:** especifica que una función no está pensada para usarse y puede que no exista en futuras versiones de una interfaz de biblioteca. El compilador puede utilizarlo para generar un mensaje informativo cuando el código de cliente intenta llamar a la función. Puede aplicarse a la declaración de una clase, un nombre typedef, una variable, un miembro de datos no estático, una función, un espacio de nombres, una enumeración, un enumerador o una especialización de plantilla.

- `[[fallthrough]]` **Visual Studio 2017 y versiones posterior:** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) la `[[fallthrough]]` atributo se puede usar en el contexto de [cambiar](switch-statement-cpp.md) instrucciones como una sugerencia para el compilador (o cualquiera que lea el código) que se prevé el comportamiento de fallthrough. El compilador de Visual C++ actualmente no advierte sobre el comportamiento de fallthrough, por lo que este atributo no tiene ningún comportamiento del compilador efecto.

- `[[nodiscard]]` **Visual Studio 2017 versión 15.3 y versiones posterior:** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) especifica que el valor devuelto de una función no está pensado para descartarse. Genera la advertencia de C4834, tal como se muestra en este ejemplo:

   ```cpp
   [[nodiscard]]
   int foo(int i) { return i * i; }

   int main()
   {
       foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
       return 0;
   }
   ```

- `[[maybe_unused]]` **Visual Studio 2017 versión 15.3 y versiones posterior:** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) especifica que una variable, función, clase, typedef, miembro de datos no estáticos, enum o especialización de plantilla intencionadamente no puede usarse. El compilador no avisa cuando una entidad marcada `[[maybe_unused]]` no se utiliza. Más adelante se puede volver a declarar una entidad que está declarada sin el atributo con el atributo y viceversa. Se considera una entidad marcada se analiza su primera declaración de marcado y para el resto de la traducción de la unidad de traducción actual.

## <a name="microsoft-specific-attributes"></a>Atributos específicos de Microsoft

- `[[gsl::suppress(rules)]]` Este atributo específico de Microsoft se utiliza para suprimir las advertencias de comprobadores que exigen [directrices de soporte técnico de biblioteca (GSL)](https://github.com/Microsoft/GSL) reglas en el código. Por ejemplo, considere este fragmento de código:

    ```cpp
    void main()
    {
        int arr[10]; // GSL warning 26494 will be fired
        int* p = arr; // GSL warning 26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning 26481 suppressed
            p = q--; // GSL warning 26481 suppressed
        }
    }
    ```

   El ejemplo genera estas advertencias:

   - 26494 (tipo de la regla 5: siempre debe inicializarse un objeto.)

   - 26485 (límites de la regla 3: ninguna matriz de decadencia de puntero.)

   - 26481 (límites de la regla 1: no usar aritmética de puntero. Usar intervalo en su lugar).

   Las dos primeras advertencias se activan cuando se compila este código con la herramienta de análisis de código CppCoreCheck instalado y activado. Pero no se activa la advertencia tercer debido al atributo. Puede suprimir todo el perfil bounds escribiendo [[gsl::suppress(bounds)]] sin incluir un número específico de regla. C++ Core Guidelines están diseñados para ayudarle a escribir código mejor y más seguro. El atributo suprimir facilita desactivar las advertencias cuando no se querían.