---
title: omp_unset_lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_unset_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_unset_lock OpenMP function
ms.assetid: 68fcb728-040b-4bad-979e-aaecb9097a4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b0b7b796ce5db6cfe23eea3608db171ff38e263
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059074"
---
# <a name="ompunsetlock"></a>omp_unset_lock
Libera un bloqueo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void omp_unset_lock(  
   omp_lock_t *lock  
);  
```  
  
### <a name="parameters"></a>Parámetros
  
*lock*<br/>
Una variable de tipo [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) que se inicializó con [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md), que se poseen el subproceso y ejecuta en la función.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [3.2.4 omp_unset_lock y omp_unset_nest_lock funciones](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) para obtener un ejemplo del uso de `omp_unset_lock`.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../../parallel/openmp/reference/openmp-functions.md)