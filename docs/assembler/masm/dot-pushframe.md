---
title: ".PUSHFRAME | Microsoft Docs"
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
  - ".PUSHFRAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".PUSHFRAME directive"
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .PUSHFRAME
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera `UWOP_PUSH_MACHFRAME` desenredado entrada de código.  Si se especifica `code` opcional, la entrada de código de desenredo se concede un modificador de 1.  De lo contrario, el modificador es 0.  
  
## Sintaxis  
  
```  
.PUSHFRAME [code]  
```  
  
## Comentarios  
 .PUSHFRAME Permite a los usuarios de ml64.exe especifican cómo una función de cuadro desenredo y sólo se permite en el prólogo, que extiende de declaración FRAME de [PROC](../../assembler/masm/proc.md) a la directiva de [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) .  estas directivas no generan código; generan solo `.xdata` y `.pdata`.  .PUSHFRAME Deben ir precedidas por las instrucciones que implementan realmente acciones para ser desenrollado.  Es aconsejable ajustar las directivas de desenredo y el código que está pensada desenrede en una macro para garantizar el contrato.  
  
 Para obtener más información, vea [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)