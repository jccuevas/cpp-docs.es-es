---
title: "Constantes del modo de traducci&#243;n | Microsoft Docs"
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
  - "_O_BINARY"
  - "_O_TEXT"
  - "_O_RAW"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_O_BINARY (constante)"
  - "_O_RAW (constante)"
  - "_O_TEXT (constante)"
  - "O_BINARY (constante)"
  - "O_RAW (constante)"
  - "O_TEXT (constante)"
  - "constantes de traducción"
  - "modos de traducción (E/S de archivo)"
  - "traslación, constantes"
  - "traslación, modos"
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Constantes del modo de traducci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <fcntl.h>  
  
```  
  
## Comentarios  
 `_O_BINARY` y las constantes del manifiesto de `_O_TEXT` determinan el de modalidad de traducción para archivos \(`_open` y `_sopen`\) o el de modalidad de traducción para las secuencias \(`_setmode`\).  
  
 Los valores permitidos son:  
  
 `_O_TEXT`  
 Archivo de Abrir en modo de texto \(traducido\).  Retorno de carro – combinaciones de avance de línea \(CR\-LF\) se convierten en un solo avance de línea \(LF\) en entrada.  Los caracteres de avance de línea se convierten en combinaciones de CR\-LF en la salida.  Además, CTRL\+Z se interpreta como carácter de final de archivo en la entrada.  En archivos abierto para lectura y lectura\/escritura, comprobaciones de `fopen` CTRL\+Z al final del archivo y colóquelo, si es posible.  Se hace esto porque usar las funciones de `fseek` y de `ftell` para desplazarse dentro de un final de archivo con CTRL\+Z puede hacer `fseek` para comportarse incorrectamente cerca del final del archivo.  
  
 `_O_BINARY`  
 Archivo de Abrir en modo \(sin traducir\) binario.  Se suprimen las conversiones anteriores.  
  
 `_O_RAW`  
 Igual que `_O_BINARY`.  Se admite para la compatibilidad de C 2,0.  
  
 Para obtener más información, vea [E\/S de archivo de texto y el modo binario](../c-runtime-library/text-and-binary-mode-file-i-o.md) y [Traducción de archivo](../c-runtime-library/file-translation-constants.md).  
  
## Vea también  
 [\_open, \_wopen](../c-runtime-library/reference/open-wopen.md)   
 [\_pipe](../c-runtime-library/reference/pipe.md)   
 [\_sopen, \_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [\_setmode](../c-runtime-library/reference/setmode.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)