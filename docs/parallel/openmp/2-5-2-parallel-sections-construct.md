---
title: "2.5.2 parallel sections (construcción) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 086552c72e37822920e0afa213c7966befa052f7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="252-parallel-sections-construct"></a>2.5.2 parallel sections (Construcción)
El **secciones en paralelo** directiva proporciona una forma de acceso directo para especificar un **paralelo** región que contiene solo una **secciones** directiva. La semántica es idéntica a la especificación explícita de un **paralelo** directiva seguido inmediatamente por un **secciones** directiva. La sintaxis de la **secciones en paralelo** directiva es como sigue:  
  
```  
#pragma omp parallel sections  [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-linestructured-block  ]  
   ...  
}  
```  
  
 El *cláusula* puede ser una de las cláusulas aceptadas por la **paralelo** y **secciones** directivas, excepto el **nowait** cláusula.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   **paralelo** directiva, consulte [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) en página 8.  
  
-   **secciones** directiva, consulte [sección 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) en la página 14.