---
title: "Texto y cadenas en Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "caracteres ASCII [C++]"
  - "juegos de caracteres [C++]"
  - "juegos de caracteres [C++], acerca de los juegos de caracteres"
  - "juegos de caracteres [C++], no europeos"
  - "globalización [C++]"
  - "globalización [C++], juegos de caracteres"
  - "aplicaciones internacionales [C++], acerca de las aplicaciones internacionales"
  - "caracteres japoneses [C++]"
  - "compatibilidad con caracteres Kanji [C++]"
  - "juegos de caracteres locales [C++]"
  - "localización [C++]"
  - "localización [C++], juegos de caracteres"
  - "MBCS [C++], programación internacional"
  - "compatibilidad con varios lenguajes [C++]"
  - "juego de caracteres no europeos [C++]"
  - "portabilidad [C++]"
  - "portabilidad [C++], juegos de caracteres"
  - "programación [C++], internacionales"
  - "traducir código [C++]"
  - "traducción [C++], juegos de caracteres"
  - "Unicode [C++]"
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
caps.latest.revision: 12
caps.handback.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Texto y cadenas en Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un aspecto importante en el desarrollo de aplicaciones para los mercados internacionales es la representación apropiada de los juegos de caracteres locales.  El juego de caracteres ASCII define los caracteres que están en el intervalo de 0x00 a 0x7F.  Hay otros juegos de caracteres, principalmente europeos, que definen los caracteres que están en el intervalo de 0x00 a 0x7F, al igual que el juego de caracteres ASCII, y que también definen un juego de caracteres extendidos de 0x80 a 0xFF.  De este modo, un juego de caracteres de un solo byte \(SBCS\) de 8 bits es suficiente para representar el juego de caracteres ASCII, así como los juegos de caracteres de la mayoría de idiomas europeos.  Sin embargo, algunos juegos de caracteres no europeos, como los caracteres Kanji del japonés, incluyen muchos más caracteres de los que puede representar un esquema de codificación de un solo byte y, por consiguiente, requieren una codificación de juego de caracteres multibyte \(MBCS\).  
  
## En esta sección  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)  
 Describe la compatibilidad de Visual C\+\+ con la programación mediante Unicode y MBCS.  
  
 [Compatibilidad con Unicode](../text/support-for-unicode.md)  
 Describe Unicode, que es una especificación para admitir todos los juegos de caracteres, incluidos los juegos de caracteres que no pueden representarse en un solo byte.  
  
 [Compatibilidad con los juegos de caracteres multibyte \(MBCS\)](../text/support-for-multibyte-character-sets-mbcss.md)  
 Describe MBCS, que es una alternativa a Unicode para la compatibilidad con juegos de caracteres, como el japonés y el chino, que no pueden representarse en un solo byte.  
  
 [Asignaciones de texto genérico en TCHAR.H](../Topic/Generic-Text%20Mappings%20in%20Tchar.h.md)  
 Proporciona las asignaciones de texto genérico específicas de Microsoft para muchos tipos de datos, rutinas y demás objetos.  
  
 [Cómo: Convertir entre distintos tipos de cadenas](../Topic/How%20to:%20Convert%20Between%20Various%20String%20Types.md)  
 Muestra cómo se convierten distintos tipos de cadenas de Visual C\+\+ en otras cadenas.  
  
## Secciones relacionadas  
 [Internacionalización](../c-runtime-library/internationalization.md)  
 Describe la compatibilidad internacional en la biblioteca en tiempo de ejecución de C.  
  
 [Ejemplos de programación internacional](http://msdn.microsoft.com/es-es/aa8d390c-cf4c-4dd8-9dea-74d81f93f2f8)  
 Proporciona vínculos a ejemplos en los que se muestra la internacionalización en Visual C\+\+.  
  
 [Cadenas de idioma de país o región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
 Proporciona las cadenas de idioma y de país o región en la biblioteca en tiempo de ejecución de C.