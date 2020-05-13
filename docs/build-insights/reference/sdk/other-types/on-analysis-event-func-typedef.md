---
title: OnAnalysisEventFunc typedef
description: La referencia de tipodef del SDK de C++ Build Insights OnAnalysisEventFunc.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eacd174279caff0db22586d5e40d3a866afc4459
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329124"
---
# <a name="onanalysiseventfunc-typedef"></a>OnAnalysisEventFunc typedef

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `OnAnalysisEventFunc` definición de tipo es una de las firmas de función utilizadas en la estructura [ANALYSIS_CALLBACKS.](analysis-callbacks-struct.md)

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parámetros

*eventStack*\
La pila de eventos para el evento actual. Para obtener más información sobre las pilas de eventos, consulte [Eventos](../event-table.md).

*callbackContext*\
El valor de contexto que se estableció para esta devolución de llamada en [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) o [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Valor devuelto

Un [valor CALLBACK_CODE](callback-code-enum.md) que controla lo que debe suceder a continuación.

::: moniker-end
