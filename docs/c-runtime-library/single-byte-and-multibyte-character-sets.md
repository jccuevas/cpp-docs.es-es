---
title: Juegos de caracteres de un solo byte y de varios bytes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
ms.workload:
- cplusplus
ms.openlocfilehash: 1d6c339f1ab2eecfac5f037e711f19d5ee9323fc
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="single-byte-and-multibyte-character-sets"></a>Juegos de caracteres de un solo byte y de varios bytes

El juego de caracteres ASCII define los caracteres que están en el intervalo de 0x00 a 0x7F. Hay otros juegos de caracteres, principalmente europeos, que definen los caracteres que están en el intervalo de 0x00 a 0x7F, al igual que el juego de caracteres ASCII, y que también definen un juego de caracteres extendidos de 0x80 a 0xFF. De este modo, un juego de caracteres de byte único (SBCS) de 8 bits es suficiente para representar el juego de caracteres ASCII, así como los juegos de caracteres de la mayoría de idiomas europeos. En cambio, algunos juegos de caracteres no europeos, como los caracteres Kanji del japonés, incluyen muchos más caracteres de los que se pueden representar en un esquema de codificación de byte único y, por consiguiente, requieren una codificación de juego de caracteres multibyte (MBCS).

> [!NOTE]
> Muchas rutinas de SBCS en la biblioteca en tiempo de ejecución de Microsoft controlan bytes, caracteres y cadenas multibyte según corresponda. Muchos juegos de caracteres de varios bytes definen el juego de caracteres ASCII como un subconjunto. En muchos juegos de caracteres de varios bytes, cada uno de los caracteres que está en el intervalo de 0x00 a 0x7F es idéntico al carácter que tiene el mismo valor en el juego de caracteres ASCII. Por ejemplo, tanto en las cadenas de caracteres ASCII como en las MBCS, el carácter NULL de un byte ('\0') tiene el valor 0x00 e indica el carácter final nulo.

Un juego de caracteres de varios bytes puede constar de caracteres de un byte y de dos bytes. Por lo tanto, una cadena de caracteres de varios bytes puede contener una mezcla de caracteres de un solo byte y de doble byte. Un carácter multibyte de dos bytes tiene un byte inicial y un byte final. En un juego de caracteres multibyte específico, los bytes iniciales quedan dentro de un intervalo determinado, al igual que los bytes finales. Si estos intervalos se superponen, puede que sea necesario evaluar el contexto concreto para determinar si un byte específico funciona como byte inicial o como byte final.

## <a name="see-also"></a>Vea también

[Internacionalización](../c-runtime-library/internationalization.md)<br/>
[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
