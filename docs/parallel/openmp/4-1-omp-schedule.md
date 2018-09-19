---
title: 4.1 OMP_SCHEDULE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e13332077a40e741f56b5602ac5197bbdfef071
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691055"
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