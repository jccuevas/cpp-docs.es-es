---
title: "Tr&#237;grafos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "? símbolo, trígrafo"
  - "?? (trígrafo)"
  - "??' (trígrafo)"
  - "??- (trígrafo)"
  - "??! (trígrafo)"
  - "??) (trígrafo)"
  - "??/ (trígrafo)"
  - "??< (trígrafo)"
  - "??= (trígrafo)"
  - "??> (trígrafo)"
  - "signo de interrogación, en trígrafos"
  - "trígrafos"
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Tr&#237;grafos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El juego de caracteres de origen de programas de código fuente C está incluido dentro del juego de caracteres ASCII de 7 bits, pero es un superconjunto del conjunto de códigos invariantes ISO 646\-1983.  Las secuencias de trígrafos permiten escribir programas de C usando solo el conjunto de códigos invariantes ISO \(International Standards Organization\).  Los trígrafos son secuencias de tres caracteres \(introducidos por dos signos de interrogación consecutivos\) que el compilador reemplaza por sus caracteres de puntuación correspondientes.  Puede usar trígrafos en los archivos de código fuente C con un juego de caracteres que no contenga representaciones gráficas adecuadas para algunos caracteres de puntuación.  
  
 En la tabla siguiente se muestran nueve secuencias de trígrafos.  Todas las apariciones en un archivo de código fuente de los caracteres de puntuación de la primera columna se reemplazan por el carácter correspondiente de la segunda columna.  
  
### Secuencias de trígrafos  
  
|Trígrafo|Carácter de puntuación|  
|--------------|----------------------------|  
|??\=|\#|  
|??\(|\[|  
|??\/|\\|  
|??\)|\]|  
|??'|^|  
|??\<|{|  
|??\!|&#124;|  
|??\>|}|  
|??\-|~|  
  
 Un trígrafo siempre se trata como un único carácter de origen.  La traducción de los trígrafos tiene lugar en la primera [fase de traducción](../preprocessor/phases-of-translation.md), antes del reconocimiento de caracteres de escape en literales de cadena y constantes de caracteres.  Solo se reconocen los nueve trígrafos mostrados en la tabla anterior.  El resto de las secuencias de caracteres se quedan sin traducir.  
  
 La secuencia de escape de caracteres, **\\?**, evita la interpretación incorrecta de secuencias de caracteres que se parecen a un trígrafo. \(Para obtener más información acerca de las secuencias de escape, vea [Secuencias de escape](../c-language/escape-sequences.md)\). Por ejemplo, si intenta imprimir la cadena `What??!` con esta instrucción `printf`  
  
```  
printf( "What??!\n" );  
```  
  
 la cadena impresa es `What|` porque `??!` es una secuencia de trígrafos que se reemplaza por el carácter          `|` .  Escriba la instrucción de la forma siguiente para imprimir correctamente la cadena:  
  
```  
printf( "What?\?!\n" );  
```  
  
 En esta instrucción `printf`, un carácter de escape de barra diagonal inversa delante del segundo signo de interrogación evita la interpretación incorrecta de `??!` como trígrafo.  
  
## Vea también  
 [Identificadores de C](../c-language/c-identifiers.md)