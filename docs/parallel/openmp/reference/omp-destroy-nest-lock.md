---
title: omp_destroy_nest_lock | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_destroy_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_nest_lock OpenMP function
ms.assetid: 0ab1352b-668f-43dd-b441-31ec4cc53e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a01ff1b0e8b37a9bd8d380b6e0e59794412e51f8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695023"
---
# <a name="ompdestroynestlock"></a>omp_destroy_nest_lock
Anula la inicialización de un bloqueo anidable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void omp_destroy_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `lock`  
 Una variable de tipo [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) que se inicializó con [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md).  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [3.2.2 omp_destroy_lock y omp_destroy_nest_lock funciones](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) para obtener un ejemplo del uso de `omp_destroy_nest_lock`.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../../parallel/openmp/reference/openmp-functions.md)