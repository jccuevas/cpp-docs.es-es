---
title: Comprobar la memoria sobrescribe | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 258aa6ae01d48df6717135f7dc8b73fc3f9e697a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369856"
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