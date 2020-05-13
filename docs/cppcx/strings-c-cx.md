---
title: Cadenas (C++/CX)
ms.date: 01/22/2017
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
ms.openlocfilehash: a67b9a4552dc83791c05029cca76f60fd83df0f1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745349"
---
# <a name="strings-ccx"></a>Cadenas (C++/CX)

El texto de Windows Runtime se representa en C++/CX mediante la [clase Platform::String](../cppcx/platform-string-class.md). Utilice `Platform::String Class` el uso de las cadenas de ida y vuelta a los métodos de las clases de Windows en tiempo de ejecución, o cuando se interactúa con otros componentes de Windows en tiempo de ejecución a través del límite de la interfaz binaria de la aplicación (ABI). La clase `Platform::String Class` proporciona métodos para varias operaciones de cadena comunes, pero no está diseñada para ser una clase de cadena completa. En el módulo de C++, utiliza los tipos de cadena de C++ estándar tales como [wstring](../standard-library/basic-string-class.md) para cualquier procesamiento de texto significativo y, a continuación, convierte el resultado final a [Platform::String^](../cppcx/platform-string-class.md) antes de pasarlo a o desde una interfaz pública. La conversión entre `wstring` o `wchar_t*` y `Platform::String`es un proceso sencillo y eficaz.

**Operación rápida de paso**

En algunos casos, el compilador puede comprobar que puede crear con seguridad un objeto `Platform::String` o pasar un objeto `String` a una función sin copiar los datos de cadena subyacentes. Dichas operaciones se conocen como operaciones *rápidas de paso* y se producen de forma transparente.

## <a name="string-construction"></a>Construcción de cadena

El valor de un objeto `String` es una secuencia inmutable (de solo lectura) de caracteres `char16` (Unicode de 16 bits). Dado que un objeto `String` es inmutable, la asignación de un nuevo literal de cadena a una variable `String` reemplaza realmente el objeto `String` original con un nuevo objeto `String` . Las operaciones de concatenación implican la destrucción del objeto `String` original y la creación de un nuevo objeto.

**Literales**

Un *carácter literal* es un carácter que se encierra entre comillas simples y una *cadena literal* es una secuencia de caracteres que se encierra entre comillas dobles. Si utilizas un literal para inicializar una variable String^, el compilador supone que el literal consta de caracteres `char16` . Es decir, no hay que colocar delante del literal el modificador de cadena 'L' ni incluir el literal en una macro **_T()** o **TEXT()** . Para obtener más información sobre la compatibilidad de C++ para Unicode, consulta [Unicode Programming Summary](../text/unicode-programming-summary.md).

En el ejemplo siguiente se muestran varias maneras de crear objetos `String` .

[!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]

## <a name="string-handling-operations"></a>Operaciones de control de cadenas

La clase `String` proporciona métodos y operadores para concatenar, comparar cadenas y otras operaciones de cadena básicas. Para realizar manipulaciones de cadena más extensas, utilice la función miembro `String::Data()` para recuperar el valor del objeto `String^` como un objeto `const wchar_t*`. A continuación, use ese valor para inicializar un objeto `std::wstring`, que proporcionan funciones mejoradas de control de cadenas.

[!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]

## <a name="string-conversions"></a>Conversiones de cadenas

Un objeto `Platform::String` solo puede contener caracteres `char16` o el carácter `NULL` . Si la aplicación tiene que trabajar con caracteres de 8 bits, utilice `const wchar_t*` [String::Data](../cppcx/platform-string-class.md#data) para extraer el texto como un archivo . Puedes utilizar las funciones de Windows o las funciones de biblioteca estándar adecuadas para funcionar en los datos y convertirlos de nuevo en un objeto `wchar_t*` o [wstring](../standard-library/basic-string-class.md), que puedes utilizar para crear un nuevo objeto `Platform::String`.

En el fragmento de código siguiente se muestra cómo convertir una variable `String^` a y desde una variable `wstring` . Para obtener más información acerca de la manipulación de cadenas que se utiliza en este ejemplo, consulta [basic_string::replace](../standard-library/basic-string-class.md#replace).

[!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]

## <a name="string-length-and-embedded-null-values"></a>Longitud de cadena y valores NULL incrustados

El [String::Length](../cppcx/platform-string-class.md#length) devuelve el número de caracteres de la cadena, no el número de bytes. El carácter NULL de terminación no se cuenta, a menos que lo especifiques explícitamente cuando utilices semántica de pila para crear una cadena.

Un objeto `Platform::String` puede contener valores NULL incrustados, pero solo cuando el valor NULL es el resultado de una operación de concatenación. Los valores NULL incrustados no se admiten en los literales de cadena; por consiguiente, no puedes utilizar valores NULL incrustados de esa manera para inicializar un objeto `Platform::String`. Los valores NULL incrustados en un objeto `Platform::String` se omiten cuando la cadena se muestra, por ejemplo, cuando se asigna a una propiedad `TextBlock::Text` . Los valores NULL incrustados se quitan cuando la propiedad `Data` devuelve el valor de cadena.

## <a name="stringreference"></a>StringReference

En algunos casos, el código (a) recibe un literal de cadena std::wstring o wchar_t cadena o L"" y simplemente lo pasa a otro método que toma un String como parámetro de entrada. Siempre que el propio búfer de cadena original siga siendo válido y no se modifique antes de que la función devuelva un valor, puedes convertir la cadena o literal de cadena `wchar_t*` a [Platform::StringReference](../cppcx/platform-stringreference-class.md), y pasar esta en lugar de `Platform::String^`. Esto es posible debido a que `StringReference` tiene una conversión definida por el usuario a `Platform::String^`. Puedes utilizar `StringReference` para evitar realizar una copia adicional de la cadena de datos. En los bucles en los que pases un gran número de cadenas, o si pasas cadenas de gran tamaño, puedes lograr una mejora significativa en el rendimiento si utilizas `StringReference`. Sin embargo, dado que `StringReference` básicamente toma prestado el búfer de cadena original, debes extremar las precauciones para evitar daños en la memoria. No debes pasar un objeto `StringReference` a un método asincrónico a menos que estés seguro de que la cadena original estará en el ámbito cuando dicho método devuelva un valor. Un objeto String^ que se inicializa desde una clase StringReference forzará la asignación y la copia de los datos de cadena si se produce una segunda operación de asignación. En este caso, se perderá la ventaja de rendimiento de `StringReference`.

Ten en cuenta que `StringReference` es un tipo de clase de C++ estándar, no una clase ref, y que no puedes utilizarlo en la interfaz pública de las clases ref que definas.

En el ejemplo siguiente se muestra cómo utilizar StringReference:

```cpp
void GetDecodedStrings(std::vector<std::wstring> strings)
{
    using namespace Windows::Security::Cryptography;
    using namespace Windows::Storage::Streams;

    for (auto&& s : strings)
    {
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)
        // Call using StringReference:
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));

        //...do something with buffer
    }
}
```
