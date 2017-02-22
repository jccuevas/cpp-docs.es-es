---
title: "_emit (Pseudoinstrucci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_emit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_emit (pseudoinstrucción)"
  - "definición de bytes (ensamblado alineado)"
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _emit (Pseudoinstrucci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 La pseudoinstrucción **\_emit** define un byte en la ubicación actual del segmento de texto actual.  La pseudoinstrucción **\_emit** se parece a la directiva [DB](../../assembler/masm/db.md) de MASM.  
  
 El fragmento siguiente coloca los bytes 0x4A, 0x43 y 0x4B en el código:  
  
```  
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B  
 .  
 .  
 .  
__asm {  
     randasm  
     }  
```  
  
> [!CAUTION]
>  Si `_emit` genera instrucciones que modifican los registros y se compila la aplicación con optimizaciones, el compilador no puede determinar qué registros se ven afectados.  Por ejemplo, si `_emit` genera una instrucción que modifica el registro **rax**, el compilador no sabrá que **rax** ha cambiado.  y podría suponer incorrectamente el valor de ese registro después de la ejecución del código ensamblador alineado.  Por consiguiente, la aplicación podría tener un comportamiento impredecible al ejecutarse.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar lenguaje de ensamblado en bloques \_\_asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)