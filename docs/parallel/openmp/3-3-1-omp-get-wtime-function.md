---
title: "3.3.1 omp_get_wtime Function | Microsoft Docs"
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
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.3.1 omp_get_wtime Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función de `omp_get_wtime` devuelve un valor de doble precisión de punto flotante es igual al tiempo de reloj transcurrido de muro en segundos desde que algo “sincroniza en el último”.  “Tiempo real en el último” es arbitrario, pero se garantiza que no cambiar durante la ejecución del programa de aplicación.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
double omp_get_wtime(void);  
```  
  
 Se espera que la función se utilizará para medir el tiempo transcurrido tal y como se muestra en el ejemplo siguiente:  
  
```  
double start;  
double end;  
start = omp_get_wtime();  
... work to be timed ...  
end = omp_get_wtime();  
printf_s("Work took %f sec. time.\n", end-start);  
```  
  
 Los tiempos devueltos son “storage medir el tiempo” por se significa lo que no se requiere ser global coherente en todos los subprocesos que participan en una aplicación.