---
title: 4.4 OMP_NESTED | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1779b75774a2177a0d6a4f0661406e28b479a7ee
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690275"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
El `OMP_NESTED` variable de entorno habilita o deshabilita el paralelismo anidado a menos que paralelismo anidado está habilitado o deshabilitado mediante una llamada a la `o` **mp_set_nested** rutina de biblioteca. Si establece en **TRUE**, paralelismo anidado está habilitado; si se establece en **FALSE**anidado paralelismo está deshabilitado. El valor predeterminado es **FALSE**.  
  
 Ejemplo:  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>Referencia cruzada:  
  
-   `omp_set_nested` función, vea [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40.