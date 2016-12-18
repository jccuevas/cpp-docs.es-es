---
title: ".SAVEXMM128 | Microsoft Docs"
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
  - ".SAVEXMM128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".SAVEXMM128 directive"
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SAVEXMM128
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera o `UWOP_SAVE_XMM128` o `UWOP_SAVE_XMM128_FAR` desenreda la entrada del registro especificado de MMX y el desplazamiento mediante el desplazamiento actual de prólogo.  MASM elegirá la codificación más eficaz.  
  
## Sintaxis  
  
```  
.savexmm128 xmmreg , offset  
```  
  
## Comentarios  
 .SAVEXMM128 permite a los usuarios de ml64.exe especifican cómo una función de cuadro desenredo, y sólo se permite en el prólogo, que extiende de declaración FRAME de [PROC](../../assembler/masm/proc.md) a la directiva de [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) .  estas directivas no generan código; generan solo `.xdata` y `.pdata`.  .SAVEXMM128 deben ir precedidas por las instrucciones que implementan realmente acciones para ser desenrollado.  Es aconsejable ajustar las directivas de desenredo y el código que está pensada desenrede en una macro para garantizar el contrato.  
  
 `offset` debe ser un múltiplo de 16.  
  
 Para obtener más información, vea [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)