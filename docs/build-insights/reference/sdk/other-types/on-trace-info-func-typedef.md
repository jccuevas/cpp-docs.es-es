---
title: OnTraceInfoFunc typedef
description: La referencia de tipodef OnTraceInfoFunc del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b987d4db9852c2e52c148bb91015ad414c04d41b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329019"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc typedef

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `OnTraceInfoFunc` definición de tipo es una de las firmas de función utilizadas en las estructuras [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) y [RELOG_CALLBACKS.](relog-callbacks-struct.md)

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parámetros

*traceInfo*\
Objeto [TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md) que contiene información sobre el seguimiento que se está analizando o reregistrando actualmente.

*callbackContext*\
El valor de contexto que se estableció para esta devolución de llamada en [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) o [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Valor devuelto

Un [valor CALLBACK_CODE](callback-code-enum.md) que controla lo que debe suceder a continuación.

::: moniker-end
