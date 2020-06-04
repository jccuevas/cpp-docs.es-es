---
title: estructura RELOG_CALLBACKS
description: El SDK de C++ Build Insights RELOG_CALLBACKS referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 60e7db81a48731090a23b82332704a79a51e97df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328969"
---
# <a name="relog_callbacks-structure"></a>estructura RELOG_CALLBACKS

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `RELOG_CALLBACKS` estructura se utiliza al inicializar un objeto [RELOG_DESCRIPTOR.](relog-descriptor-struct.md) Especifica qué funciones llamar durante el reregistro de un seguimiento de seguimiento de eventos para Windows (ETW).

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct RELOG_CALLBACKS_TAG
{
    OnRelogEventFunc        OnStartActivity;
    OnRelogEventFunc        OnStopActivity;
    OnRelogEventFunc        OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginRelogging;
    OnBeginEndPassFunc      OnEndRelogging;
    OnBeginEndPassFunc      OnBeginReloggingPass;
    OnBeginEndPassFunc      OnEndReloggingPass;
} RELOG_CALLBACKS;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `OnStartActivity` | Se llama para procesar un evento de inicio de actividad. |
| `OnStopActivity` | Se llama para procesar un evento de detención de actividad. |
| `OnSimpleEvent` | Llamado para procesar un evento simple. |
| `OnTraceInfo` | Llamado una vez al principio del `OnBeginReloggingPass` pase de relogging, después de haber sido llamado. |
| `OnBeginRelogging` | Se llama al iniciar una sesión de reregistro, antes de que el pase de reregistro haya comenzado. |
| `OnEndRelogging` | Se llama al finalizar una sesión de reregistro, después de que el pase de reregistro haya finalizado. |
| `OnBeginReloggingPass` | Se llama al iniciar el paso de reregistro, antes de procesar cualquier evento. |
| `OnEndReloggingPass` | Se llama al finalizar el paso de reregistro, después de procesar todos los eventos. |

## <a name="remarks"></a>Observaciones

Todos los `RELOG_CALLBACKS` miembros de la estructura deben apuntar a una función válida. Para obtener más información sobre las firmas de función aceptadas, vea [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)y [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
