---
title: "setjmp/longjump | Microsoft Docs"
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
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# setjmp/longjump
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se incluye setjmpex.h o setjmp.h, todas las llamadas a [setjmp](../c-runtime-library/reference/setjmp.md) o [longjmp](../c-runtime-library/reference/longjmp.md) resultarán en un desenredo que invoca a los destructores y llamadas finally.  Esto difiere de x86, donde incluir los resultados de setjmp.h no implica que se invoque a los destructores y cláusulas finally.  
  
 Una llamada a `setjmp` conserva el puntero de pila actual, los registros no volátiles y los registros de MxCsr.  Las llamadas a `longjmp` vuelven al emplazamiento de la llamada `setjmp` más reciente y se devuelve el puntero de pila, los registros no volátiles y los registros MxCsr al estado mantenido desde la llamada `setjmp` más reciente.  
  
## Vea también  
 [Convención de llamada](../build/calling-convention.md)