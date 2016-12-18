---
title: "Macros de MASM | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Macros de MASM
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para simplificar el uso de las [Pseudoperaciones sin formato](../build/raw-pseudo-operations.md), existe un conjunto de macros, definidas en ksamd64.inc, que se pueden usar para crear prólogos y epílogos típicos de procedimientos.  
  
## Comentarios  
  
|Macro|Descripción|  
|-----------|-----------------|  
|alloc\_stack\(n\)|Asigna un marco de pila de n bytes \(utilizando sub rsp, n\) y emite la información de desenredo apropiada \(.allocstack n\)|  
|save\_reg registro, ubicación|Guarda un registro del registro no variable en la pila en la ubicación de desplazamiento de RSP y emite la información de desenredo apropiada.  \(.savereg registro, ubicación\)|  
|push\_reg registro|Inserta un registro del registro no variable en la pila y emite la información de desenredo apropiada.  \(.pushreg registro\)|  
|rex\_push\_reg registro|Guarde un registro permanente en la pila mediante una inserción de 2 bytes, y emite el adecuado desenreda la información \(registro\) de .pushreg This debe usarse si la inserción es la primera instrucción de la función para asegurarse de que la función es activo \- patchable.|  
|save\_xmm128 registro, ubicación|Guarda un registro del registro XMM no variable en la pila en la ubicación de desplazamiento de RSP y emite la información de desenredo apropiada \(.savexmm128 registro, ubicación\)|  
|set\_frame registro, desplazamiento|Establece el registro del registro de marco como RSP \+ desplazamiento \(mediante mov o lea\) y emite la información de desenredo apropiada \(.set\_frame registro, desplazamiento\)|  
|push\_eflags|Inserta eflags con una instrucción pushfq y emite la información de desenredo apropiada \(.alloc\_stack 8\)|  
  
 Este es un ejemplo de prólogo de función con uso apropiado de las macros:  
  
```  
SkFrame struct   
Fill    dq ?; fill to 8 mod 16   
SavedRdi dq ?; saved register RDI   
SavedRsi dq ?; saved register RSI   
SkFrame ends  
  
sampleFrame struct  
Filldq?; fill to 8 mod 16  
SavedRdidq?; Saved Register RDI   
SavedRsi  dq?; Saved Register RSI  
sampleFrame ends  
  
sample2 PROC FRAME  
alloc_stack(sizeof sampleFrame)  
save_reg rdi, sampleFrame.SavedRdi  
save_reg rsi, sampleFrame.SavedRsi  
.end_prolog  
  
; function body  
  
mov rsi, sampleFrame.SavedRsi[rsp]  
mov rdi, sampleFrame.SavedRdi[rsp]  
  
; Here’s the official epilog  
  
add rsp, (sizeof sampleFrame)  
ret  
sample2 ENDP  
```  
  
## Vea también  
 [Aplicaciones auxiliares de desenredo para MASM](../build/unwind-helpers-for-masm.md)