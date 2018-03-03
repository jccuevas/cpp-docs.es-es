---
title: Pseudoperaciones sin formato | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52ce7fb4455f87001bcfe87e1368ed0c09cda6b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="raw-pseudo-operations"></a>Pseudoperaciones sin formato
Este tema enumeran las operaciones de seudoprueba.  
  
## <a name="remarks"></a>Comentarios  
  
|Operación de pseudo|Descripción|  
|----------------------|-----------------|  
|MARCO de proceso [: ehandler]|Causas MASM para generar una función de tabla de entrada en .pdata e información de desenredo en .xdata para una función de la estructura comportamiento de desenredo del control de excepciones.  Si ehandler está presente, este procedimiento se escribe en .xdata como el controlador específico del lenguaje.<br /><br /> Cuando se utiliza el atributo FRAME, debe ir seguido por una. Directiva ENDPROLOG.  Si la función es una función de hoja (como se define en [tipos de función](../build/function-types.md)) el atributo FRAME es innecesario, igual que el resto de estas pseudoperaciones.|  
|. PUSHREG registro|Genera una entrada de código de desenredo UWOP_PUSH_NONVOL para el número de registro especificado mediante el desplazamiento actual en el prólogo.<br /><br /> Solo debe usarse con registros de enteros no volátil.  Para inserciones de registros variables, utilice una. ALLOCSTACK 8 en su lugar|  
|. SETFRAME registro, desplazamiento|Rellenos en el marco de registran el campo y el desplazamiento en la información de desenredo mediante el registro especificado y el desplazamiento. El desplazamiento debe ser un múltiplo de 16 y menor o igual que 240. Esta directiva también genera una entrada de código de desenredo UWOP_SET_FPREG para el registro especificado mediante el desplazamiento actual del prólogo.|  
|. ALLOCSTACK tamaño|Genera una entrada UWOP_ALLOC_SMALL o UWOP_ALLOC_LARGE con el tamaño especificado para el desplazamiento actual en el prólogo.<br /><br /> El operando del tamaño debe ser un múltiplo de 8.|  
|. SAVEREG registro, desplazamiento|Genera un UWOP_SAVE_NONVOL o una entrada de código de desenredado UWOP_SAVE_NONVOL_FAR para el registro especificado y el desplazamiento utilizando el desplazamiento actual del prólogo. MASM elegirá la codificación más eficaz.<br /><br /> Desplazamiento debe ser positivo y múltiplo de 8.  Desplazamiento es relativo a la base del marco del procedimiento, que suele ser en RSP, o bien, si utiliza un puntero de marco, el puntero de marco sin ajuste de escala.|  
|. Savexmm128 registro, desplazamiento|Genera un UWOP_SAVE_XMM128 o una entrada de código de desenredado UWOP_SAVE_XMM128_FAR para el registro de registros de XMM especificado y el desplazamiento utilizando el desplazamiento actual del prólogo. MASM elegirá la codificación más eficaz.<br /><br /> Desplazamiento debe ser positivo y a un múltiplo de 16.  Desplazamiento es relativo a la base del marco del procedimiento, que suele ser en RSP, o bien, si utiliza un puntero de marco, el puntero de marco sin ajuste de escala.|  
|. PUSHFRAME [código]|Genera una entrada de código de desenredo UWOP_PUSH_MACHFRAME. Si se especifica el código opcional, la entrada de código de desenredado tiene un modificador de 1. En caso contrario, el modificador es 0.|  
|.ENDPROLOG|Marca el final de las declaraciones del prólogo.  Se debe producir en los primeros 255 bytes de la función.|  
  
 Este es un ejemplo de prólogo de función con el uso correcto de la mayoría de los códigos de operación:  
  
```  
sample PROC FRAME     
   db      048h; emit a REX prefix, to enable hot-patching  
push rbp  
.pushreg rbp  
sub rsp, 040h  
.allocstack 040h     
lea rbp, [rsp+020h]  
.setframe rbp, 020h  
movdqa [rbp], xmm7  
.savexmm128 xmm7, 020h;the offset is from the base of the frame  
;not the scaled offset of the frame  
mov [rbp+018h], rsi  
.savereg rsi, 038h  
mov [rsp+010h], rdi  
.savereg rdi, 010h; you can still use RSP as the base of the frame  
; or any other register you choose  
.endprolog  
  
; you can modify the stack pointer outside of the prologue (similar to alloca)  
; because we have a frame pointer.  
; if we didn’t have a frame pointer, this would be illegal  
; if we didn’t make this modification,  
; there would be no need for a frame pointer  
  
sub rsp, 060h  
  
; we can unwind from the following AV because of the frame pointer  
  
mov rax, 0  
mov rax, [rax] ; AV!  
  
; restore the registers that weren’t saved with a push  
; this isn’t part of the official epilog, as described in section 2.5  
  
movdqa xmm7, [rbp]  
mov rsi, [rbp+018h]  
mov rdi, [rbp-010h]  
  
; Here’s the official epilog  
  
lea rsp, [rbp-020h]  
pop rbp  
ret  
sample ENDP  
```  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones auxiliares de desenredo para MASM](../build/unwind-helpers-for-masm.md)