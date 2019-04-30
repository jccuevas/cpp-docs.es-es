---
title: Enumeraciones &lt;atomic&gt;
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: 03247f6abd01b00fbbed3b33016cd4a12d8a13f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377294"
---
# <a name="ltatomicgt-enums"></a>Enumeraciones &lt;atomic&gt;

## <a name="memory_order_enum"></a>  memory_order (Enumeración)

Proporciona nombres simbólicos para las operaciones de sincronización en ubicaciones de memoria. Estas operaciones afectan a cómo las asignaciones de un subproceso se hacen visibles en otro.

```cpp
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```

### <a name="enumeration-members"></a>Miembros de enumeración

|||
|-|-|
|`memory_order_relaxed`|No se necesita ninguna ordenación.|
|`memory_order_consume`|Una operación de carga actúa como una operación de uso en la ubicación de memoria.|
|`memory_order_acquire`|Una operación de carga actúa como una operación de adquisición en la ubicación de memoria.|
|`memory_order_release`|Una operación de almacenamiento actúa como una operación de liberación en la ubicación de memoria.|
|`memory_order_acq_rel`|Combina `memory_order_acquire` y `memory_order_release`.|
|`memory_order_seq_cst`|Combina `memory_order_acquire` y `memory_order_release`. Los accesos a memoria marcados como `memory_order_seq_cst` debe ser secuencialmente coherentes.|

## <a name="see-also"></a>Vea también

[\<atomic>](../standard-library/atomic.md)<br/>
