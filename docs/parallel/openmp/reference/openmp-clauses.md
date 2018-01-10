---
title: "Cláusulas de OpenMP | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 582afec1c2d6401aee107a2e20cc04ef943254ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="openmp-clauses"></a>Cláusulas de OpenMP
Proporciona vínculos a las cláusulas que se utilizan en la API de OpenMP.  
  
 Visual C++ admite las cláusulas de OpenMP siguientes:  
  
|Cláusula|Descripción|  
|------------|-----------------|  
|[copyin](../../../parallel/openmp/reference/copyin.md)|Permite que los subprocesos tener acceso a valor del subproceso principal, para un [threadprivate](../../../parallel/openmp/reference/threadprivate.md) variable.|  
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|Especifica que una o más variables deben compartirse entre todos los subprocesos.|  
|[default](../../../parallel/openmp/reference/default-openmp.md)|Especifica el comportamiento de las variables sin ámbito en una región paralela.|  
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|Especifica que cada subproceso debe tener su propia instancia de una variable, y que se debe inicializar la variable con el valor de la variable, porque existe antes de la construcción paralela.|  
|[if](../../../parallel/openmp/reference/if-openmp.md)|Especifica si se debe ejecutar un bucle en paralelo o en serie.|  
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|Especifica que la versión del contexto envolvente de la variable se establece igual que la versión privada del cualquier subproceso ejecuta la última iteración (construcción de bucle for) o la última sección (#pragma secciones).|  
|[nowait](../../../parallel/openmp/reference/nowait.md)|Invalida la barrera implícita en una directiva.|  
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|Establece el número de subprocesos en un equipo de subproceso.|  
|[ordenada](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|Obligatorio en un paralelo [para](../../../parallel/openmp/reference/for-openmp.md) instrucción si un [ordenados](../../../parallel/openmp/reference/ordered-openmp-directives.md) directiva es para su uso en el bucle.|  
|[private](../../../parallel/openmp/reference/private-openmp.md)|Especifica que cada subproceso debe tener su propia instancia de una variable.|  
|[reduction](../../../parallel/openmp/reference/reduction.md)|Especifica que una o más variables que son privadas para cada subproceso son el asunto de una operación de reducción al final de la región paralela.|  
|[schedule](../../../parallel/openmp/reference/schedule.md)|Se aplica a la [para](../../../parallel/openmp/reference/for-openmp.md) directiva.|  
|[compartido](../../../parallel/openmp/reference/shared-openmp.md)|Especifica que una o más variables deben compartirse entre todos los subprocesos.|  
  
## <a name="see-also"></a>Vea también  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Directivas](../../../parallel/openmp/reference/openmp-directives.md)