---
title: Estructura de TRACING_SESSION_OPTIONS
description: El C++ SDK de Build insights TRACING_SESSION_OPTIONS referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3f02552d5df4ffe71bc4be5c46e4b5239f25d73c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333873"
---
# <a name="tracing_session_options-structure"></a>Estructura de TRACING_SESSION_OPTIONS

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura de `TRACING_SESSION_OPTIONS` se utiliza al inicializar una estructura de [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) o [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Describe los eventos que se capturan durante la recopilación de un seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `SystemEventFlags` | Máscara de máscara que describe los eventos del sistema que se van a capturar. Para obtener más información, vea [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md). |
| `MsvcEventFlags` | Máscara de máscara que describe los eventos MSVC que se van a capturar. Para obtener más información, vea [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md). |

::: moniker-end
