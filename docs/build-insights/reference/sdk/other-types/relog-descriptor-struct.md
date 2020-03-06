---
title: Estructura de RELOG_DESCRIPTOR
description: El C++ SDK de Build insights RELOG_DESCRIPTOR referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6f20835ed6535dd05def629200c113772e8f077
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333975"
---
# <a name="relog_descriptor-structure"></a>Estructura de RELOG_DESCRIPTOR

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura de `RELOG_DESCRIPTOR` se usa con las funciones [RelogA](../functions/relog-a.md) y [RelogW](../functions/relog-w.md) . Describe cómo se debe reregistrar un seguimiento de seguimiento de eventos para Windows (ETW).

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | El número de pasos de análisis que se deben realizar sobre el seguimiento de ETW durante la fase de análisis de la sesión de reregistro. |
| `AnalysisCallbacks` | Objeto [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) que especifica las funciones a las que se va a llamar durante la fase de análisis de la sesión de reinicio. |
| `RelogCallbacks` | Objeto [RELOG_CALLBACKS](relog-callbacks-struct.md) que especifica las funciones a las que se va a llamar durante la fase de reregistro de la sesión de reinicio. |
| `SystemEventsRetentionFlags` | Una máscara de [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) que especifica qué eventos ETW del sistema mantener en el seguimiento que se ha reiniciado. |
| `AnalysisContext` | Contexto proporcionado por el usuario que se pasa como argumento a todas las funciones de devolución de llamada especificadas en `AnalysisCallbacks` |
| `RelogContext` | Contexto proporcionado por el usuario que se pasa como argumento a todas las funciones de devolución de llamada especificadas en `RelogCallbacks` |

## <a name="remarks"></a>Comentarios

El usuario controla el reinicio de los eventos ETW durante una sesión de reregistro a través de las funciones de devolución de llamada especificadas en `RelogCallbacks`. Sin embargo, los eventos ETW del sistema, como los ejemplos de CPU, no se reenvían a estas funciones de devolución de llamada. Utilice el campo `SystemEventsRetentionFlags` para controlar el registro de los eventos ETW del sistema.

Las estructuras `AnalysisCallbacks` y `RelogCallbacks` solo aceptan punteros a funciones no miembro. Puede evitar esta limitación si las establece en un puntero de objeto. Este puntero de objeto se pasará como argumento a todas las funciones de devolución de llamada que no son miembros. Utilice este puntero para llamar a funciones miembro desde dentro de las funciones de devolución de llamada que no son miembros.

La fase de análisis de una sesión de reregistro siempre se ejecuta antes de la fase de reregistro.

::: moniker-end
