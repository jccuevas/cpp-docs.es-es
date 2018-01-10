---
title: OMP_DYNAMIC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_DYNAMIC
dev_langs: C++
helpviewer_keywords: OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 900f3e4ddd0e9901e72ed65f12bc036d87a6956e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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