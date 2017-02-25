---
title: "COMM | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COMM"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COMM directive"
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# COMM
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

crea una variable comunal con los atributos especificados en `definition`.  
  
## Sintaxis  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## Comentarios  
 Cada `definition` tiene el siguiente formato:  
  
 \[\[*langtype*\]\] \[\[**NEAR** &#124; *etiqueta***:**`type`de**FAR**\]\] \[\[*recuento de***:**\]\]  
  
 *la etiqueta* es el nombre de la variable.  `type` puede ser cualquier especificador de tipo \([Byte](../../assembler/masm/byte-masm.md), [word](../../assembler/masm/word.md), etc.\) o un entero que especifica el número de bytes.  *El recuento* especifica el número de objetos de datos \(uno es el valor predeterminado\).  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)