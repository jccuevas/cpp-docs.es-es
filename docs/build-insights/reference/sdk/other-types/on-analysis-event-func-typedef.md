---
title: OnAnalysisEventFunc (typedef)
description: La C++ referencia de definición de tipo ONANALYSISEVENTFUNC del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d260f6060e759f315589abda82e31c2c2b95a65e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334065"
---
# <a name="onanalysiseventfunc-typedef"></a>OnAnalysisEventFunc (typedef)

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

El `OnAnalysisEventFunc` typedef es una de las firmas de función utilizadas en la estructura [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) .

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parámetros

\ *eventStack*
Pila de eventos para el evento actual. Para obtener más información sobre las pilas de eventos, vea [eventos](../event-table.md).

\ *callbackContext*
Valor de contexto que se estableció para esta devolución de llamada en [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) o [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Valor devuelto

Un valor [CALLBACK_CODE](callback-code-enum.md) que controla lo que debe ocurrir A continuación.

::: moniker-end
