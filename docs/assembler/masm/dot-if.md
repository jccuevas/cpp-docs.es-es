---
title: ".IF | Microsoft Docs"
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
  - ".IF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".IF directive"
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .IF
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera el código prueba `condition1` \(por ejemplo, el AX \> 7\) y ejecuta *las instrucciones* si la condición es true.  
  
## Sintaxis  
  
```  
  
   .IF condition1   
statements  
[[.ELSEIF condition2   
   statements]]  
[[.ELSE  
   statements]]  
.ENDIF  
```  
  
## Comentarios  
 Si [.ELSE](../../assembler/masm/dot-else.md) sigue, se ejecutan las instrucciones si la condición original sea false.  Observe que las condiciones se evalúa en tiempo de ejecución.  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)