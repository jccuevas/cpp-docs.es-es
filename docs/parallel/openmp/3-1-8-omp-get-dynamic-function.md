---
title: 3.1.8 omp_get_dynamic (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af7755173ab884a40a5f8a41f432f265cc1e6c32
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
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