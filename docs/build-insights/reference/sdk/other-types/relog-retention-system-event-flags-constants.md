---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS constantes
description: El SDK de C++ Build Insights RELOG_RETENTION_SYSTEM_EVENT_FLAGS referencia de constantes.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7110f809a819357b31951c203c1fa6ac9fb9f42e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323470"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS constantes

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

Las `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` constantes se utilizan para describir qué eventos del sistema se van a mantener en un seguimiento reiniciado. Utilícelos para inicializar el `SystemEventsRetentionFlags` campo de la estructura [RELOG_DESCRIPTOR.](relog-descriptor-struct.md)

## <a name="syntax"></a>Sintaxis

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Mantenga los eventos del sistema de ejemplo de CPU en un seguimiento reiniciado. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Mantenga todos los eventos del sistema en un seguimiento reiniciado. |

## <a name="remarks"></a>Observaciones

::: moniker-end
