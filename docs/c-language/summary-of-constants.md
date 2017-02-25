---
title: "Resumen de constantes | Microsoft Docs"
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
  - "constantes, C"
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Resumen de constantes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`constant`:  
 *floating\-point\-constant*  
  
 *integer\-constant*  
  
 *enumeration\-constant*  
  
 *character\-constant*  
  
 *floating\-point\-constant*:  
 *fractional\-constant exponent\-part*  opt *floating\-suffix* opt  
  
 *digit\-sequence exponent\-part floating\-suffix*  opt  
  
 *fractional\-constant*:  
 *digit\-sequence*  opt **.***digit\-sequence*  
  
 *digit\-sequence*  **.**  
  
 *exponent\-part*:  
 **e**  *sign*  opt *digit\-sequence*  
  
 **E**  *sign*  opt *digit\-sequence*  
  
 *sign*: uno de  
 **\+ –**  
  
 *digit\-sequence*:  
 *digit*  
  
 *digit\-sequence digit*  
  
 *floating\-suffix*: uno de  
 **f l F L**  
  
 *integer\-constant*:  
 *decimal\-constant integer\-suffix*  opt  
  
 *octal\-constant integer\-suffix*  opt  
  
 *hexadecimal\-constant integer\-suffix*  opt  
  
 *decimal\-constant*:  
 *nonzero\-digit*  
  
 *decimal\-constant digit*  
  
 *octal\-constant*:  
 **0**  
  
 *octal\-constant octal\-digit*  
  
 *hexadecimal\-constant*:  
 **0x**  *hexadecimal\-digit*  
  
 **0X**  *hexadecimal\-digit*  
  
 *hexadecimal\-constant hexadecimal\-digit*  
  
 *nonzero\-digit*: uno de  
 **1 2 3 4 5 6 7 8 9**  
  
 *octal\-digit*: uno de  
 **0 1 2 3 4 5 6 7**  
  
 *hexadecimal\-digit*: uno de  
 **0 1 2 3 4 5 6 7 8 9**  
  
 **a b c d e f**  
  
 **A B C D E F**  
  
 *unsigned\-suffix*: uno de  
 **u U**  
  
 *long\-suffix*: uno de  
 **l L**  
  
 *character\-constant*:  
 **'** *c\-char\-sequence*  
  
 **'L'** *c\-char\-sequence* **'**  
  
 *integer\-suffix*:  
 *unsigned\-suffix long\-suffix*  opt  
  
 *long\-suffix unsigned\-suffix*  opt  
  
 *c\-char\-sequence*:  
 *c\-char*  
  
 *c\-char\-sequence c\-char*  
  
 *c\-char*:  
 Cualquier miembro del juego de caracteres de origen excepto la comilla simple \('\), la barra diagonal inversa \(**\\**\) o el carácter de nueva línea *escape\-sequence*  
  
 *escape\-sequence*:  
 *simple\-escape\-sequence*  
  
 *octal\-escape\-sequence*  
  
 *hexadecimal\-escape\-sequence*  
  
 *simple\-escape\-sequence*: uno de  
 **\\a \\b \\f \\n \\r \\t \\v**  
  
 **\\' \\" \\\\ \\?**  
  
 *octal\-escape\-sequence*:  
 **\\** *octal\-digit*  
  
 **\\** *octal\-digit octal\-digit*  
  
 **\\** *octal\-digit octal\-digit octal\-digit*  
  
 *hexadecimal\-escape\-sequence*:  
 **\\x**  *hexadecimal\-digit*  
  
 *hexadecimal\-escape\-sequence hexadecimal\-digit*  
  
## Vea también  
 [Gramática léxica](../c-language/lexical-grammar.md)