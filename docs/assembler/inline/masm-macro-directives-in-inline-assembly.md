---
title: "Directivas de macro MASM en ensamblados alineados | Microsoft Docs"
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
helpviewer_keywords: 
  - "directivas, macros"
  - "ensamblado en línea, macro (directivas)"
  - "macros, directivas"
  - "MASM (Microsoft Macro Assembler), directivas de macro para ensamblados alineados"
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Directivas de macro MASM en ensamblados alineados
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 El ensamblador alineado no es un Macro Assembler.  No puede utilizar directivas de macro de MASM \(**MACRO**, `REPT`, **IRC**, `IRP` y `ENDM`\) ni operadores de macro \(**\<\>**, **\!**, **&**, `%` y `.TYPE`\).  Sin embargo, un bloque `__asm` puede usar directivas de preprocesador de C.  Vea [Uso de C o C\+\+ en bloques \_\_asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) para obtener más información.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar lenguaje de ensamblado en bloques \_\_asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)