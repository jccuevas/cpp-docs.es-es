---
title: PROC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROC
dev_langs:
- C++
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0900b277650fee1c4134d354d964d49d570c6266
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="proc"></a>PROC
Marca el principio y final de un bloque de procedimiento llamado *etiqueta*. Las instrucciones del bloque se pueden llamar con la **llamar a** instrucción o [INVOKE](../../assembler/masm/invoke.md) directiva.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
   label PROC [[distance]] [[langtype]] [[visibility]] [[<prologuearg>]]   
[[USES reglist]] [[, parameter [[:tag]]]]...  
[FRAME [:ehandler-address] ]  
statements  
label ENDP  
```  
  
## <a name="remarks"></a>Comentarios  
 [Marco [:*ehandler dirección*]] sólo es válido con ml64.exe y hace que MASM generar una entrada de tabla de funciones en .pdata e información de desenredo en .xdata para una función de la estructura comportamiento de desenredo del control de excepciones.  
  
 Cuando el **marco** se usa el atributo, debe ir seguido por un [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directiva.  
  
 Vea [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) para obtener más información sobre el uso de ml64.exe.  
  
## <a name="example"></a>Ejemplo  
  
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
  
 El código anterior se emita la siguiente tabla de funciones e información de desenredo:  
  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)