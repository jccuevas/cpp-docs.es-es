---
title: "Pseudoperaciones sin formato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Pseudoperaciones sin formato
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema contiene una lista de las pseudoperaciones.  
  
## Comentarios  
  
|Pseudoperación|Descripción|  
|--------------------|-----------------|  
|PROC FRAME \[:ehandler\]|Hace que MASM genere una entrada de tabla de funciones en .pdata e información de desenredo en .xdata para el comportamiento de desenredo del control de excepciones estructurado de una función.  Si ehandler está presente, este procedimiento se escribe en .xdata como el controlador específico del lenguaje.<br /><br /> Cuando se utiliza el atributo FRAME, debe ir seguido de una directiva .ENDPROLOG.  Si la función es de hoja \(como se define en [Tipos de funciones](../build/function-types.md)\), el atributo FRAME es innecesario, igual que el resto de estas pseudoperaciones.|  
|.PUSHREG registro|Genera una entrada de código de desenredo UWOP\_PUSH\_NONVOL correspondiente al número del registro especificado mediante el desplazamiento actual en el prólogo.<br /><br /> Sólo se debe utilizar con registros enteros no variables.  Para inserciones de registros variables, utilice .ALLOCSTACK 8 en su lugar|  
|.SETFRAME registro, desplazamiento|Rellena el campo de registro de marco y el desplazamiento en la información de desenredo mediante el registro y el desplazamiento especificados.  El desplazamiento debe ser múltiplo de 16 y menor o igual que 240.  Esta directiva también genera una entrada de código de desenredo UWOP\_SET\_FPREG para el registro especificado mediante el desplazamiento de prólogo actual.|  
|.ALLOCSTACK tamaño|Genera una entrada UWOP\_ALLOC\_SMALL o UWOP\_ALLOC\_LARGE con el tamaño especificado para el desplazamiento actual en el prólogo.<br /><br /> El operando del tamaño debe ser un múltiplo de 8.|  
|.SAVEREG registro, desplazamiento|Genera una entrada de código de desenredo UWOP\_SAVE\_NONVOL o UWOP\_SAVE\_NONVOL\_FAR para el registro y el desplazamiento especificados utilizando el desplazamiento actual del prólogo.  MASM elegirá la codificación más eficaz.<br /><br /> El desplazamiento debe ser positivo y múltiplo de 8.  El desplazamiento es relativo a la base del marco del procedimiento, que por lo general está en RSP, o bien, si se usa un puntero de marco, el puntero de marco sin cambio de escala.|  
|.SAVEXMM128 registro, desplazamiento|Genera una entrada de código de desenredo UWOP\_SAVE\_XMM128 o UWOP\_SAVE\_XMM128\_FAR para el registro XMM y el desplazamiento especificados utilizando el desplazamiento actual del prólogo.  MASM elegirá la codificación más eficaz.<br /><br /> El desplazamiento debe ser positivo y múltiplo de 16.  El desplazamiento es relativo a la base del marco del procedimiento, que por lo general está en RSP, o bien, si se usa un puntero de marco, el puntero de marco sin cambio de escala.|  
|.PUSHFRAME \[código\]|Genera una entrada de código de desenredo UWOP\_PUSH\_MACHFRAME.  Si se especifica el código opcional, la entrada de código de desenredo recibe un modificador de 1.  De lo contrario, el modificador es 0.|  
|.ENDPROLOG|Señala el fin de las declaraciones del prólogo.  Debe aparecer en los primeros 255 bytes de la función.|  
  
 Este es un ejemplo de prólogo de función con uso correcto de la mayoría de los códigos de operación:  
  
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
  
## Vea también  
 [Aplicaciones auxiliares de desenredo para MASM](../build/unwind-helpers-for-masm.md)