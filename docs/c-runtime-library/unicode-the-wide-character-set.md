---
title: "Unicode: el juego de caracteres anchos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.international"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "Unicode [C++], juego de caracteres anchos"
  - "caracteres anchos [C++], Unicode"
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Unicode: el juego de caracteres anchos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un carácter ancho es un código de carácter multilingüe de 2 bytes.  Cualquier carácter en uso en la informática moderna en todo el mundo, incluidos símbolos técnicos y caracteres especiales de publicación, se puede representar como la especificación Unicode como un carácter ancho.  Convierte y mantenido por un consorcio grande que incluye Microsoft, el estándar Unicode ahora se acepta ampliamente.  
  
 Un carácter ancho es de `wchar_t`escrito.  Una cadena de caracteres se representa como una matriz de `wchar_t[]` y se señala por un puntero de `wchar_t*` .  Puede representar cualquier carácter ASCII como un carácter ancho anteponiendo la letra `L` al carácter.  Por ejemplo, L'\\0 es el carácter \(16 bits\) ancho de `NULL` que finaliza.  De igual forma, puede representar un literal de cadena ASCII como literal de cadena de caracteres simplemente anteponiendo la letra l al literal ASCII \(l " Hello”\).  
  
 Normalmente, los caracteres anchos ocupan más espacio de memoria que los caracteres multibyte pero son más rapidez.  Además, sólo se puede representar una configuración regional a la vez en la codificación multibyte, mientras que todos los juegos de caracteres del mundo están representados de forma simultánea por la representación de Unicode.  
  
## Vea también  
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)