---
title: "Tipos de caracteres | Microsoft Docs"
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
  - "tipos de datos de caracteres [C]"
  - "tipos [C], caracteres"
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Tipos de caracteres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una constante de caracteres entera no precedida por la letra **L** tiene el tipo `int`.  El valor de una constante de caracteres entera que contiene un carácter individual es el valor numérico del carácter interpretado como un entero.  Por ejemplo, el valor numérico del carácter `a` es 97 en decimal y 61 en hexadecimal.  
  
 Sintácticamente, una "constante de caracteres anchos" es una constante de caracteres que tienen como prefijo la letra **L**.  Una constante de caracteres anchos es de tipo `wchar_t`, un tipo entero definido en el archivo de encabezado STDDEF.H.  Por ejemplo:  
  
```  
char    schar =  'x';   /* A character constant          */  
wchar_t wchar = L'x';   /* A wide-character constant for   
                            the same character           */  
```  
  
 Las constantes de caracteres anchos tienen 16 bits de ancho y especifican miembros del juego de caracteres de ejecución extendidos.  Permiten expresar caracteres en los alfabetos demasiado grandes para representarlos mediante el tipo `char`.  Vea [Caracteres multibyte y anchos](../c-language/multibyte-and-wide-characters.md) para obtener más información sobre los caracteres anchos.  
  
## Vea también  
 [Constantes de caracteres de C](../c-language/c-character-constants.md)