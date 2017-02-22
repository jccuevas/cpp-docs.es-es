---
title: "IF (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IF directive"
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# IF (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Concede al ensamblado *de ifstatements* si *expression1* es true \(cero\) o *elseifstatements* si *expression1* es false \(0\) y *expression2* es true.  
  
## Sintaxis  
  
```  
  
   IF expression1  
ifstatements  
[[ELSEIF expression2  
   elseifstatements]]  
[[ELSE  
   elsestatements]]  
ENDIF  
```  
  
## Comentarios  
 Las siguientes directivas se pueden sustituir por [ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **ELSEIFDEF**, **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**, y **ELSEIFNDEF**.  Opcionalmente, ensambla *elsestatements* si la expresión anterior es false.  Observe que las expresiones se evalúa en tiempo de ensamblado.  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)