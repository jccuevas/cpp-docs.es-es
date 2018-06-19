---
title: 3.3.1 omp_get_wtime (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d71296d23df72464ed730713566c95e2403760a1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689498"
---
# <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime (Función)
El `omp_get_wtime` función devuelve un valor de punto flotante de precisión doble igual que el tiempo de reloj transcurrido en segundos desde alguna "hora del pasado".  El "tiempo en el pasado" real es arbitrario, pero se garantiza que no cambia durante la ejecución del programa de aplicación. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
double omp_get_wtime(void);  
```  
  
 Se prevé que se utilizará la función para medir los tiempos transcurridos tal como se muestra en el ejemplo siguiente:  
  
```  
double start;  
double end;  
start = omp_get_wtime();  
... work to be timed ...  
end = omp_get_wtime();  
printf_s("Work took %f sec. time.\n", end-start);  
```  
  
 Los tiempos de devueltos son "veces por subproceso" por la que está destinada a que no tienen que ser globalmente coherente en todos los subprocesos que participan en una aplicación.