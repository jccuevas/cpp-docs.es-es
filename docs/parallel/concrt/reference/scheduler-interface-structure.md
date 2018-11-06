---
title: scheduler_interface (Estructura)
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 9fa51aa5bd1fdea4eb1c35488654f0b5003e2efe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612776"
---
# <a name="schedulerinterface-structure"></a>scheduler_interface (Estructura)

Interfaz de Scheduler

## <a name="syntax"></a>Sintaxis

```
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[scheduler_interface::Schedule](#schedule)||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`scheduler_interface`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplinterface.h

**Espacio de nombres:** simultaneidad

##  <a name="schedule"></a>  scheduler_interface::Schedule (método)

```
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
