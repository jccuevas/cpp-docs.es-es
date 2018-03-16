---
title: "2.5.1 parallel for (construcción) | Documentos de Microsoft"
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
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7dcd763b68a78e11c3c33bf3d750a26e88ad02ee
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
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