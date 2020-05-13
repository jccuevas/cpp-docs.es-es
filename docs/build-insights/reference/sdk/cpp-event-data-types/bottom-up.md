---
title: Clase BottomUp
description: Referencia de clase BottomUp del SDK de C+++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BottomUp
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1cfe25aaa5736b9e2ba55a577e64958a6b9f113b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325217"
---
# <a name="bottomup-class"></a>Clase BottomUp

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `BottomUp` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [BOTTOM_UP.](../event-table.md#bottom-up)

## <a name="syntax"></a>Sintaxis

```cpp
class BottomUp : public Activity
{
public:
    BottomUp(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados `BottomUp` de su clase base [Activity,](activity.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[BottomUp](#bottom-up)

## <a name="bottomup"></a><a name="bottom-up"></a>BottomUp

```cpp
BottomUp(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [BOTTOM_UP.](../event-table.md#bottom-up)

::: moniker-end
