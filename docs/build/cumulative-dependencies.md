---
title: "Dependencias acumuladas | Microsoft Docs"
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
  - "dependencias, acumuladas"
  - "dependencias acumuladas en NMAKE"
  - "dependencias"
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Dependencias acumuladas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las dependencias son acumulativas en un bloque de descripción si se repite un destino.  
  
 Por ejemplo, este conjunto de reglas,  
  
```Output  
bounce.exe : jump.obj  
bounce.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 se evalúa como lo siguiente:  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 Varios destinos en varias líneas de dependencia en un solo bloque de descripción se evalúan como si cada uno estuviera especificado en un bloque de descripción independiente, pero los destinos que no están en la última línea de dependencia no usan el bloque de comandos. NMAKE intenta utilizar una regla de inferencia para estos destinos.  
  
 Por ejemplo, este conjunto de reglas,  
  
```Output  
leap.exe bounce.exe : jump.obj  
bounce.exe climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 se evalúa como lo siguiente:  
  
```Output  
  
leap.exe : jump.obj  
# invokes an inference rule  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
## <a name="see-also"></a>Vea también  
 [Destinos](../build/targets.md)