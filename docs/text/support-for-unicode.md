---
title: Compatibilidad con Unicode | Documentos de Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b9d5a435339e366d70749d64e5aae9264fe12b1f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858411"
---
# <a name="support-for-unicode"></a>Compatibilidad con Unicode

Unicode es una especificación para admitir todos los juegos de caracteres, incluidos aquellos que no pueden representarse en un solo byte (es decir, la mayoría de ellos). Si está programando para un mercado internacional, se recomienda que utilice Unicode o una [juego de caracteres multibyte](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS), o el programa de código, lo que permite compilar para cualquiera de ellos cambiando un modificador.

Un carácter ancho es un código de carácter multilingüe de dos bytes. Decenas de miles de caracteres, que cuenta con casi todos los caracteres que se utilizan en la informática moderna alrededor del mundo, incluidos los símbolos técnicos y caracteres especiales de publicación, se pueden representar según la especificación Unicode como un todo el único carácter codificado por mediante UTF-16. Caracteres que no pueden representarse en un solo carácter ancho se pueden representar en un par Unicode con la característica de par de suplentes de Unicode. Dado que casi todos los caracteres de uso común se representan en UTF-16 en un carácter de ancho de 16 bits único, con los caracteres anchos simplifica la programación con juegos de caracteres internacionales. Caracteres anchos codificados con UTF-16LE (para little-endian) tienen el formato de caracteres nativo para Windows.

Una cadena de caracteres anchos se representa como una matriz `wchar_t[]` y apunta a ella un puntero `wchar_t*`. Cualquier carácter ASCII se puede representar como un carácter ancho agregando la letra L al principio del carácter. Por ejemplo, L'\0' es el carácter **nulo** ancho (de 16 bits) de terminación. De manera similar, cualquier literal de cadena ASCII se puede representar como un literal de cadena de caracteres anchos agregando la letra L al principio del literal ASCII (L"Hola").

En general, los caracteres anchos ocupan más espacio en la memoria que los caracteres multibyte, pero se procesan más rápido. Además, varias configuraciones regionales pueden representar a la vez en una codificación multibyte, mientras que todos los caracteres se establece en el mundo representa simultáneamente a la representación de Unicode.

Todo el marco MFC está habilitado para Unicode. MFC habilita Unicode con macros portables, como se muestra en la tabla siguiente.

## <a name="portable-data-types-in-mfc"></a>Tipos de datos portables en MFC

|Tipo de datos no portable|Reemplazado por esta macro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (Tipo de datos de Win32), `LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Tipo de datos de Win32), `LPCWSTR`|`LPCTSTR`|

Clase `CString` usa `_TCHAR` como base y proporciona constructores y operadores para realizar conversiones sencillas. La mayoría de las operaciones de cadena de Unicode se puede escribir con la misma lógica que se usa para administrar el juego de caracteres ANSI de Windows, con la diferencia de que la unidad de operación básica es un carácter de 16 bits en lugar de un byte de 8 bits. A diferencia de cuando se trabaja con juegos de caracteres multibyte, no es necesario (y no se debe) tratar un carácter Unicode como si fueran dos bytes independientes. Sin embargo,, tiene que tratar con la posibilidad de un solo carácter representado por un par suplente de caracteres anchos. En general, no se escribe código que supone que la longitud de una cadena es el mismo que el número de caracteres, si estrechos o anchos, que contiene.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Usar Unicode MFC y soporte técnico de juegos de caracteres Multibyte (MBCS) del conjunto](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Habilitar Unicode en mi programa](../text/international-enabling.md)

- [Habilitar Unicode y MBCS en mi programa](../text/internationalization-strategies.md)

- [Utilizar Unicode para crear un programa internacionalizado](../text/unicode-programming-summary.md)

- [Obtenga información acerca de las ventajas de Unicode](../text/benefits-of-character-set-portability.md)

- [Usar wmain para pasar argumentos de caracteres anchos a mi programa](../text/support-for-using-wmain.md)

- [Ver un resumen de la programación con Unicode](../text/unicode-programming-summary.md)

- [Obtenga información acerca de las asignaciones de texto genérico para portabilidad de ancho de byte](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Vea también

[Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)  
[Compatibilidad con el uso de wmain](../text/support-for-using-wmain.md)  
