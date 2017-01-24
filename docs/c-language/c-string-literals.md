---
title: "Literales de cadena de C | Microsoft Docs"
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
  - "cadenas literales, C"
  - "literales de cadena, sintaxis"
  - "cadenas [C++], literales de cadena"
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Literales de cadena de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un “literal de cadena” es una secuencia de caracteres del juego de caracteres de origen incluida entre comillas dobles \(**" "**\).  Los literales de cadena se utilizan para representar una secuencia de caracteres que, en conjunto, forman una cadena terminada en null.  Siempre debe agregar como prefijo la letra **L** a los literales de cadena anchos.  
  
## Sintaxis  
 *string\-literal*:  
 **"** *s\-char\-sequence*  opt               **"**  
  
 **L"** *s\-char\-sequence*  opt               **"**  
  
 *s\-char\-sequence*:  
 *s\-char*  
  
 *s\-char\-sequence s\-char*  
  
 *s\-char*:  
 cualquier miembro del juego de caracteres de origen excepto las comillas dobles \("\), la barra diagonal inversa \(\\\) o el carácter de nueva línea  
  
 *escape\-sequence*  
  
 El ejemplo siguiente es un literal de cadena simple:  
  
```  
char *amessage = "This is a string literal.";  
```  
  
 Todos los códigos de escape mostrados en la tabla [Secuencias de escape](../c-language/escape-sequences.md) son válidos en literales de cadena.  Para representar un carácter de dobles comillas en un literal de cadena, utilice la secuencia de escape **\\"**.  El carácter de comilla simple \(**'**\) se puede representar sin una secuencia de escape.  La barra diagonal inversa \(**\\**\) deben ir seguida de una segunda barra diagonal inversa \(**\\\\**\) cuando aparece dentro de una cadena.  Cuando una barra diagonal inversa aparece al final de una línea, se interpreta siempre como un carácter de continuación de línea.  
  
## Vea también  
 [Elementos de C](../c-language/elements-of-c.md)