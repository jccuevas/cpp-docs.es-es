---
title: "Tipo para literales de cadena | Microsoft Docs"
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
  - "literales de cadena, tipo"
  - "tipos [C], literales de cadena"
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Tipo para literales de cadena
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los literales de cadena tienen una matriz de tipos de `char` \(es decir, **char\[ \]**\). \(Las cadenas de caracteres anchos tienen una matriz de tipos de `wchar_t` \(es decir, **wchar\_t\[ \]**\)\). Esto significa que una cadena es una matriz con elementos de tipo `char`.  El número de elementos de la matriz es igual al número de caracteres de la cadena más una por el carácter NULL de terminación.  
  
## Vea también  
 [Literales de cadena de C](../c-language/c-string-literals.md)