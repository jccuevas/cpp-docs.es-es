---
title: char, wchar_t, char16_t, char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: 8d109ec452df33b774848229837ed3e2eae80dc4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181023"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char, wchar_t, char16_t, char32_t

Los tipos **Char**, **wchar_t**, **char16_t** y **char32_t** son tipos integrados que representan caracteres alfanuméricos, así como glifos no alfanuméricos y caracteres no imprimibles.

## <a name="syntax"></a>Sintaxis

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Observaciones

El tipo **Char** era el tipo de carácter original en C C++y. El tipo **Char sin signo** se suele usar para representar un *byte*, que no es un tipo integrado en C++. El tipo **Char** se puede usar para almacenar caracteres del juego de caracteres ASCII o de cualquiera de los juegos de caracteres ISO-8859, así como los bytes individuales de caracteres de varios bytes, como Shift-JIS o la codificación UTF-8 del juego de caracteres Unicode. Las cadenas de tipo **Char** se conocen como cadenas *estrechas* , incluso cuando se usan para codificar caracteres de varios bytes. En el compilador de Microsoft, **Char** es un tipo de 8 bits.

El tipo de **wchar_t** es un tipo de carácter ancho definido por la implementación. En el compilador de Microsoft, representa un carácter ancho de 16 bits que se usa para almacenar la codificación Unicode codificada como UTF-16LE, el tipo de carácter nativo en los sistemas operativos Windows. Las versiones de caracteres anchos de las funciones de la biblioteca en tiempo de ejecución universal C (UCRT) usan **wchar_t** y sus tipos de puntero y matriz como parámetros y valores devueltos, al igual que las versiones de caracteres anchos de la API nativa de Windows.

Los tipos **char16_t** y **char32_t** representan caracteres anchos de 16 y 32 bits, respectivamente. La codificación Unicode codificada como UTF-16 puede almacenarse en el tipo de **char16_t** , y la codificación Unicode codificada como utf-32 puede almacenarse en el tipo de **char32_t** . Las cadenas de estos tipos y **wchar_t** se conocen como cadenas *anchas* , aunque el término suele referirse específicamente a cadenas de tipo **wchar_t** .

En la C++ biblioteca estándar, el tipo de `basic_string` es especializado para las cadenas anchas y estrechas. Use `std::string` cuando los caracteres sean de tipo **Char**, `std::u16string` cuando los caracteres sean de tipo **char16_t**, `std::u32string` cuando los caracteres sean de tipo **char32_t**y `std::wstring` cuando los caracteres sean de tipo **wchar_t**. Otros tipos que representan texto, incluidos `std::stringstream` y `std::cout` tienen especializaciones para cadenas estrechas y anchas.
