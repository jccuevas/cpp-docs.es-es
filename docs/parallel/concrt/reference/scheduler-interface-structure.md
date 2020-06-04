---
title: scheduler_interface (Estructura)
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: da2ebc2f9c2878baefcfa792bac08f420dbbb281
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358782"
---
# <a name="scheduler_interface-structure"></a>scheduler_interface (Estructura)

Interfaz de Scheduler

## <a name="syntax"></a>Sintaxis

```cpp
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[scheduler_interface::programa](#schedule)||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`scheduler_interface`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplinterface.h

**Espacio de nombres:** simultaneidad

## <a name="scheduler_interfaceschedule-method"></a><a name="schedule"></a>scheduler_interface::método de programación Método

```cpp
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)
