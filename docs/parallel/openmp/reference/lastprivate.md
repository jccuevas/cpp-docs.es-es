---
title: lastprivate | Microsoft Docs
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
ms.openlocfilehash: c87dfc47f7f2554e75567a1de4ea9cb2e06eaa00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028199"
---
# <a name="lastprivate"></a>lastprivate
Especifica que versión envolvente del contexto de la variable se establece igual que la versión privada de cualquier subproceso que ejecuta la última iteración (construcción de bucle for) o la última sección (#pragma secciones).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
lastprivate(var)  
```  
  
### <a name="parameters"></a>Parámetros
  
*var*<br/>
La variable que se establece igual que la versión privada de cualquier subproceso que ejecuta la última iteración (construcción de bucle for) o la última sección (#pragma secciones).  
  
## <a name="remarks"></a>Comentarios  
 `lastprivate` se aplica a las siguientes directivas:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Secciones](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, consulte [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte [programación](../../../parallel/openmp/reference/schedule.md) para obtener un ejemplo del uso de `lastprivate` cláusula.  
  
## <a name="see-also"></a>Vea también  
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)