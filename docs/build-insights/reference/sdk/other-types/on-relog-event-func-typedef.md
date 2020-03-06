---
title: OnRelogEventFunc (typedef)
description: La C++ referencia de definición de tipo ONRELOGEVENTFUNC del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 619f9a142ad19a7809b867eda93f2db634825a8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334029"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc (typedef)

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

El `OnRelogEventFunc` typedef es una de las firmas de función utilizadas en la estructura [RELOG_CALLBACKS](relog-callbacks-struct.md) .

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parámetros

\ *eventStack*
Pila de eventos para el evento actual. Para obtener más información sobre las pilas de eventos, vea [eventos](../event-table.md).

\ *relogSession*
Puntero de sesión de reregistro que se va a usar al llamar a [InjectEvent](../functions/inject-event.md).

\ *callbackContext*
Valor de contexto que se estableció para esta devolución de llamada en [RELOG_DESCRIPTOR](analysis-descriptor-struct.md).

### <a name="return-value"></a>Valor devuelto

Un valor [CALLBACK_CODE](callback-code-enum.md) que controla lo que debe ocurrir A continuación.

::: moniker-end
