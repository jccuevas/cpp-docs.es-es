---
title: 2.5.1 parallel for (construcción) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef2732c4f8713466d282346ea240bd3c41886ce0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687158"
---
# <a name="251-parallel-for-construct"></a>2.5.1 parallel for (Construcción)
El **for paralelos** directiva es un acceso directo para un **paralelo** una región que contiene solo una **para** directiva. La sintaxis de la **for paralelos** directiva es como sigue:  
  
```  
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop  
```  
  
 Esta directiva permite que todas las cláusulas de la **paralelo** directiva y la **para** directiva, excepto el `nowait` cláusula idéntico significado y las restricciones. La semántica es idéntica a la especificación explícita de un **paralelo** directiva seguido inmediatamente por un **para** directiva.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   **paralelo** directiva, consulte [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) en página 8.  
  
-   **para** directiva, consulte [sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en página 11.  
  
-   Cláusulas de atributos de datos, vea [2.7.2 cláusulas de atributos de uso compartido de datos](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en página 25.