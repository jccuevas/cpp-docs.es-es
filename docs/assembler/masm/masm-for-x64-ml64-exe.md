---
title: "MASM for x64 (ml64.exe) | Microsoft Docs"
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
helpviewer_keywords: 
  - "ml64.exe"
  - "ml"
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MASM for x64 (ml64.exe)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ml64.exe es el ensamblador que acepta el lenguaje de ensamblado de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] .  Para obtener información sobre las opciones del compilador de ml64.exe, vea [ML and ML64 Command\-Line Reference](../../assembler/masm/ml-and-ml64-command-line-reference.md).  
  
 El ASM especificado no se admite para [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)].  Uso MASM o función intrínseca del compilador \([x64 Intrinsics](http://msdn.microsoft.com/es-es/5d1f5d3e-156e-4ebf-932e-fd09be7ced62)\).  
  
 Las dos soluciones alternativas son el ensamblado independiente con MASM \(que admite x64 totalmente\) y función intrínseca del compilador.  Hemos agregado muchos intrínseco para permitir que los clientes hacen uso de instrucciones especial\-función \(por ejemplo.  análisis privilegiado, de bits por prueba, de bloqueo, etc.…\) en tan cierre a la interplataforma una manera posible.  
  
## directivas de ml64\-Specific  
 Utilice las siguientes directivas con ml64.exe:  
  
-   [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)  
  
-   [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)  
  
-   [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)  
  
-   [.PUSHREG](../../assembler/masm/dot-pushreg.md)  
  
-   [.SAVEREG](../../assembler/masm/dot-savereg.md)  
  
-   [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)  
  
-   [.SETFRAME](../../assembler/masm/dot-setframe.md)  
  
 Además, la directiva de [PROC](../../assembler/masm/proc.md) se actualizó con ml64.exe.  
  
## modo de direcciones de 32 bits \(invalidación del tamaño de la dirección\)  
 MASM emitirá el reemplazo del tamaño de la dirección 0x67 si un operando de memoria incluye los registros de 32 bits.  Por ejemplo, los ejemplos siguientes producen la invalidación del tamaño de dirección que se emitirá:  
  
```  
mov rax, QWORD PTR [ecx]  
mov eax, DWORD PTR [ecx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10d+0100h]  
prefetch [eax]  
movnti rax, QWORD PTR [r8d]  
```  
  
 MASM supone que si un desplazamiento de 32 bits solo aparece como operando de memoria, el 64 bit addressing está pensado.  Actualmente no hay compatibilidad con el direccionamiento de 32 bits con estos operandos.  
  
 Finalmente, mezclar los tamaños de registro dentro de un operando de memoria, como se muestra en el código siguiente, generará un error.  
  
```  
mov eax, DWORD PTR [rcx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10+0100h]  
```  
  
## Vea también  
 [Microsoft Macro Assembler Reference](../../assembler/masm/microsoft-macro-assembler-reference.md)