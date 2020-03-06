---
title: Constantes de RELOG_RETENTION_SYSTEM_EVENT_FLAGS
description: El C++ SDK de Build insights RELOG_RETENTION_SYSTEM_EVENT_FLAGS referencia de constantes.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 74afc10faa26ba39a669a05aa3e3cabd1a211293
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333969"
---
# <a name="relog_retention_system_event_flags-constants"></a>Constantes de RELOG_RETENTION_SYSTEM_EVENT_FLAGS

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Las constantes de `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` se usan para describir qué eventos del sistema deben conservarse en un seguimiento reiniciado. Úselos para inicializar el campo `SystemEventsRetentionFlags` de la estructura de [RELOG_DESCRIPTOR](relog-descriptor-struct.md) .

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

## <a name="remarks"></a>Comentarios

::: moniker-end
