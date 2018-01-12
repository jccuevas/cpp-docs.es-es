---
title: Enumeraciones &lt;atomic&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
caps.latest.revision: "11"
helpviewer_keywords: std::memory_order
manager: ghogen
ms.openlocfilehash: 4d0c60a908d795d8bf9fa7643471c6c9f29cc1cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ltatomicgt-enums"></a>Enumeraciones &lt;atomic&gt;
  
##  <a name="memory_order_enum"></a>  memory_order (Enumeración)  
 Proporciona nombres simbólicos para las operaciones de sincronización en ubicaciones de memoria. Estas operaciones afectan a cómo las asignaciones de un subproceso se hacen visibles en otro.  
  
```
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```  
  
### <a name="remarks"></a>Comentarios  
  
|||  
|-|-|  
|`memory_order_relaxed`|No se necesita ninguna ordenación.|  
|`memory_order_consume`|Una operación de carga actúa como una operación de uso en la ubicación de memoria.|  
|`memory_order_acquire`|Una operación de carga actúa como una operación de adquisición en la ubicación de memoria.|  
|`memory_order_release`|Una operación de almacenamiento actúa como una operación de liberación en la ubicación de memoria.|  
|`memory_order_acq_rel`|Combina `memory_order_acquire` y `memory_order_release`.|  
|`memory_order_seq_cst`|Combina `memory_order_acquire` y `memory_order_release`. Los accesos a memoria marcados como `memory_order_seq_cst` debe ser secuencialmente coherentes.|  
  
## <a name="see-also"></a>Vea también  
 [\<atomic>](../standard-library/atomic.md)



