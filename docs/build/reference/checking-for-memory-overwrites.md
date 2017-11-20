---
title: Comprobar la memoria sobrescribe | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4560fb580d3d1b24feccf84dc07bde7dc38458c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="checking-for-memory-overwrites"></a>Comprobar si se ha sobrescrito la memoria
Si se produce una infracción de acceso en una llamada a una función de manipulación de montón, es posible que el programa haya dañado el montón. Un síntoma común de esta situación sería:  
  
```  
Access Violation in _searchseg  
```  
  
 El [_heapchk](../../c-runtime-library/reference/heapchk.md) función está disponible en ambas versiones de depuración y de lanzamiento (sólo en Windows NT) para comprobar la integridad del montón de la biblioteca de tiempo de ejecución. Puede usar `_heapchk` de la misma manera como el `AfxCheckMemory` función para aislar una sobrescritura en el montón, por ejemplo:  
  
```  
if(_heapchk()!=_HEAPOK)  
   DebugBreak();  
```  
  
 Si esta función nunca se produce un error, debe aislar punto en el que se ha dañado el montón.  
  
## <a name="see-also"></a>Vea también  
 [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)