---
title: Directivas de OpenMP | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7421f397b39c6d26c2e60042b25f37277afa5fd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="openmp-directives"></a>Directivas de OpenMP
Proporciona vínculos a las directivas que se utilizan en la API de OpenMP.  
  
 Visual C++ admite las siguientes directivas de OpenMP:  
  
|Directiva|Descripción|  
|---------------|-----------------|  
|[atomic](../../../parallel/openmp/reference/atomic.md)|Especifica que una ubicación de memoria que se actualizarán de forma atómica.|  
|[barrier](../../../parallel/openmp/reference/barrier.md)|Sincroniza todos los subprocesos en un equipo; todos los subprocesos se sitúe en la barrera, hasta que todos los subprocesos ejecutan la barrera.|  
|[critical](../../../parallel/openmp/reference/critical.md)|Especifica que el código solo se ejecuta en un subproceso a la vez.|  
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|Especifica que todos los subprocesos tienen la misma vista de memoria para todos los objetos compartidos.|  
|[for](../../../parallel/openmp/reference/for-openmp.md)|Hace que el trabajo realizado un bucle dentro de una región paralela va a dividir entre subprocesos.|  
|[master](../../../parallel/openmp/reference/master.md)|Especifica que sólo lo threadshould maestro ejecutará una sección del programa.|  
|[ordenada](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Especifica que el código en una ejecución en paralelo para bucle debe ejecutarse como un bucle secuencial.|  
|[parallel](../../../parallel/openmp/reference/parallel.md)|Define una región paralela, que es código que se ejecutará por varios subprocesos en paralelo.|  
|[Secciones](../../../parallel/openmp/reference/sections-openmp.md)|Identifica las secciones de código para ser dividido entre todos los subprocesos.|  
|[single](../../../parallel/openmp/reference/single.md)|Le permite especificar que una sección de código debe ejecutarse en un solo subproceso, no necesariamente el subproceso principal.|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Especifica que una variable privada a un subproceso.|  
  
## <a name="see-also"></a>Vea también  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)