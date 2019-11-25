---
title: Configuraciones regionales y páginas de códigos
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
ms.openlocfilehash: 5821048363d92911f2902a580cb11f5b349f5e7c
ms.sourcegitcommit: 4f15b69e35dd112001b24fe9dc836dd5d6902465
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474077"
---
# <a name="locales-and-code-pages"></a>Configuraciones regionales y páginas de códigos

Un identificador de configuración regional refleja el idioma y las convenciones locales de una determinada zona geográfica. Un idioma determinado se puede hablar en varios países o regiones; por ejemplo, el portugués se habla en Portugal y Brasil. A la inversa, una región o un país pueden tener más de un idioma oficial. Por ejemplo, Canadá tiene dos idiomas, el inglés y el francés. Es decir, Canadá tiene dos configuraciones regionales distintas, el inglés canadiense y el francés canadiense. Entre las categorías dependientes de la configuración regional se encuentran el formato de fechas y el formato de presentación de valores de moneda.

El idioma determina las convenciones de formato de datos y texto, mientras que el país o la región determinan las convenciones locales. Cada idioma tiene una asignación única, representada por páginas de códigos, que incluye caracteres distintos de los del alfabeto (como los signos de puntuación y los números). Una página de códigos es un juego de caracteres y está relacionada con el idioma. As such, a [locale](../c-runtime-library/locale.md) is a unique combination of language, country/region, and code page. The locale and code page setting can be changed at run time by calling the [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) function.

Idiomas distintos pueden utilizar páginas de códigos distintas. Por ejemplo, la página de códigos ANSI 1252 se utiliza para el inglés y para la mayoría de idiomas europeos, mientras que la página de códigos ANSI 932 se utiliza para los caracteres Kanji del japonés. La práctica totalidad de páginas de códigos comparten el juego de caracteres ASCII para los 128 caracteres inferiores (de 0x00 a 0x7F).

Una página de códigos de un solo byte se puede representar en una tabla (con 256 entradas) como una asignación de valores de byte a caracteres (incluidos números y signos de puntuación), o glifos. Una página de códigos multibyte también se puede representar como una tabla de gran tamaño (con 64.000 entradas) de valores de doble byte a caracteres. In practice, however, it is usually represented as a table for the first 256 (single-byte) characters and as ranges for the double-byte values.

Para obtener más información sobre las páginas de códigos, vea [Páginas de códigos](../c-runtime-library/code-pages.md).

La biblioteca en tiempo de ejecución de C tiene dos tipos de páginas de códigos internas: regionales y multibyte. You can change the current code page during program execution (see the documentation for the [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) and [_setmbcp](../c-runtime-library/reference/setmbcp.md) functions). Also, the run-time library might obtain and use the value of the operating system code page, which is constant for the duration of the program's execution.

Cuando la página de códigos regional cambia, el comportamiento del conjunto de funciones dependiente de la configuración regional cambia a lo que indica la página de códigos elegida. De forma predeterminada, todas las funciones dependientes de la configuración regional empiezan a ejecutarse con una página de códigos regional única de la configuración regional "C". Se puede cambiar la página de códigos regional interna (así como otras propiedades específicas de la configuración regional) llamando a la función `setlocale`. Una llamada a la función `setlocale`(LC_ALL, "") establece la configuración regional en lo que indica la configuración regional de usuario del sistema operativo.

De forma similar, cuando la página de códigos multibyte cambia, el comportamiento de las funciones multibyte cambia a lo que indica la página de códigos elegida. De forma predeterminada, todas las funciones multibyte empiezan a ejecutarse con una página de códigos multibyte correspondiente a la página de códigos predeterminada del sistema operativo. Se puede cambiar la página de códigos multibyte interna llamando a la función `_setmbcp`.

La función en tiempo de ejecución de C `setlocale` establece, cambia o consulta una parte o la totalidad de la información relativa a la configuración regional del programa actual. The [_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) routine is a wide-character version of `setlocale`; the arguments and return values of `_wsetlocale` are wide-character strings.

## <a name="see-also"></a>Vea también

[Unicode y MBCS](../text/unicode-and-mbcs.md)<br/>
[Ventajas de la portabilidad de los juegos de caracteres](../text/benefits-of-character-set-portability.md)
