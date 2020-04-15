---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS constantes
description: El SDK de C++ Build Insights TRACING_SESSION_SYSTEM_EVENT_FLAGS referencia de constantes.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 264d697cc905eb6b44c8ec7de835a552976f0eb8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323268"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS constantes

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

Las `TRACING_SESSION_SYSTEM_EVENT_FLAGS` constantes se utilizan para describir qué eventos del sistema se recopilarán durante un seguimiento. Utilícelos para inicializar el `SystemEventFlags` campo de la estructura [TRACING_SESSION_OPTIONS.](tracing-session-options-struct.md)

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

| Nombre | Eventos activados por esta bandera |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | El SDK de C++ Build Insights activa esta marca de forma predeterminada incluso si no se especifica explícitamente. Permite que los eventos básicos del sistema que requieren C++ Build Insights funcionen correctamente. Los eventos habilitados por esta marca proporcionan información sobre los procesos, los subprocesos y la carga de imágenes. No puede deshabilitar estos eventos. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Muestras de CPU |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Esta marca activa todos los eventos del sistema. |

::: moniker-end
