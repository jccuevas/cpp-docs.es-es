---
title: "MxCsr | Microsoft Docs"
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
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MxCsr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El estado del registro también incluye MxCsr.  La convención de llamada divide este registro en una parte variable y otra no variable.  La parte variable está compuesta por los 6 marcadores de estado \(MXCSR\[0:5\]\), mientras el resto del registro \(MXCSR\[6:15\]\) se considera no variable.  
  
 La parte no variable se establece en los valores estándar siguientes al inicio de la ejecución del programa:  
  
```  
MXCSR[6]         : Denormals are zeros - 0  
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)  
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)  
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)  
```  
  
 Un destinatario que modifica cualquiera de los campos no variables incluidos en MXCSR debe restaurarlos antes de devolverlos a su llamador.  Además, un llamador que haya modificado alguno de estos campos debe restaurar los valores normales antes de invocar a un destinatario de llamada salvo que, por acuerdo, el destinatario espere valores modificados.  
  
 Hay dos excepciones a las reglas sobre marcadores de control no volátiles:  
  
-   En funciones donde el propósito documentado de la función determinada es modificar los marcadores de MxCsr no variables.  
  
-   Cuando sea correcto que la infracción de estas reglas dé como resultado un programa cuyo comportamiento es similar al de un programa en el que se han respetado las reglas, por ejemplo, mediante el análisis del programa completo.  
  
 No se pueden hacer suposiciones respecto al estado de la parte variable de MXCSR en el límite de una función, excepto que se describa específicamente en la documentación de una función.  
  
## Vea también  
 [Convención de llamada](../build/calling-convention.md)