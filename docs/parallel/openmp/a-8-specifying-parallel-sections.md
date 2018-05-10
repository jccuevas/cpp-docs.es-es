---
title: A.8 especificar secciones paralelas | Documentos de Microsoft
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
ms.openlocfilehash: acb28f4e7e99ea09696d116ab031778fcf9ff919
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="a8---specifying-parallel-sections"></a>A.8 Especificar secciones paralelas
En el ejemplo siguiente, (para [sección 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) en la página 14) funciones *xaxis*, *eje y*, y *zaxis* pueden ejecutarse simultáneamente. La primera `section` directiva es opcional.  Tenga en cuenta que todos los `section` directivas tiene que aparecer en la extensión léxica de los `parallel sections` construir.  
  
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