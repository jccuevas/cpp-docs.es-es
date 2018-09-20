---
title: Directivas de OpenMP | Microsoft Docs
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
ms.openlocfilehash: 983a71920e9e7ce390ab8c64e81886db0d459450
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389453"
---
# <a name="openmp-directives"></a>Directivas de OpenMP

Proporciona vínculos a las directivas que se utilizan en la API de OpenMP.

Visual C++ admite las siguientes directivas de OpenMP:

|Directiva|Descripción|
|---------------|-----------------|
|[atomic](../../../parallel/openmp/reference/atomic.md)|Especifica que una ubicación de memoria que se actualizarán de forma atómica.|
|[barrier](../../../parallel/openmp/reference/barrier.md)|Sincroniza todos los subprocesos en un equipo; todos los subprocesos se detendrá en la barrera, hasta que todos los subprocesos ejecuten la barrera.|
|[critical](../../../parallel/openmp/reference/critical.md)|Especifica que código solo se ejecuta en un subproceso a la vez.|
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|Especifica que todos los subprocesos tienen la misma vista de memoria para todos los objetos compartidos.|
|[for](../../../parallel/openmp/reference/for-openmp.md)|Hace que el trabajo realizado en un bucle dentro de una región paralela a dividirse entre subprocesos.|
|[master](../../../parallel/openmp/reference/master.md)|Especifica que sólo el maestro threadshould ejecutar una sección del programa.|
|[Ordenada](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Especifica ese código en una ejecución en paralelo para el bucle se debe ejecutar como un bucle secuencial.|
|[parallel](../../../parallel/openmp/reference/parallel.md)|Define una región paralela, que es código que se va a ejecutar varios subprocesos en paralelo.|
|[Secciones](../../../parallel/openmp/reference/sections-openmp.md)|Identifica las secciones de código se divide entre todos los subprocesos.|
|[single](../../../parallel/openmp/reference/single.md)|Le permite especificar que una sección de código debe ejecutarse en un único subproceso, no necesariamente el subproceso principal.|
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Especifica que una variable privada a un subproceso.|

## <a name="see-also"></a>Vea también

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)