---
title: "EOF, WEOF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EOF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EOF (función)"
  - "WEOF (función)"
  - "final de archivo"
ms.assetid: a7150563-cdae-4cdf-9798-ad509990e505
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# EOF, WEOF
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <stdio.h>  
```  
  
## Comentarios  
 EOF es devuelto por una rutina de E\/S cuando se encuentra el fin de archivo \(o en algunos casos, un error\).  
  
 WEOF hace que el valor devuelto, de **wint\_t**escrito, utilizado para indicar el final de una secuencia de ancho, o para designar una condición de error.  
  
## Vea también  
 [putc, putwc](../c-runtime-library/reference/putc-putwc.md)   
 [ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [fflush](../c-runtime-library/reference/fflush.md)   
 [fclose, \_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_ungetch, \_ungetwch, \_ungetch\_nolock, \_ungetwch\_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)   
 [\_putch, \_putwch](../c-runtime-library/reference/putch-putwch.md)   
 [isascii, \_\_isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)