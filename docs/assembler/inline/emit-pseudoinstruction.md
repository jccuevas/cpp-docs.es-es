---
title: "_emit (pseudoinstrucción) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _emit
dev_langs:
- C++
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c506c689b94a7f6f7fa51c4c456e20454b28df02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="emit-pseudoinstruction"></a>_emit (Pseudoinstrucción)
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 El **_emit** (pseudoinstrucción) define un byte en la ubicación actual en el segmento de texto actual. El **_emit** (pseudoinstrucción) es similar a la [DB](../../assembler/masm/db.md) la directiva de MASM.  
  
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
>  Si `_emit` genera instrucciones que modifican los registros y se compila la aplicación con optimizaciones, el compilador no puede determinar qué registros se ven afectados. Por ejemplo, si `_emit` genera una instrucción que modifica la **rax** registro, el compilador no sabe que **rax** ha cambiado. y podría suponer incorrectamente el valor de ese registro después de la ejecución del código ensamblador alineado. Por consiguiente, la aplicación podría tener un comportamiento impredecible al ejecutarse.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)