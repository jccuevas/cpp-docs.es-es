---
title: Constantes de TRACING_SESSION_SYSTEM_EVENT_FLAGS
description: El C++ SDK de Build insights TRACING_SESSION_SYSTEM_EVENT_FLAGS referencia de constantes.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce0b0ea373ec53f0d5bcf228269299d69b49bb95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333999"
---
# <a name="tracing_session_system_event_flags-constants"></a>Constantes de TRACING_SESSION_SYSTEM_EVENT_FLAGS

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Las constantes de `TRACING_SESSION_SYSTEM_EVENT_FLAGS` se usan para describir los eventos del sistema que se van a recopilar durante un seguimiento. Úselos para inicializar el campo `SystemEventFlags` de la estructura de [TRACING_SESSION_OPTIONS](tracing-session-options-struct.md) .

## <a name="syntax"></a>Sintaxis

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Miembros

| Name | Eventos activados por esta marca |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Este marcador se activa de forma predeterminada mediante C++ el SDK de Build Insights, incluso si no se especifica explícitamente. Habilita los eventos básicos del sistema que son necesarios C++ para que la información de compilación funcione correctamente. Los eventos habilitados por esta marca proporcionan información sobre los procesos, los subprocesos y la carga de imágenes. Estos eventos no se pueden deshabilitar. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Ejemplos de CPU |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Esta marca activa todos los eventos del sistema. |

::: moniker-end
