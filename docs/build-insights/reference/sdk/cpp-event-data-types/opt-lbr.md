---
title: Clase OptLBR
description: Referencia de clase OptLBR del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptLBR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4cbd87134741d6fc09521f94bfdfbc099cb426a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324455"
---
# <a name="optlbr-class"></a>Clase OptLBR

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `OptLBR` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [OPT_LBR.](../event-table.md#opt-lbr)

## <a name="syntax"></a>Sintaxis

```cpp
class OptLBR : public Activity
{
public:
    OptLBR(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados `OptLBR` de su clase base [Activity,](activity.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[OptLBR](#opt-lbr)

## <a name="optlbr"></a><a name="opt-lbr"></a>OptLBR

```cpp
OptLBR(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [OPT_LBR.](../event-table.md#opt-lbr)

::: moniker-end
