---
title: 4.1 OMP_SCHEDULE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 330e5ea576e3cd779a7c17c21d00b6459f5e7043
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE
**OMP_SCHEDULE** solo se aplica a **para** y **for paralelos** directivas que tengan el tipo de programación **en tiempo de ejecución**. El tamaño de tipo y el fragmento de programación para todos los bucles de este tipo se puede establecer en tiempo de ejecución al establecer esta variable de entorno que va a cualquiera de los tipos de programación reconocido como un elemento opcional *chunk_size*.  
  
 Para **para** y **for paralelos** directivas que tienen un tipo de programación distinto de **en tiempo de ejecución**, **OMP_SCHEDULE** se omite. El valor predeterminado de esta variable de entorno es definido por la implementación. Si la parte opcional *chunk_size* se establece, el valor debe ser positivo. Si *chunk_size* no se establece, se supone que un valor de 1, excepto en el caso de un **estático** programación. Para una **estático** programación, el tamaño del fragmento predeterminado se establece en el espacio de iteración del bucle dividido por el número de subprocesos que se aplica al bucle.  
  
 Ejemplo:  
  
```  
setenv OMP_SCHEDULE "guided,4"  
setenv OMP_SCHEDULE "dynamic"  
```  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   **para** directiva, consulte [sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en página 11.  
  
-   **paralelas para** directiva, consulte [sección 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) en la página 16.