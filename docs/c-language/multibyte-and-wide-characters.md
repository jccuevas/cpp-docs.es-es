---
title: Caracteres anchos y multibyte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc259a75ab12352a7d0029241496aea22803152a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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