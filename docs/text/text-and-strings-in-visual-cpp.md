---
title: Texto y cadenas en Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
ms.openlocfilehash: c6083fcf9db8236df15d1cb5e7de4cc15fe5916e
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626726"
---
# <a name="text-and-strings-in-visual-c"></a>Texto y cadenas en Visual C++

Un aspecto importante en el desarrollo de aplicaciones para los mercados internacionales es la representación apropiada de los juegos de caracteres locales. El juego de caracteres ASCII define los caracteres que están en el intervalo de 0x00 a 0x7F. Hay otros juegos de caracteres, principalmente europeos, que definen los caracteres que están en el intervalo de 0x00 a 0x7F, al igual que el juego de caracteres ASCII, y que también definen un juego de caracteres extendidos de 0x80 a 0xFF. De este modo, un juego de caracteres de un solo byte (SBCS) de 8 bits es suficiente para representar el juego de caracteres ASCII, así como los juegos de caracteres de la mayoría de idiomas europeos. Sin embargo, algunos juegos de caracteres no europeos, como los caracteres Kanji del japonés, incluyen muchos más caracteres de los que puede representar un esquema de codificación de un solo byte y, por consiguiente, requieren una codificación de juego de caracteres multibyte (MBCS).

## <a name="in-this-section"></a>En esta sección

[Unicode y MBCS](../text/unicode-and-mbcs.md)<br/>
Describe la compatibilidad de Visual C++ con la programación mediante Unicode y MBCS.

[Compatibilidad con Unicode](../text/support-for-unicode.md)<br/>
Describe Unicode, que es una especificación para admitir todos los juegos de caracteres, incluidos los juegos de caracteres que no pueden representarse en un solo byte.

[Compatibilidad con juegos de caracteres Multibyte (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
Describe MBCS, que es una alternativa a Unicode para la compatibilidad con juegos de caracteres, como el japonés y el chino, que no pueden representarse en un solo byte.

[Asignaciones de texto genérico en tchar.h](../text/generic-text-mappings-in-tchar-h.md)<br/>
Proporciona las asignaciones de texto genérico específicas de Microsoft para muchos tipos de datos, rutinas y demás objetos.

[Cómo: Convertir entre distintos tipos de cadenas](../text/how-to-convert-between-various-string-types.md)<br/>
Muestra cómo se convierten distintos tipos de cadenas de Visual C++ en otras cadenas.

## <a name="related-sections"></a>Secciones relacionadas

[Internacionalización](../c-runtime-library/internationalization.md)<br/>
Describe la compatibilidad internacional en la biblioteca en tiempo de ejecución de C.

[Ejemplos de programación internacional](https://github.com/Microsoft/VCSamples)<br/>
Proporciona vínculos a ejemplos en los que se muestra la internacionalización en Visual C++.

[Cadenas de idioma de país o región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
Proporciona las cadenas de idioma y de país o región en la biblioteca en tiempo de ejecución de C.
