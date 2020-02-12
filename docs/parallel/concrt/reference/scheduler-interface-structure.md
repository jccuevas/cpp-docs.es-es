---
title: scheduler_interface (estructura)
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 36feff80cab1c5d301c009a581b869d5c2bad5e9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142152"
---
# <a name="scheduler_interface-structure"></a>scheduler_interface (estructura)

Interfaz de Scheduler

## <a name="syntax"></a>Sintaxis

```cpp
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[scheduler_interface:: Schedule](#schedule)||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`scheduler_interface`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplinterface. h

**Espacio de nombres:** simultaneidad

## <a name="schedule"></a>scheduler_interface:: Schedule (método)

```cpp
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
