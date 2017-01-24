---
title: ".ALLOCSTACK | Microsoft Docs"
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
  - ".ALLOCSTACK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".ALLOCSTACK directive"
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .ALLOCSTACK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera **UWOP\_ALLOC\_SMALL** o **UWOP\_ALLOC\_LARGE** con el tamaño especificado para el desplazamiento actual en el prólogo.  
  
## Sintaxis  
  
```  
.ALLOCSTACK size  
```  
  
## Comentarios  
 MASM elegirá la codificación más eficaz para un tamaño determinado.  
  
 .ALLOCSTACK Permite a los usuarios de ml64.exe especifican cómo una función de cuadro desenredo y sólo se permite en el prólogo, que extiende de declaración FRAME de [PROCEDURE](../../assembler/masm/proc.md) a la directiva de [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) .  estas directivas no generan código; generan solo `.xdata` y `.pdata`.  .ALLOCSTACK Deben ir precedidas por las instrucciones que implementan realmente acciones para ser desenrollado.  Es aconsejable ajustar las directivas de desenredo y el código que está pensada desenrede en una macro para garantizar el contrato.  
  
 el operando de `size` debe ser un múltiplo de 8.  
  
 Para obtener más información, vea [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo especificar un desenredo y un controlador de excepciones:  
  
```  
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console  
text SEGMENT  
PUBLIC Example3  
PUBLIC Example3_UW  
Example3_UW PROC NEAR  
   ; exception/unwind handler body  
  
   ret 0  
  
Example3_UW ENDP  
  
Example3 PROC FRAME : Example3_UW  
  
   sub rsp, 16  
.allocstack 16  
  
.endprolog  
  
   ; function body  
    add rsp, 16  
   ret 0  
  
Example3 ENDP  
text ENDS  
END  
```  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)