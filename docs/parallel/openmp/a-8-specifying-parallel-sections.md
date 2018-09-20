---
title: A.8 especificar secciones paralelas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d969f1a0e9d9b282104ee00a3b2d06610533ad4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440425"
---
# <a name="a8---specifying-parallel-sections"></a>A.8 Especificar secciones paralelas

En el ejemplo siguiente, (para [sección 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) en la página 14) funciones *valor*, *eje y*, y *zaxis* se puede ejecutar simultáneamente. La primera `section` directiva es opcional.  Tenga en cuenta que todos los `section` directivas deben aparecer en la extensión de léxico el `parallel sections` construir.

```
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```