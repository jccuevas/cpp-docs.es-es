---
title: estructura RELOG_DESCRIPTOR
description: El SDK de C++ Build Insights RELOG_DESCRIPTOR referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c3aee49fe9f609ca37082693ddcfd5e838cc96a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328936"
---
# <a name="relog_descriptor-structure"></a>estructura RELOG_DESCRIPTOR

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `RELOG_DESCRIPTOR` estructura se utiliza con las funciones [RelogA](../functions/relog-a.md) y [RelogW.](../functions/relog-w.md) Describe cómo se debe volver a registrar un seguimiento de seguimiento de eventos para Windows (ETW).

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
| `NumberOfAnalysisPasses` | El número de pasadas de análisis que se deben realizar a través del seguimiento ETW durante la fase de análisis de la sesión de reregistro. |
| `AnalysisCallbacks` | Un [objeto ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) que especifica qué funciones llamar durante la fase de análisis de la sesión de reregistro. |
| `RelogCallbacks` | Objeto [RELOG_CALLBACKS](relog-callbacks-struct.md) que especifica qué funciones se deben llamar durante la fase de reregistro de la sesión de reregistro. |
| `SystemEventsRetentionFlags` | Una máscara de bits [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) que especifica qué eventos ETW del sistema se deben mantener en el seguimiento reiniciado. |
| `AnalysisContext` | Un contexto proporcionado por el usuario que se pasa como argumento a todas las funciones de devolución de llamada especificadas en`AnalysisCallbacks` |
| `RelogContext` | Un contexto proporcionado por el usuario que se pasa como argumento a todas las funciones de devolución de llamada especificadas en`RelogCallbacks` |

## <a name="remarks"></a>Observaciones

El registro de eventos ETW durante una sesión de reregistro es `RelogCallbacks`controlado por el usuario a través de las funciones de devolución de llamada especificadas en . Sin embargo, los eventos ETW del sistema, como los ejemplos de CPU, no se reenvían a estas funciones de devolución de llamada. Utilice `SystemEventsRetentionFlags` el campo para controlar el reregistro de eventos ETW del sistema.

Las `AnalysisCallbacks` `RelogCallbacks` estructuras y solo aceptan punteros a funciones que no son miembros. Puede evitar esta limitación estableciéndolas en un puntero de objeto. Este puntero de objeto se pasará como argumento a todas las funciones de devolución de llamada que no sean miembros. Utilice este puntero para llamar a funciones miembro desde dentro de las funciones de devolución de llamada que no son miembros.

La fase de análisis de una sesión de reregistro siempre se ejecuta antes de la fase de recorrección.

::: moniker-end
