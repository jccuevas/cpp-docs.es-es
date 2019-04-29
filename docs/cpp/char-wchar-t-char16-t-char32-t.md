---
title: char, wchar_t, char16_t, char32_t
ms.date: 02/14/2018
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: 542751cdbd5bb21bb70467163c823e2669373e24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331173"
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t

Los tipos de **char**, **wchar_t**, **char16_t** y **char32_t** son tipos integrados que representan caracteres alfanuméricos, así como glifos no alfanuméricos y caracteres no imprimibles.

## <a name="syntax"></a>Sintaxis

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Comentarios

El **char** tipo era el tipo de carácter original en C y C++. El tipo **unsigned char** a menudo se usa para representar un *bytes*, que no es un tipo integrado en C++. El **char** tipo puede utilizarse para almacenar los caracteres del juego de caracteres ASCII o cualquiera de los juegos de caracteres ISO-8859 e individuales bytes de caracteres de varios bytes como Shift-JIS o la codificación UTF-8 del juego de caracteres Unicode. Cadenas de **char** tipo se conoce como *restringir* cadenas, incluso cuando se usa para codificar los caracteres multibyte. En el compilador de Microsoft, **char** es un tipo de 8 bits.

El **wchar_t** tipo es un tipo de caracteres anchos definido por la implementación. En el compilador de Microsoft, representa un carácter ancho de 16 bits utilizado para almacenar Unicode codificado como UTF-16LE, el tipo de caracteres nativo en los sistemas operativos de Windows. Las versiones de caracteres anchos de uso de funciones de la biblioteca en tiempo de ejecución de C Universal (UCRT) **wchar_t** y su puntero y matriz de tipos como parámetros y valores devueltos, como las versiones de caracteres anchos de la API nativa de Windows.

El **char16_t** y **char32_t** tipos representan caracteres anchos de 16 bits y 32 bits, respectivamente. Unicode codificado como UTF-16 se puede almacenar en el **char16_t** tipo y Unicode codificados como UTF-32 puede almacenarse en el **char32_t** tipo. Las cadenas de estos tipos y **wchar_t** son todas se conoce como *amplia* cadenas, aunque el término suele referirse específicamente a las cadenas de **wchar_t** tipo.

En la biblioteca estándar de C++, el `basic_string` tipo sirve para cadenas anchas y estrechas. Use `std::string` cuando son los caracteres de tipo **char**, `std::u16string` cuando son los caracteres de tipo **char16_t**, `std::u32string` cuando son los caracteres de tipo **char32_t** , y `std::wstring` cuando son los caracteres de tipo **wchar_t**. Otros tipos que representan texto, incluidos `std::stringstream` y `std::cout` disponen de especializaciones para cadenas anchas y estrechas.