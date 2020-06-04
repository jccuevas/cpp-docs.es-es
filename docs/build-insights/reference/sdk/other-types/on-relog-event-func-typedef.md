---
title: OnRelogEventFunc typedef
description: La referencia de tipodef del SDK de C++ Build Insights OnRelogEventFunc.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2df8646d530c089b1239978d716b2b619a5b4b61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329076"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc typedef

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `OnRelogEventFunc` definición de tipo es una de las firmas de función utilizadas en la estructura [RELOG_CALLBACKS.](relog-callbacks-struct.md)

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parámetros

*eventStack*\
La pila de eventos para el evento actual. Para obtener más información sobre las pilas de eventos, consulte [Eventos](../event-table.md).

*relogSession*\
El puntero de sesión de reregistro que se va a utilizar al llamar a [InjectEvent](../functions/inject-event.md).

*callbackContext*\
El valor de contexto que se estableció para esta devolución de llamada en [RELOG_DESCRIPTOR](analysis-descriptor-struct.md).

### <a name="return-value"></a>Valor devuelto

Un [valor CALLBACK_CODE](callback-code-enum.md) que controla lo que debe suceder a continuación.

::: moniker-end
