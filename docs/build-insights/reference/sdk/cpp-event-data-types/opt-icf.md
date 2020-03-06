---
title: Clase OptICF
description: Referencia C++ de la clase OPTICF del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptICF
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b7594d573a0e4eaf2e19f306b8a109923ba235dc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334647"
---
# <a name="opticf-class"></a>Clase OptICF

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `OptICF` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [OPT_ICF](../event-table.md#opt-icf) .

## <a name="syntax"></a>Sintaxis

```cpp
class OptICF : public Activity
{
public:
    OptICF(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base de [actividad](activity.md) , la clase `OptICF` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[OptICF](#opt-icf)

## <a name="opt-icf"></a>OptICF

```cpp
OptICF(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [OPT_ICF](../event-table.md#opt-icf) .

::: moniker-end
