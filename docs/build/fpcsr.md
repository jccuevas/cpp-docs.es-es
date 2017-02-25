---
title: "FpCsr | Microsoft Docs"
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
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# FpCsr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El estado del registro también incluye la palabra de control de la unidad de punto flotante \(FPU x87\).  La convención de llamada obliga a que este registro sea no volátil.  
  
 El registro de la palabra de control de FPU x87 se establece en los valores estándar siguientes cuando se inicia la ejecución del programa:  
  
```  
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)  
FPCSR[7]: Reserved – 0  
FPCSR[8:9]: Precision Control – 10B (double precision)  
FPCSR[10:11]: Rounding  control - 0 (round to nearest)  
FPCSR[12]: Infinity control – 0 (not used)  
```  
  
 Un destinatario de llamada que modifique uno de los campos dentro de FPCSR debe restaurarlos antes de devolver a su llamador.  Además, un llamador que haya modificado alguno de estos campos debe restaurar los valores normales antes de invocar a un destinatario de llamada salvo que, por acuerdo, el destinatario espere valores modificados.  
  
 Hay dos excepciones a las reglas sobre marcadores de control no volátiles:  
  
1.  Funciones cuyo propósito documentado sea modificar los marcadores de control FpCsr no volátiles.  
  
2.  Cuando sea correcto que la infracción de estas reglas dé como resultado un programa cuyo comportamiento es similar al de un programa en el que se han respetado las reglas, por ejemplo, mediante el análisis del programa completo.  
  
## Vea también  
 [Convención de llamada](../build/calling-convention.md)