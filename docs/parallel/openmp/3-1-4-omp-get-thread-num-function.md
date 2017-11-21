---
title: "3.1.4 omp_get_thread_num (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9beb9e81d767a11b4ca701725ac44cc19cd3c3e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num (Función)
El `omp_get_thread_num` función devuelve el número de subprocesos, dentro de su equipo, de que el subproceso que ejecuta la función. Los archivos de número subproceso entre 0 y **omp_get_num_threads()**-1, ambos inclusive. El subproceso principal del equipo es 0.  
  
 El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_thread_num(void);  
```  
  
 Si se llama desde una región de la serie, `omp_get_thread_num` devuelve 0. Si se llama desde dentro de una región paralela anidada que se serializa, esta función devuelve 0.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   `omp_get_num_threads`función, vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37.