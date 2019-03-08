---
title: Caracteres anchos y multibyte
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- character data types [C]
- Unicode [C++], wide character set
- types [C], character
- characters [C++], wide
- international applications [C++], character display
- multibyte characters [C++]
- wide characters [C++]
- characters [C++], codes
- character codes [C++], wide
- character codes [C++], multibyte
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
ms.openlocfilehash: 0d573fac938f5e4d62c99c8cd6e676b96123a0c4
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152019"
---
# <a name="multibyte-and-wide-characters"></a>Caracteres anchos y multibyte

Un carácter multibyte es un carácter compuesto por secuencias de uno o más bytes. Cada secuencia de bytes representa un único carácter en el juego de caracteres extendidos. Los caracteres multibyte se utilizan en juegos de caracteres tales como Kanji.

Los caracteres anchos son códigos de caracteres multilingües con un ancho invariable de 16 bits. El tipo de las constantes de caracteres es `char`; para los caracteres anchos, el tipo es `wchar_t`. Puesto que los caracteres anchos siempre son de tamaño fijo, con los caracteres anchos se simplifica la programación con juegos de caracteres internacionales.

El literal de cadena de carácter ancho `L"hello"` se convierte en una matriz de seis enteros de tipo `wchar_t`.

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

La especificación Unicode es la especificación de caracteres anchos. Las rutinas de la biblioteca en tiempo de ejecución para traducir caracteres multibyte y anchos incluyen `mbstowcs`, `mbtowc`, `wcstombs` y `wctomb`.

## <a name="see-also"></a>Vea también

[Identificadores de C](../c-language/c-identifiers.md)
