---
title: Trígrafos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ??) trigraph
- ??- trigraph
- question mark, in trigraphs
- ??= trigraph
- ?? trigraph
- ??< trigraph
- ??/ trigraph
- trigraphs
- '? symbol, trigraph'
- ??> trigraph
- ??! trigraph
- ??' trigraph
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3c83fc3feecc1b79f28c1b00b94469d30b93d8b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389961"
---
# <a name="trigraphs"></a>Trígrafos
El juego de caracteres de origen de programas de código fuente C está incluido dentro del juego de caracteres ASCII de 7 bits, pero es un superconjunto del conjunto de códigos invariantes ISO 646-1983. Las secuencias de trígrafos permiten escribir programas de C usando solo el conjunto de códigos invariantes ISO (International Standards Organization). Los trígrafos son secuencias de tres caracteres (introducidos por dos signos de interrogación consecutivos) que el compilador reemplaza por sus caracteres de puntuación correspondientes. Puede usar trígrafos en los archivos de código fuente C con un juego de caracteres que no contenga representaciones gráficas adecuadas para algunos caracteres de puntuación.  
  
 C++17 quita trígrafos del idioma. Puede que las implementaciones sigan admitiendo trígrafos como parte de la asignación definida por la implementación del archivo físico de código fuente al *juego básico de caracteres de código fuente*, aunque la norma promueve que las implementaciones no lo hagan. A través de C++14, se admiten trígrafos como en C.  
  
 Visual C++ sigue admitiendo la sustitución de trígrafos, pero está deshabilitada de forma predeterminada. Para obtener información sobre cómo habilitar la sustitución de trígrafos, consulte [/Zc:trigraphs (Sustitución de trígrafos)](../build/reference/zc-trigraphs-trigraphs-substitution.md).  
  
 En la tabla siguiente se muestran nueve secuencias de trígrafos. Todas las apariciones en un archivo de código fuente de los caracteres de puntuación de la primera columna se reemplazan por el carácter correspondiente de la segunda columna.  
  
### <a name="trigraph-sequences"></a>Secuencias de trígrafos  
  
|Trígrafo|Carácter de puntuación|  
|--------------|---------------------------|  
|??=|#|  
|??(|[|  
|??/|\|  
|??)|]|  
|??'|^|  
|??\<|{|  
|??!|&#124;|  
|??>|}|  
|??-|~|  
  
 Un trígrafo siempre se trata como un único carácter de origen. La traducción de los trígrafos se produce en la primera [fase de traducción](../preprocessor/phases-of-translation.md), antes del reconocimiento de caracteres de escape en literales de cadena y constantes de caracteres. Solo se reconocen los nueve trígrafos mostrados en la tabla anterior. El resto de las secuencias de caracteres se quedan sin traducir.  
  
 La secuencia de escape de caracteres, **\\?**, evita la interpretación incorrecta de secuencias de caracteres que se parecen a un trígrafo. (Para obtener más información sobre las secuencias de escape, consulte [Secuencias de escape](../c-language/escape-sequences.md)). Por ejemplo, si intenta imprimir la cadena `What??!` con esta instrucción `printf`  
  
```  
printf( "What??!\n" );  
```  
  
 la cadena impresa es `What|` porque `??!` es una secuencia de trígrafos que se reemplaza por el carácter `|`. Escriba la instrucción de la forma siguiente para imprimir correctamente la cadena:  
  
```  
printf( "What?\?!\n" );  
```  
  
 En esta instrucción `printf`, un carácter de escape de barra diagonal inversa delante del segundo signo de interrogación evita la interpretación incorrecta de `??!` como trígrafo.  
  
## <a name="see-also"></a>Vea también  
 [/Zc (Sustitución de trígrafos)](../build/reference/zc-trigraphs-trigraphs-substitution.md)   
 [Identificadores de C](../c-language/c-identifiers.md)