---
title: Juegos de caracteres de un solo byte y de varios bytes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.character.multibyte
dev_langs:
- C++
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: c7d9a62c2b6dc69f9fcd86c8f498e42ce31cae84
ms.lasthandoff: 04/01/2017

---
# <a name="single-byte-and-multibyte-character-sets"></a>Juegos de caracteres de un solo byte y de varios bytes
El juego de caracteres ASCII define los caracteres que están en el intervalo de 0x00 a 0x7F. Hay otros juegos de caracteres, principalmente europeos, que definen los caracteres que están en el intervalo de 0x00 a 0x7F, al igual que el juego de caracteres ASCII, y que también definen un juego de caracteres extendidos de 0x80 a 0xFF. De este modo, un juego de caracteres de un solo byte (`SBCS`) de 8 bits es suficiente para representar el juego de caracteres ASCII, así como los juegos de caracteres de la mayoría de idiomas europeos. En cambio, algunos juegos de caracteres no europeos, como los caracteres Kanji del japonés, incluyen muchos más caracteres que pueden representarse en un esquema de codificación de un solo byte y, por consiguiente, requieren una codificación de juego de caracteres multibyte (`MBCS`).  
  
> [!NOTE]
>  Muchas rutinas de `SBCS` en la biblioteca en tiempo de ejecución de Microsoft controlan cadenas, caracteres y uno o varios bytes según corresponda. Muchos juegos de caracteres de varios bytes definen el juego de caracteres ASCII como un subconjunto. En muchos juegos de caracteres de varios bytes, cada uno de los caracteres que está en el intervalo de 0x00 a 0x7F es idéntico al carácter que tiene el mismo valor en el juego de caracteres ASCII. Por ejemplo, tanto en las cadenas de caracteres `ASCII` como en las `MBCS`, el carácter `NULL` de un byte ("\0") tiene el valor 0x00 e indica el carácter final nulo.  
  
 Un juego de caracteres de varios bytes puede constar de caracteres de un byte y de dos bytes. Por lo tanto, una cadena de caracteres de varios bytes puede contener una mezcla de caracteres de un solo byte y de doble byte. Un carácter multibyte de dos bytes tiene un byte inicial y un byte final. En un juego de caracteres multibyte específico, los bytes iniciales quedan dentro de un intervalo determinado, al igual que los bytes finales. Si estos intervalos se superponen, puede que sea necesario evaluar el contexto concreto para determinar si un byte específico funciona como byte inicial o como byte final.  
  
## <a name="see-also"></a>Vea también  
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)
