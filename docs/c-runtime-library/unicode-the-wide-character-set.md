---
title: 'Unicode: el juego de caracteres anchos'
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 3a0c5698544c72e19feea8f35b7f5a516d95d561
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444486"
---
# <a name="unicode-the-wide-character-set"></a>Unicode: el juego de caracteres anchos

Un carácter ancho es un código de carácter multilingüe de dos bytes. Todos los caracteres usados en la informática moderna alrededor del mundo, como los símbolos técnicos o los caracteres de publicación especiales, se pueden representar de acuerdo con la especificación Unicode en forma de carácter ancho. La norma Unicode cuenta con un amplio reconocimiento, de cuyo desarrollo y mantenimiento se encarga un gran consorcio que incluye a Microsoft.

Un carácter ancho es de tipo **wchar_t**. Una cadena de caracteres anchos se representa como una matriz **wchar_t[]** y apunta a ella un puntero `wchar_t*`. Cualquier carácter ASCII se puede representar como un carácter ancho si se le antepone la letra **L** como prefijo. Por ejemplo, L"\0" es el carácter nulo ancho final (16 bits). De manera similar, cualquier literal de cadena ASCII se puede representar como un literal de cadena de caracteres anchos con tan solo anteponer la letra L como prefijo del literal ASCII (L"Hola").

En general, los caracteres anchos ocupan más espacio en la memoria que los caracteres multibyte, pero se procesan más rápido. Además, en la codificación multibyte no se pueden representar varias configuraciones regionales a la vez, mientras que la representación de Unicode representa simultáneamente a todos los juegos de caracteres del mundo.

## <a name="see-also"></a>Consulte también

[Internacionalización](../c-runtime-library/internationalization.md)<br/>
[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
