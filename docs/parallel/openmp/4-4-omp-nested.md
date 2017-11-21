---
title: 4.4 OMP_NESTED | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fbb45bb04db612451c7d081f3a7afad8031da643
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
El `OMP_NESTED` variable de entorno habilita o deshabilita el paralelismo anidado a menos que paralelismo anidado está habilitado o deshabilitado mediante una llamada a la `o` **mp_set_nested** rutina de biblioteca. Si establece en **TRUE**, paralelismo anidado está habilitado; si se establece en **FALSE**anidado paralelismo está deshabilitado. El valor predeterminado es **FALSE**.  
  
 Ejemplo:  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>Referencia cruzada:  
  
-   `omp_set_nested`función, vea [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40.