---
title: OMP_SCHEDULE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5052aaadc673e38a844ea5b0d1e11ff3a96f3fbe
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691760"
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
 Especifica el tamaño de las iteraciones. `size` Debe ser un entero positivo. El valor predeterminado es 1, excepto cuando `type` es estático. No es válido cuando `type` es `runtime`.  
  
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