---
title: "3.1.8 omp_get_dynamic (función) | Documentos de Microsoft"
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
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd4ec73b82848efcdface781738639b05a256958
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic (Función)
El **omp_get_dynamic ()** función devuelve un valor distinto de cero si realizar un ajuste dinámico de subprocesos está habilitado y lo contrario, devuelve 0. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_dynamic(void);  
```  
  
 Si la implementación no implementa realizar un ajuste dinámico del número de subprocesos, esta función siempre devuelve 0.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   Para obtener una descripción de ajuste de subproceso dinámica, consulte [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.