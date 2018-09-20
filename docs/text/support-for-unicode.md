---
title: Compatibilidad con Unicode | Microsoft Docs
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4ed04c30eb71086f57cc9a782c320c06a301485
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405039"
---
# <a name="support-for-unicode"></a>Compatibilidad con Unicode

Unicode es una especificación para admitir todos los juegos de caracteres, los que no se puede representar incluidos en un solo byte (es decir, la mayoría de ellos). Si está programando para un mercado internacional, se recomienda que utilice Unicode o una [juego de caracteres multibyte](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS), o el programa de código para que pueda crear para ambos cambiando un modificador.

Un carácter ancho es un código de carácter multilingüe de dos bytes. Se pueden representar decenas de miles de caracteres, que incluyen casi todos los caracteres que se utilizan en la informática moderna alrededor del mundo, incluidos los símbolos técnicos y caracteres de publicación especiales, según la especificación Unicode como un todo solo caracteres codifican por mediante UTF-16. Caracteres que no pueden representarse en un solo carácter ancho pueden representarse en un par Unicode mediante la característica de par suplente Unicode. Dado que casi todos los caracteres de uso común está representado en UTF-16 en un carácter ancho de 16 bits único, con caracteres anchos simplifica la programación con juegos de caracteres internacionales. Caracteres anchos codificados con UTF-16LE (para little-endian) son el formato de caracteres nativo para Windows.

Una cadena de caracteres anchos se representa como una matriz `wchar_t[]` y apunta a ella un puntero `wchar_t*`. Cualquier carácter ASCII se puede representar como un carácter ancho agregando la letra L al principio del carácter. Por ejemplo, L '\0' es el carácter nulo final de todo (16 bits). De manera similar, cualquier literal de cadena ASCII se puede representar como un literal de cadena de caracteres anchos agregando la letra L al principio del literal ASCII (L"Hola").

En general, los caracteres anchos ocupan más espacio en la memoria que los caracteres multibyte, pero se procesan más rápido. Además, varias configuraciones regionales se puede representar a la vez en una codificación multibyte, mientras que todos los caracteres se establece en el mundo se representan al mismo tiempo mediante la representación Unicode.

Todo el marco MFC está habilitado para Unicode. MFC habilita Unicode con macros portables, como se muestra en la tabla siguiente.

## <a name="portable-data-types-in-mfc"></a>Tipos de datos portables en MFC

|Tipo de datos no portable|Reemplazado por esta macro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (Tipo de datos de Win32) `LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Tipo de datos de Win32) `LPCWSTR`|`LPCTSTR`|

Clase `CString` usa `_TCHAR` como base y proporciona constructores y operadores para realizar conversiones fácilmente. La mayoría de las operaciones de cadena de Unicode se puede escribir con la misma lógica que se usa para administrar el juego de caracteres ANSI de Windows, con la diferencia de que la unidad de operación básica es un carácter de 16 bits en lugar de un byte de 8 bits. A diferencia de cuando se trabaja con juegos de caracteres multibyte, no es necesario (y no se debe) tratar un carácter Unicode como si fueran dos bytes independientes. Sin embargo,, tiene que tratar con la posibilidad de un solo carácter representado por un par suplente de caracteres anchos. En general, no escribir código que supone que la longitud de una cadena es el mismo que el número de caracteres, si estrechos o anchos, que contiene.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Usar Unicode MFC y soporte técnico de juegos de caracteres Multibyte (MBCS) del conjunto](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Habilitar Unicode en mi programa](../text/international-enabling.md)

- [Habilitar Unicode y MBCS en mi programa](../text/internationalization-strategies.md)

- [Utilizar Unicode para crear un programa internacionalizado](../text/unicode-programming-summary.md)

- [Descubra las ventajas de Unicode](../text/benefits-of-character-set-portability.md)

- [Usar wmain para pasar argumentos de caracteres anchos a mi programa](../text/support-for-using-wmain.md)

- [Ver un resumen de la programación con Unicode](../text/unicode-programming-summary.md)

- [Obtenga información sobre asignaciones de texto genérico para portabilidad de ancho de byte](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Vea también

[Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)<br/>
[Compatibilidad con el uso de wmain](../text/support-for-using-wmain.md)