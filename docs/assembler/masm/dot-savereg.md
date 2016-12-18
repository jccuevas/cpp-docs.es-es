---
title: ".SAVEREG | Microsoft Docs"
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
  - ".SAVEREG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".SAVEREG directive"
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SAVEREG
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera o `UWOP_SAVE_NONVOL` o `UWOP_SAVE_NONVOL_FAR` desenreda la entrada del registro especificado \(`reg`\) y el desplazamiento \(`offset`\) mediante el desplazamiento actual de prólogo.  MASM elegirá la codificación más eficaz.  
  
## Sintaxis  
  
```  
.SAVEREG reg, offset  
```  
  
## Comentarios  
 .SAVEREG Permite a los usuarios de ml64.exe especifican cómo una función de cuadro desenredo y sólo se permite en el prólogo, que extiende de declaración FRAME de [PROC](../../assembler/masm/proc.md) a la directiva de [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) .  estas directivas no generan código; generan solo `.xdata` y `.pdata`.  .SAVEREG Deben ir precedidas por las instrucciones que implementan realmente acciones para ser desenrollado.  Es aconsejable ajustar las directivas de desenredo y el código que está pensada desenrede en una macro para garantizar el contrato.  
  
 Para obtener más información, vea [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)