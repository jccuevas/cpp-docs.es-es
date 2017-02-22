---
title: "EVEN y ALIGN (Directivas) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "align"
  - "EVEN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ALIGN (directiva)"
  - "directivas, MASM"
  - "EVEN (directiva)"
  - "MASM (Microsoft Macro Assembler), directivas"
  - "NOP (sin instrucciones de funcionamiento)"
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# EVEN y ALIGN (Directivas)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Aunque el ensamblador insertado no admite la mayoría de las directivas MASM, sí admite `EVEN` y **ALIGN**.  Estas directivas colocan instrucciones **NOP** \(sin operación\) en el código de ensamblado según sea necesario para ajustar las etiquetas a los límites específicos.  Esto hace que las operaciones de búsqueda de instrucciones sean más eficaces en algunos procesadores.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar lenguaje de ensamblado en bloques \_\_asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)