---
title: omp_unset_nest_lock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_unset_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_unset_nest_lock OpenMP function
ms.assetid: 1721d061-3f9c-45d7-b479-a665cd0a121d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4facb30dc5f869b5be83f4221ef06312eba41251
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ompunsetnestlock"></a>omp_unset_nest_lock
Libera un bloqueo anidable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void omp_unset_nest_lock(   
   omp_nest_lock_t *lock   
);  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `lock`  
 Una variable de tipo [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) que se inicializó con [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md), posee el subproceso y ejecuta en la función.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [3.2.4 omp_unset_lock y omp_unset_nest_lock funciones](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) para obtener un ejemplo del uso de `omp_unset_nest_lock`.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../../parallel/openmp/reference/openmp-functions.md)