---
title: Clase SimpleEvent
description: Referencia C++ de la clase SIMPLEEVENT del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4c30f81236138328322d8c870d4ad69d9988b49a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334593"
---
# <a name="simpleevent-class"></a>Clase SimpleEvent

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `SimpleEvent` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con cualquier evento simple. Consulte la [tabla de eventos](../event-table.md) para ver todos los eventos que pueden coincidir con la clase `SimpleEvent`.

## <a name="syntax"></a>Sintaxis

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de la clase base de [evento](event.md) , la clase `SimpleEvent` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[SimpleEvent](#simple-event)

## <a name="simple-event"></a>SimpleEvent

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Cualquier evento simple.

::: moniker-end
