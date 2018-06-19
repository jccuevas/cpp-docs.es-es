---
title: OMP_DYNAMIC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de4a81d861bf72943a67356577da37c36df63f69
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695816"
---
# <a name="ompdynamic"></a>OMP_DYNAMIC
Especifica si el tiempo de ejecución de OpenMP puede ajustar el número de subprocesos en una región paralela.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
set OMP_DYNAMIC[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>Comentarios  
 El `OMP_DYNAMIC` variable de entorno puede reemplazarse por la [omp_set_dynamic ()](../../../parallel/openmp/reference/omp-set-dynamic.md) (función).  
  
 El valor predeterminado en la implementación de Visual C++ del estándar OpenMP es `OMP_DYNAMIC=FALSE`.  
  
 Para obtener más información, consulte [OMP_DYNAMIC 4.3](../../../parallel/openmp/4-3-omp-dynamic.md).  
  
## <a name="example"></a>Ejemplo  
 El comando siguiente establece la `OMP_DYNAMIC` variable de entorno a TRUE:  
  
```  
set OMP_DYNAMIC=TRUE  
```  
  
 El comando siguiente muestra la configuración actual de la `OMP_DYNAMIC` variable de entorno:  
  
```  
set OMP_DYNAMIC  
```  
  
## <a name="see-also"></a>Vea también  
 [Variables de entorno](../../../parallel/openmp/reference/openmp-environment-variables.md)