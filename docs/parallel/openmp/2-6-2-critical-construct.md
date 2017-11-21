---
title: "2.6.2 critical (construcción) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13e9b4a8611732c7dddb81be1ca6123b725f7169
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="262-critical-construct"></a>2.6.2 critical (Construcción)
El **crítico** directiva identifica una construcción que limita la ejecución del bloque estructurado asociado a un único subproceso cada vez. La sintaxis de la **crítico** directiva es como sigue:  
  
```  
#pragma omp critical [(name)]  new-linestructured-block  
```  
  
 Opcional *nombre* puede utilizarse para identificar la región crítica. Identificadores utilizados para identificar una región crítica tienen vinculación externa y están en un espacio de nombres que es independiente de los espacios de nombres utilizados por las etiquetas, etiquetas, los miembros e identificadores normales.  
  
 Un subproceso espera al principio de una región crítica hasta que ningún otro subproceso se está ejecutando una región crítica (en cualquier lugar en el programa) con el mismo nombre. Todos los sin nombre **crítico** asignan directivas en el mismo nombre especificado.