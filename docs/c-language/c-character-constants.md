---
title: "Constantes de caracteres de C | Microsoft Docs"
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
  - "(') comilla simple"
  - "caracteres, constantes"
  - "constantes, caracteres"
  - "comilla simple"
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Constantes de caracteres de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una “constante de carácter” se forma agregando un carácter individual del juego de caracteres que se puede representar dentro de comillas sencillas \(**' '**\).  Las constantes de caracteres se utilizan para representar los caracteres del [juego de caracteres de la ejecución](../c-language/execution-character-set.md).  
  
## Sintaxis  
 *character\-constant*:  
 **'** *c\-char\-sequence* **'**  
  
 **L'** *c\-char\-sequence* **'**  
  
 *c\-char\-sequence*:  
 *c\-char*  
  
 *c\-char\-sequence c\-char*  
  
 *c\-char*:  
 Cualquier miembro del juego de caracteres de origen, excepto la comilla simple \(**'**\), la barra diagonal inversa \(**\\**\) o el carácter de nueva línea  
  
 *escape\-sequence*  
  
 *escape\-sequence*:  
 *simple\-escape\-sequence*  
  
 *octal\-escape\-sequence*  
  
 *hexadecimal\-escape\-sequence*  
  
 *simple\-escape\-sequence*: uno de  
 **\\a \\b \\f \\n \\r \\t \\v**  
  
 **\\' \\" \\\\ \\?**  
  
 *octal\-escape\-sequence*:  
 **\\**  *octal\-digit*  
  
 **\\**  *octal\-digit octal\-digit*  
  
 **\\**  *octal\-digit octal\-digit octal\-digit*  
  
 *hexadecimal\-escape\-sequence*:  
 **\\x**  *hexadecimal\-digit*  
  
 *hexadecimal\-escape\-sequence hexadecimal\-digit*  
  
## Vea también  
 [Constantes de C](../c-language/c-constants.md)