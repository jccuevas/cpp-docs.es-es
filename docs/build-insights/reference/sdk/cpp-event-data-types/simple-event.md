---
title: Clase SimpleEvent
description: Referencia de clase SimpleEvent del SDK de Compilación de C++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 414ff5c1af99acc612384c1ae39f6e12ab051275
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324362"
---
# <a name="simpleevent-class"></a>Clase SimpleEvent

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `SimpleEvent` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con cualquier evento simple. Consulte la tabla de [eventos](../event-table.md) para ver todos `SimpleEvent` los eventos que puede coincidir con la clase.

## <a name="syntax"></a>Sintaxis

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados `SimpleEvent` de su clase base [Event,](event.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[SimpleEvent](#simple-event)

## <a name="simpleevent"></a><a name="simple-event"></a>SimpleEvent

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Cualquier evento simple.

::: moniker-end
