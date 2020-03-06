---
title: OnTraceInfoFunc (typedef)
description: La C++ referencia de definición de tipo ONTRACEINFOFUNC del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b168d6783b31454f6a2837bcad1fc81199ce9054
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333993"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc (typedef)

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

El `OnTraceInfoFunc` typedef es una de las firmas de función usadas en las estructuras [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) y [RELOG_CALLBACKS](relog-callbacks-struct.md) .

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parámetros

\ *traceInfo*
[TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md) objeto que contiene información sobre el seguimiento que se está analizando o reregistrando actualmente.

\ *callbackContext*
Valor de contexto que se estableció para esta devolución de llamada en [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) o [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Valor devuelto

Un valor [CALLBACK_CODE](callback-code-enum.md) que controla lo que debe ocurrir A continuación.

::: moniker-end
