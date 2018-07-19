---
title: compartido (OpenMP) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8287f96f80748272e29b22ed5c43c364f4353b86
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691682"
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