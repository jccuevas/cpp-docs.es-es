---
title: OMP_NESTED | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- OMP_NESTED
dev_langs:
- C++
helpviewer_keywords:
- OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 363a125cb7f9858b1ef4105234344d2a8d35b707
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ompnested"></a>OMP_NESTED
Especifica si está habilitado paralelismo anidado, a menos que paralelismo anidado está habilitado o deshabilitado con `omp_set_nested`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
set OMP_NESTED[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>Comentarios  
 El `OMP_NESTED` variable de entorno puede reemplazarse por la [omp_set_nested ()](../../../parallel/openmp/reference/omp-set-nested.md) (función).  
  
 El valor predeterminado en la implementación de Visual C++ del estándar OpenMP es `OMP_DYNAMIC=FALSE`.  
  
 Para obtener más información, consulte [OMP_NESTED 4.4](../../../parallel/openmp/4-4-omp-nested.md).  
  
## <a name="example"></a>Ejemplo  
 El comando siguiente establece la `OMP_NESTED` variable de entorno a TRUE:  
  
```  
set OMP_NESTED=TRUE  
```  
  
 El comando siguiente muestra la configuración actual de la `OMP_NESTED` variable de entorno:  
  
```  
set OMP_NESTED  
```  
  
## <a name="see-also"></a>Vea también  
 [Variables de entorno](../../../parallel/openmp/reference/openmp-environment-variables.md)