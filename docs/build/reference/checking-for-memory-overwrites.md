---
title: "Comprobar si se ha sobrescrito la memoria | Microsoft Docs"
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
  - "memoria, sobrescrituras"
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Comprobar si se ha sobrescrito la memoria
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Si se obtiene una infracción de acceso en una llamada a una función de manipulación del montón, puede ser que el programa haya dañado el montón.  Un síntoma habitual de esta situación sería:  
  
```  
Access Violation in _searchseg  
```  
  
 La función [\_heapchk](../../c-runtime-library/reference/heapchk.md) está disponible tanto en versiones de depuración como de lanzamiento \(sólo en Windows NT\) para comprobar la integridad del montón de la biblioteca en tiempo de ejecución.  Se puede utilizar `_heapchk` de forma análoga a la función `AfxCheckMemory` para aislar una sobrescritura en el montón; por ejemplo:  
  
```  
if(_heapchk()!=_HEAPOK)  
   DebugBreak();  
```  
  
 Si esta función produce un error en algún momento, se deberá aislar el punto en el que el montón resultó dañado.  
  
## Vea también  
 [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)