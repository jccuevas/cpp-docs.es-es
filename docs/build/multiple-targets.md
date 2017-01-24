---
title: "Destinos m&#250;ltiples | Microsoft Docs"
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
  - "MAKE (archivos), destinos"
  - "varios destinos en NMAKE"
  - "destinos, múltiples en NMAKE"
  - "NMAKE (programa), destinos"
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Destinos m&#250;ltiples
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE evalúa varios destinos en una sola dependencia como si cada uno estuviera especificado en un bloque de descripción independiente.  
  
 Por ejemplo, esto...  
  
```Output  
bounce.exe leap.exe : jump.obj  
   echo Building...  
```  
  
 .. .es código que se evalúa como lo siguiente:  
  
```Output  
bounce.exe : jump.obj  
   echo Building...  
leap.exe : jump.obj  
   echo Building...  
```  
  
## <a name="see-also"></a>Vea también  
 [Destinos](../build/targets.md)