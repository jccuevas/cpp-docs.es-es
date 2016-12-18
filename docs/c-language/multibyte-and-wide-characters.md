---
title: "Caracteres anchos y multibyte | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "códigos de caracteres [C++], multibyte"
  - "códigos de caracteres [C++], anchos"
  - "tipos de datos de caracteres [C]"
  - "caracteres [C++], códigos"
  - "caracteres [C++], anchos"
  - "globalización [C++], juegos de caracteres"
  - "aplicaciones internacionales [C++], presentación de caracteres"
  - "caracteres multibyte [C++]"
  - "tipos [C], caracteres"
  - "Unicode [C++], juego de caracteres anchos"
  - "caracteres anchos [C++]"
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Caracteres anchos y multibyte
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un carácter multibyte es un carácter compuesto por secuencias de uno o más bytes.  Cada secuencia de bytes representa un único carácter en el juego de caracteres extendidos.  Los caracteres multibyte se utilizan en juegos de caracteres tales como Kanji.  
  
 Los caracteres anchos son códigos de caracteres multilingües con un ancho invariable de 16 bits.  El tipo de las constantes de caracteres es `char`; para los caracteres anchos, el tipo es `wchar_t`.  Puesto que los caracteres anchos siempre son de tamaño fijo, con los caracteres anchos se simplifica la programación con juegos de caracteres internacionales.  
  
 El literal de cadena de carácter ancho `L"hello"` se convierte en una matriz de seis enteros de tipo `wchar_t`.  
  
```  
{L'h', L'e', L'l', L'l', L'o', 0}  
```  
  
 La especificación Unicode es la especificación de caracteres anchos.  Las rutinas de la biblioteca en tiempo de ejecución para traducir caracteres multibyte y anchos incluyen `mbstowcs`, `mbtowc`, `wcstombs` y `wctomb`.  
  
## Vea también  
 [Identificadores de C](../c-language/c-identifiers.md)