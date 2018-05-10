---
title: lastprivate | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aaf80e3061877c42154ab9ee5ccd30f47f17135
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="lastprivate"></a>lastprivate
Especifica que la versión del contexto envolvente de la variable se establece igual que la versión privada del cualquier subproceso ejecuta la última iteración (construcción de bucle for) o la última sección (#pragma secciones).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
lastprivate(var)  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `var`  
 La variable que se establece igual que la versión privada del cualquier subproceso ejecuta la última iteración (construcción de bucle for) o la última sección (#pragma secciones).  
  
## <a name="remarks"></a>Comentarios  
 `lastprivate` se aplica a las siguientes directivas:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Secciones](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, consulte [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [programación](../../../parallel/openmp/reference/schedule.md) para obtener un ejemplo del uso de `lastprivate` cláusula.  
  
## <a name="see-also"></a>Vea también  
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)