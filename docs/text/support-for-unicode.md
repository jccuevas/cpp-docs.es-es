---
title: Compatibilidad con Unicode
ms.date: 01/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: c30cb1fbfb1930b5e4b026e58c478f0099e8ecdf
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929913"
---
# <a name="support-for-unicode"></a>Compatibilidad con Unicode

Unicode es una especificación para admitir todos los juegos de caracteres, incluidos aquellos que no se pueden representar en un solo byte.  Si está programando para un mercado internacional, se recomienda usar Unicode o un juego de [caracteres multibyte](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS). O bien, codifique el programa para que pueda compilarlo mediante el cambio de un modificador.

Un carácter ancho es un código de carácter multilingüe de dos bytes. Decenas de miles de caracteres, que incluye casi todos los caracteres que se usan en la informática moderna en todo el mundo, incluidos los símbolos técnicos y los caracteres de publicación especiales, se pueden representar de acuerdo con la especificación Unicode como un carácter ancho único codificado por mediante UTF-16. Los caracteres que no se pueden representar en un solo carácter ancho se pueden representar en un par Unicode mediante la característica de par suplente Unicode. Dado que casi todos los caracteres del uso común se representan en UTF-16 en un solo carácter ancho de 16 bits, el uso de caracteres anchos simplifica la programación con juegos de caracteres internacionales. Los caracteres anchos codificados mediante UTF-16LE (para Little-endian) son el formato de caracteres nativos de Windows.

Una cadena de caracteres anchos se representa como una matriz `wchar_t[]` y apunta a ella un puntero `wchar_t*`. Cualquier carácter ASCII se puede representar como un carácter ancho agregando la letra L al principio del carácter. Por ejemplo, L ' \ 0 ' es el carácter NULL ancho de terminación (16 bits). De manera similar, cualquier literal de cadena ASCII se puede representar como un literal de cadena de caracteres anchos agregando la letra L al principio del literal ASCII (L"Hola").

En general, los caracteres anchos ocupan más espacio en la memoria que los caracteres multibyte, pero se procesan más rápido. Además, solo se puede representar una configuración regional a la vez en una codificación multibyte, mientras que todos los juegos de caracteres del mundo se representan simultáneamente mediante la representación Unicode.

Todo el marco MFC está habilitado para Unicode. MFC habilita Unicode con macros portables, como se muestra en la tabla siguiente.

## <a name="portable-data-types-in-mfc"></a>Tipos de datos portables en MFC

|Tipo de datos no portable|Reemplazado por esta macro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (Tipo de datos Win32),`LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Tipo de datos Win32),`LPCWSTR`|`LPCTSTR`|

La `CString` clase `_TCHAR` usa como base y proporciona constructores y operadores para realizar conversiones sencillas. La mayoría de las operaciones de cadena de Unicode se puede escribir con la misma lógica que se usa para administrar el juego de caracteres ANSI de Windows, con la diferencia de que la unidad de operación básica es un carácter de 16 bits en lugar de un byte de 8 bits. A diferencia de cuando se trabaja con juegos de caracteres multibyte, no es necesario (y no se debe) tratar un carácter Unicode como si fueran dos bytes independientes. Sin embargo, tiene que tratar con la posibilidad de que un solo carácter esté representado por un par suplente de caracteres anchos. En general, no Escriba código que asuma que la longitud de una cadena es igual que el número de caracteres, ya sean estrechos o anchos, que contiene.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Usar la compatibilidad con Unicode y el juego de caracteres multibyte (MBCS) de MFC](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Habilitar Unicode en mi programa](../text/international-enabling.md)

- [Habilitar Unicode y MBCS en mi programa](../text/internationalization-strategies.md)

- [Usar Unicode para crear un programa internacionalizado](../text/unicode-programming-summary.md)

- [Obtener información sobre las ventajas de Unicode](../text/benefits-of-character-set-portability.md)

- [Usar wmain para poder pasar argumentos de caracteres anchos a mi programa](../text/support-for-using-wmain.md)

- [Ver un resumen de la programación con Unicode](../text/unicode-programming-summary.md)

- [Más información sobre las asignaciones de texto genérico para la portabilidad de ancho de bytes](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Vea también

[Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)<br/>
[Compatibilidad con el uso de wmain](../text/support-for-using-wmain.md)