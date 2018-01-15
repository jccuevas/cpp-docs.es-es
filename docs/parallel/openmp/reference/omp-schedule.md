---
title: OMP_SCHEDULE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_SCHEDULE
dev_langs: C++
helpviewer_keywords: OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8aa1406b490128657da19f7c48c958d382850d96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ompschedule"></a>OMP_SCHEDULE
Modifica el comportamiento de la [programación](../../../parallel/openmp/reference/schedule.md) cláusula cuando `schedule(runtime)` se especifica en un `for` o `parallel for` directiva.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `size` (opcional)  
 Especifica el tamaño de las iteraciones. `size`debe ser un entero positivo. El valor predeterminado es 1, excepto cuando `type` es estático. No es válido cuando `type` es `runtime`.  
  
 `type`  
 El tipo de programación:  
  
-   `dynamic`  
  
-   `guided`  
  
-   `runtime`  
  
-   `static`  
  
## <a name="remarks"></a>Comentarios  
 El valor predeterminado en la implementación de Visual C++ del estándar OpenMP es `OMP_SCHEDULE=static,0`.  
  
 Para obtener más información, consulte [OMP_SCHEDULE 4.1](../../../parallel/openmp/4-1-omp-schedule.md).  
  
## <a name="example"></a>Ejemplo  
 El comando siguiente establece la **OMP_SCHEDULE** variable de entorno:  
  
```  
set OMP_SCHEDULE="guided,2"  
```  
  
 El comando siguiente muestra la configuración actual de la **OMP_SCHEDULE** variable de entorno:  
  
```  
set OMP_SCHEDULE  
```  
  
## <a name="see-also"></a>Vea también  
 [Variables de entorno](../../../parallel/openmp/reference/openmp-environment-variables.md)