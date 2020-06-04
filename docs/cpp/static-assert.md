---
title: static_assert
ms.date: 07/29/2019
f1_keywords:
- static_assert_cpp
helpviewer_keywords:
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
ms.openlocfilehash: a3336e9e41e3dc6804c2398d3ef815ba8c471e50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160910"
---
# <a name="static_assert"></a>static_assert

Comprueba una aserción de software en tiempo de compilación. Si la expresión constante especificada es falsa, el compilador muestra el mensaje especificado, si se proporciona uno, y la compilación produce un error C2338; de lo contrario, la declaración no tiene ningún efecto.

## <a name="syntax"></a>Sintaxis

```
static_assert( constant-expression, string-literal );

static_assert( constant-expression ); // C++17 (Visual Studio 2017 and later)
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*expresión constante*|Una expresión constante entera que se puede convertir en un valor booleano.<br /><br /> Si la expresión evaluada es cero (false), se muestra el parámetro *String-literal* y se produce un error en la compilación. Si la expresión es distinto de cero (true), la declaración de **static_assert** no tiene ningún efecto.|
|*string-literal*|Un mensaje que se muestra si el parámetro *Constant-Expression* es cero. El mensaje es una cadena de caracteres del [juego de caracteres base](../c-language/ascii-character-set.md) del compilador; es decir, no [caracteres anchos o multibyte](../c-language/multibyte-and-wide-characters.md).|

## <a name="remarks"></a>Observaciones

El parámetro *Constant-Expression* de una declaración de **static_assert** representa una *aserción de software*. Una aserción de software especifica una condición que se espera que sea cierta (valor true) en un determinado punto del programa. Si la condición es true, la declaración de **static_assert** no tiene ningún efecto. Si la condición es falsa, se produce un error en la aserción, el compilador muestra el mensaje en el parámetro de *literal de cadena* y se produce un error en la compilación. En Visual Studio 2017 y versiones posteriores, el parámetro String-literal es opcional.

La declaración **static_assert** prueba una aserción de software en tiempo de compilación. En cambio, la [macro Assert y las funciones _assert y _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) prueban una aserción de software en tiempo de ejecución y incurren en tiempo de ejecución en el espacio o en el tiempo. La declaración **static_assert** es especialmente útil para depurar plantillas, porque los argumentos de plantilla se pueden incluir en el parámetro *Constant-Expression* .

El compilador examina la declaración de **static_assert** de errores de sintaxis cuando se encuentra la declaración. El compilador evalúa el parámetro *Constant-Expression* inmediatamente si no depende de un parámetro de plantilla. De lo contrario, el compilador evalúa el parámetro *Constant-Expression* cuando se crea una instancia de la plantilla. Por consiguiente, el compilador puede emitir un mensaje de diagnóstico una vez cuando se encuentra la declaración y otra vez cuando se crea una instancia de la plantilla.

Puede usar la palabra clave **static_assert** en el ámbito de espacio de nombres, clase o bloque. (La palabra clave **static_assert** es técnicamente una declaración, aunque no introduce un nuevo nombre en el programa, porque se puede utilizar en el ámbito de espacio de nombres).

## <a name="description"></a>Descripción

En el ejemplo siguiente, la declaración de **static_assert** tiene el ámbito de espacio de nombres. Dado que el compilador conoce el tamaño del tipo `void *`, la expresión se evalúa inmediatamente.

## <a name="example"></a>Ejemplo

```cpp
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");
```

## <a name="description"></a>Descripción

En el ejemplo siguiente, la declaración de **static_assert** tiene ámbito de clase. El **static_assert** comprueba si un parámetro de plantilla es un tipo de datos antiguos (POD) *sin formato* . El compilador examina la declaración de **static_assert** cuando se declara, pero no evalúa el parámetro *Constant-Expression* hasta que se crea una instancia de la plantilla de clase `basic_string` en `main()`.

## <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iosfwd>
namespace std {
template <class CharT, class Traits = std::char_traits<CharT> >
class basic_string {
    static_assert(std::is_pod<CharT>::value,
                  "Template argument CharT must be a POD type in class template basic_string");
    // ...
    };
}

struct NonPOD {
    NonPOD(const NonPOD &) {}
    virtual ~NonPOD() {}
};

int main()
{
    std::basic_string<char> bs;
}
```

## <a name="description"></a>Descripción

En el ejemplo siguiente, la declaración de **static_assert** tiene ámbito de bloque. En el **static_assert** se comprueba que el tamaño de la estructura vmpage sea es igual a la paginación de la memoria virtual del sistema.

## <a name="example"></a>Ejemplo

```cpp
#include <sys/param.h> // defines PAGESIZE
class VMMClient {
public:
    struct VMPage { // ...
           };
    int check_pagesize() {
    static_assert(sizeof(VMPage) == PAGESIZE,
        "Struct VMPage must be the same size as a system virtual memory page.");
    // ...
    }
// ...
};
```

## <a name="see-also"></a>Consulte también

[Aserción y mensajes proporcionados por el usuario (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
[#error (directiva) (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert (macro), _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Templates](../cpp/templates-cpp.md) (Plantillas [C++])<br/>
[Juego de caracteres ASCII](../c-language/ascii-character-set.md)<br/>
[Declaraciones y definiciones](declarations-and-definitions-cpp.md)
