---
title: compartido (OpenMP) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 90491e6e8b415c79e21b4fa518f7e60327ac823e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="shared-openmp"></a>shared (OpenMP)
Especifica que una o más variables deben compartirse entre todos los subprocesos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
shared(var)  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `var`  
 Uno más más variables para compartir. Si se especifica más de una variable, separe los nombres de variable con una coma.  
  
## <a name="remarks"></a>Comentarios  
 Otra manera de compartir variables entre subprocesos es con el [copyprivate](../../../parallel/openmp/reference/copyprivate.md) cláusula.  
  
 `shared` se aplica a las siguientes directivas:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [Secciones](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, consulte [2.7.2.4 compartido](../../../parallel/openmp/2-7-2-4-shared.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [privada](../../../parallel/openmp/reference/private-openmp.md) para obtener un ejemplo del uso de `shared`.  
  
## <a name="see-also"></a>Vea también  
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)