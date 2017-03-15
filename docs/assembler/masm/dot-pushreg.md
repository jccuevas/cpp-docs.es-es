---
title: ".PUSHREG | Microsoft Docs"
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
  - ".PUSHREG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".PUSHREG directive"
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .PUSHREG
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera `UWOP_PUSH_NONVOL` desenreda la entrada del número especificado de registro mediante el desplazamiento actual en el prólogo.  
  
## Sintaxis  
  
```  
.PUSHREG register  
```  
  
## Comentarios  
 .PUSHREG Permite a los usuarios de ml64.exe especifican cómo una función de cuadro desenredo, y sólo se permite en el prólogo, que extiende de declaración FRAME de [PROC](../../assembler/masm/proc.md) a la directiva de [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) .  estas directivas no generan código; generan solo `.xdata` y `.pdata`.  .PUSHREG Deben ir precedidas por las instrucciones que implementan realmente acciones para ser desenrollado.  Es aconsejable ajustar las directivas de desenredo y el código que está pensada desenrede en una macro para garantizar el contrato.  
  
 Para obtener más información, vea [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## Ejemplo  
  
### Descripción  
 El ejemplo siguiente se muestra cómo insertar tegisters permanentes.  
  
### Código  
  
```  
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE  
_text SEGMENT  
Example1 PROC FRAME  
   push r10  
.pushreg r10  
   push r15  
.pushreg r15  
   push rbx  
.pushreg rbx  
   push rsi  
.pushreg rsi  
.endprolog  
   ; rest of function ...  
   ret  
Example1 ENDP  
_text ENDS  
END  
```  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)