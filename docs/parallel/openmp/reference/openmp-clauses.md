---
title: Cláusulas de OpenMP | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7abe5a637a2a32c696f19f5ab9988f1be361f647
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
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
|[Compartido](../../../parallel/openmp/reference/shared-openmp.md)|Especifica que una o más variables deben compartirse entre todos los subprocesos.|  
  
## <a name="see-also"></a>Vea también  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Directivas](../../../parallel/openmp/reference/openmp-directives.md)