---
title: "PROC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROC directive"
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# PROC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las marcas inician y final de un bloque de procedimiento denominado *etiqueta*.  Las instrucciones del bloque se pueden llamar a la instrucción de **Llamada** o la directiva de [INVOCAR](../../assembler/masm/invoke.md) .  
  
## Sintaxis  
  
```  
  
   label PROC [[distance]] [[langtype]] [[visibility]] [[<prologuearg>]]   
[[USES reglist]] [[, parameter [[:tag]]]]...  
[FRAME [:ehandler-address] ]  
statements  
label ENDP  
```  
  
## Comentarios  
 \[FRAME \[:*la ehandler\-dirección*\]\] sólo es válido con ml64.exe, haga MASM para generar una entrada de tabla de la función en .pdata y desenredar la información en .xdata para el control de excepciones estructurado de una función desenredo el comportamiento.  
  
 Cuando se utiliza el atributo de **Marco** , debe ir seguido de una directiva de [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) .  
  
 Vea [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md) para obtener más información sobre cómo utilizar ml64.exe.  
  
## Ejemplo  
  
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
  
 El código anterior emitirá la tabla de función siguiente y desenrollará información:  
  
```  
FileHeader->Machine 34404  
Dumping Unwind Information for file ex2.exe  
  
.pdata entry 1 0x00001000 0x00001023  
  
  Unwind data: 0x00002000  
  
    Unwind version: 1  
    Unwind Flags: None  
    Size of prologue: 0x08  
    Count of codes: 3  
    Frame register: rbp  
    Frame offset: 0x0  
    Unwind codes:  
  
      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00  
      Code offset: 0x05, ALLOC_SMALL, size=0x10  
      Code offset: 0x01, PUSH_NONVOL, register=rbp  
```  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)