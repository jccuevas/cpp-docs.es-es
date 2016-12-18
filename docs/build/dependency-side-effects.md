---
title: "Efectos secundarios de las relaciones de dependencia | Microsoft Docs"
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
  - "dependencias, efectos secundarios"
  - "NMAKE (programa), dependientes"
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Efectos secundarios de las relaciones de dependencia
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si se especifica un destino con un signo de dos puntos (:) en dos líneas de dependencia en diferentes ubicaciones y comandos aparecen después de sólo una de las líneas, NMAKE interpreta las dependencias como si adyacentes o combinadas. No se invoca una regla de inferencia para la dependencia que no tiene comandos, sino que supone que las dependencias pertenecen a un bloque de descripción y ejecuta los comandos especificados con la otra dependencia. Por ejemplo, este conjunto de reglas:  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
```  
  
 se evalúa como lo siguiente:  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 Este efecto no se produce si dos puntos dobles (`::`) se utiliza. Por ejemplo, este conjunto de reglas:  
  
```Output  
bounce.exe :: jump.obj  
   echo Building bounce.exe...  
  
bounce.exe :: up.obj  
```  
  
 se evalúa como lo siguiente:  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
# invokes an inference rule  
```  
  
## <a name="see-also"></a>Vea también  
 [Destinos](../build/targets.md)