---
title: lastprivate | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: lastprivate
dev_langs: C++
helpviewer_keywords: lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ad36a68078856706a4d1d994e72fd001c36dbaf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
 `lastprivate`se aplica a las siguientes directivas:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [secciones](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, consulte [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [programación](../../../parallel/openmp/reference/schedule.md) para obtener un ejemplo del uso de `lastprivate` cláusula.  
  
## <a name="see-also"></a>Vea también  
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)