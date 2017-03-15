---
title: "Juegos de caracteres de un solo byte y de varios bytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.character.multibyte"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "juegos de caracteres [C++], multibyte"
  - "juegos de caracteres [C++], un solo byte"
  - "MBCS [C++], acerca de MBCS"
  - "SBCS (juego de caracteres de un solo byte)"
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Juegos de caracteres de un solo byte y de varios bytes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El juego de caracteres ASCII define los caracteres del intervalo de 0x00 a 0x7F.  Hay otros juegos de caracteres, principalmente europeos, que definen los caracteres dentro del intervalo de 0x00 a 0x7F exactamente igual que el juego de caracteres ASCII y también define un juego de caracteres extendidos de 0x80 – 0xFF.  Así un de 8 bits, juego de caracteres de byte único \(`SBCS`\) es suficiente para representar el juego de caracteres ASCII así como los juegos de caracteres de muchos idiomas europeos.  Sin embargo, algunos juegos de caracteres no europeos, como los caracteres Kanji del japonés, incluyen muchos más caracteres que se puede representar en un esquema de codificación de solo\- byte, y por consiguiente requieren la codificación del juego de caracteres multibyte \(`MBCS`\).  
  
> [!NOTE]
>  Muchas rutinas de `SBCS` en la biblioteca en tiempo de ejecución de Microsoft controlan bytes, caracteres, y las cadenas multibyte según corresponda.  Muchos juegos de caracteres multibyte definen el juego de caracteres ASCII como un subconjunto.  En muchos juegos de caracteres multibyte, cada uno de los caracteres que está en el intervalo de 0x00 a 0x7F es idéntico al carácter que tiene el mismo valor en el juego de caracteres ASCII.  Por ejemplo, en `ASCII` y las cadenas de caracteres `MBCS` , el carácter de `NULL` de uno\- byte \(“\\0”\) tiene el valor 0x00 e indica el carácter null de terminación.  
  
 Un juego de caracteres multibyte puede ser el uno\- bytes y caracteres de dos bytes.  Así una cadena de multibyte\- carácter puede contener una combinación de solo\- byte y de caracteres de doble byte.  Un carácter de dos bytes multibyte tiene un byte inicial y un byte final.  En un juego de caracteres multibyte específico, los bytes iniciales quedan dentro de un intervalo determinado, al igual que los bytes finales.  Si estos intervalos se superponen, puede ser necesario evaluar el contexto determinado para determinar si un byte específico funciona como un byte inicial o un byte final.  
  
## Vea también  
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)