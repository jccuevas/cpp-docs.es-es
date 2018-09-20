---
title: Cláusulas de OpenMP | Microsoft Docs
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
ms.openlocfilehash: afd0a8f66f9b0d027671629998597955b3aa69e9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378340"
---
# <a name="openmp-clauses"></a>Cláusulas de OpenMP

Proporciona vínculos a las cláusulas que se utilizan en la API de OpenMP.

Visual C++ admite las cláusulas de OpenMP siguientes:

|Cláusula|Descripción|
|------------|-----------------|
|[copyin](../../../parallel/openmp/reference/copyin.md)|Permite que los subprocesos tener acceso a valor del subproceso principal, para un [threadprivate](../../../parallel/openmp/reference/threadprivate.md) variable.|
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|Especifica que una o más variables deben compartirse entre todos los subprocesos.|
|[default](../../../parallel/openmp/reference/default-openmp.md)|Especifica el comportamiento de las variables sin ámbito de una región paralela.|
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|Especifica que cada subproceso debe tener su propia instancia de una variable, y que la variable debe inicializarse con el valor de la variable, porque existe antes de la construcción paralela.|
|[if](../../../parallel/openmp/reference/if-openmp.md)|Especifica si se debe ejecutar un bucle en paralelo o en serie.|
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|Especifica que versión envolvente del contexto de la variable se establece igual que la versión privada de cualquier subproceso que ejecuta la última iteración (construcción de bucle for) o la última sección (#pragma secciones).|
|[nowait](../../../parallel/openmp/reference/nowait.md)|Invalida la barrera implícita en una directiva.|
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|Establece el número de subprocesos en un equipo de subproceso.|
|[Ordenada](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|Necesario en un paralelo [para](../../../parallel/openmp/reference/for-openmp.md) instrucción si un [ordenados](../../../parallel/openmp/reference/ordered-openmp-directives.md) directiva es que se usará en el bucle.|
|[private](../../../parallel/openmp/reference/private-openmp.md)|Especifica que cada subproceso debe tener su propia instancia de una variable.|
|[reduction](../../../parallel/openmp/reference/reduction.md)|Especifica que una o más variables que son privadas para cada subproceso se el sujeto de una operación de reducción al final de la región paralela.|
|[schedule](../../../parallel/openmp/reference/schedule.md)|Se aplica a la [para](../../../parallel/openmp/reference/for-openmp.md) directiva.|
|[Compartido](../../../parallel/openmp/reference/shared-openmp.md)|Especifica que una o más variables deben compartirse entre todos los subprocesos.|

## <a name="see-also"></a>Vea también

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[Directivas](../../../parallel/openmp/reference/openmp-directives.md)