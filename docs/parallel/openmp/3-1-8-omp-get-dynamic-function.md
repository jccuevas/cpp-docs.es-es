---
title: "3.1.8 omp_get_dynamic Function | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.8 omp_get_dynamic Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función de **omp\_get\_dynamic** devuelve un valor distinto de cero si el ajuste dinámico de subprocesos está habilitado, y devuelve 0 en caso contrario.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_dynamic(void);  
```  
  
 Si la implementación no implementa el ajuste dinámico de subprocesos, esta función siempre devuelve 0.  
  
## referencias cruzadas:  
  
-   Para obtener una descripción del ajuste dinámico de subprocesos, vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en la página 39.