---
title: Dependencias acumuladas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d502912a8aeee2e6b3782e7795f44238386e1dba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cumulative-dependencies"></a>Dependencias acumuladas
Las dependencias son acumulativas en un bloque de descripción si se repite un destino.  
  
 Por ejemplo, este conjunto de reglas,  
  
```Output  
bounce.exe : jump.obj  
bounce.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 se evalúa como esta:  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 Varios destinos en varias líneas de dependencia en un solo bloque de descripción se evalúan como si cada uno se especificaron en un bloque de descripción independiente, pero los destinos que no están en la última línea de dependencia no usan el bloque de comandos. NMAKE intenta usar una regla de inferencia para estos destinos.  
  
 Por ejemplo, este conjunto de reglas,  
  
```Output  
leap.exe bounce.exe : jump.obj  
bounce.exe climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 se evalúa como esta:  
  
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