---
title: 'Unicode: el juego de caracteres anchos | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46702f9ea91c9cbba7f7ddbaadc23de88d80fe9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-the-wide-character-set"></a>Unicode: el juego de caracteres anchos
Un carácter ancho es un código de carácter multilingüe de dos bytes. Todos los caracteres usados en la informática moderna alrededor del mundo, como los símbolos técnicos o los caracteres de publicación especiales, se pueden representar de acuerdo con la especificación Unicode en forma de carácter ancho. La norma Unicode cuenta con un amplio reconocimiento, de cuyo desarrollo y mantenimiento se encarga un gran consorcio que incluye a Microsoft.  
  
 Un carácter ancho es de tipo `wchar_t`. Una cadena de caracteres anchos se representa como una matriz `wchar_t[]` y apunta a ella un puntero `wchar_t*`. Cualquier carácter ASCII se puede representar como un carácter ancho anteponiéndole la letra `L` como prefijo. Por ejemplo, L'\0' es el carácter `NULL` ancho (de 16 bits) de terminación. De manera similar, cualquier literal de cadena ASCII se puede representar como un literal de cadena de caracteres anchos con tan solo anteponer la letra L como prefijo del literal ASCII (L"Hola").  
  
 En general, los caracteres anchos ocupan más espacio en la memoria que los caracteres multibyte, pero se procesan más rápido. Además, en la codificación multibyte no se pueden representar varias configuraciones regionales a la vez, mientras que la representación de Unicode representa simultáneamente a todos los juegos de caracteres del mundo.  
  
## <a name="see-also"></a>Vea también  
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)