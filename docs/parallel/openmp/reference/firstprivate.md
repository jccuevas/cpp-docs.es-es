---
title: firstprivate | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- firstprivate
dev_langs:
- C++
helpviewer_keywords:
- firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0438d98467b7843b6f70e0d075dc3b61375c48ca
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="firstprivate"></a>firstprivate
Especifica que cada subproceso debe tener su propia instancia de una variable, y que se debe inicializar la variable con el valor de la variable, porque existe antes de la construcción paralela.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
firstprivate(var)  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`var`|La variable tener instancias en cada subproceso y que se inicializará con el valor de la variable, porque existe antes de la construcción paralela. Si se especifica más de una variable, separe los nombres de variable con una coma.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="remarks"></a>Comentarios  
 `firstprivate` se aplica a las siguientes directivas:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [Secciones](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [single](../../../parallel/openmp/reference/single.md)  
  
 Para obtener más información, consulte [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo del uso de `firstprivate`, vea el ejemplo de [privada](../../../parallel/openmp/reference/private-openmp.md).  
  
## <a name="see-also"></a>Vea también  
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)