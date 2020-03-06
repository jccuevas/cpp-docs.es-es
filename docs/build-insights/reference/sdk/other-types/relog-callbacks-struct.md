---
title: Estructura de RELOG_CALLBACKS
description: El C++ SDK de Build insights RELOG_CALLBACKS referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5dbed196e6cafaa301b6e07cd0f5546a0f4d563
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333987"
---
# <a name="relog_callbacks-structure"></a>Estructura de RELOG_CALLBACKS

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura de `RELOG_CALLBACKS` se utiliza al inicializar un objeto [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Especifica las funciones a las que se debe llamar durante el reinicio del registro de un seguimiento de seguimiento de eventos para Windows (ETW).

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
| `OnSimpleEvent` | Se llama para procesar un evento simple. |
| `OnTraceInfo` | Se le llama una vez al principio del paso de registro, una vez que se ha llamado a `OnBeginReloggingPass`. |
| `OnBeginRelogging` | Se llama al iniciar una sesión de reinicio de sesión antes de que se haya iniciado el paso de registro. |
| `OnEndRelogging` | Se llama al finalizar una sesión de reregistro, una vez finalizada la fase de reregistro. |
| `OnBeginReloggingPass` | Se llama cuando se inicia el paso de registro, antes de procesar cualquier evento. |
| `OnEndReloggingPass` | Se llama al finalizar el paso de registro, después de procesar todos los eventos. |

## <a name="remarks"></a>Comentarios

Todos los miembros de la estructura `RELOG_CALLBACKS` deben apuntar a una función válida. Para obtener más información sobre las firmas de funciones aceptadas, vea [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)y [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
