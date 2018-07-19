---
title: 2.6.2 critical (construcción) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae7070fcc590307e71b0c34259bcbe1c12200550
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689602"
---
# <a name="262-critical-construct"></a>2.6.2 critical (Construcción)
El **crítico** directiva identifica una construcción que limita la ejecución del bloque estructurado asociado a un único subproceso cada vez. La sintaxis de la **crítico** directiva es como sigue:  
  
```  
#pragma omp critical [(name)]  new-linestructured-block  
```  
  
 Opcional *nombre* puede utilizarse para identificar la región crítica. Identificadores utilizados para identificar una región crítica tienen vinculación externa y están en un espacio de nombres que es independiente de los espacios de nombres utilizados por las etiquetas, etiquetas, los miembros e identificadores normales.  
  
 Un subproceso espera al principio de una región crítica hasta que ningún otro subproceso se está ejecutando una región crítica (en cualquier lugar en el programa) con el mismo nombre. Todos los sin nombre **crítico** asignan directivas en el mismo nombre especificado.