---
title: "INSTR | Microsoft Docs"
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
  - "InStr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "INSTR directive"
ms.assetid: fc37f6a2-3c95-47b2-b6bb-1066edd25994
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# INSTR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

encuentra la primera aparición de *textitem2* en *textitem1*.  
  
## Sintaxis  
  
```  
  
name  
 INSTR [[position,]] textitem1, textitem2  
```  
  
## Comentarios  
 *La posición* inicial es opcional.  Cada elemento de texto puede ser una cadena literal, una constante precedida por `%`, o la cadena devuelta por una función de macro.  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)