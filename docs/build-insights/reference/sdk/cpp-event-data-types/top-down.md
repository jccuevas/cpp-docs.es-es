---
title: Clase TopDown
description: La referencia de clase TopDown del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TopDown
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7c0c957fa17daaec34710debeda634192c63d1da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324207"
---
# <a name="topdown-class"></a>Clase TopDown

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `TopDown` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [TOP_DOWN.](../event-table.md#top-down)

## <a name="syntax"></a>Sintaxis

```cpp
class TopDown : public Activity
{
public:
    TopDown(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados `TopDown` de su clase base [Activity,](activity.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[TopDown](#top-down)

## <a name="topdown"></a><a name="top-down"></a>TopDown

```cpp
TopDown(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un [evento TOP_DOWN.](../event-table.md#top-down)

::: moniker-end
