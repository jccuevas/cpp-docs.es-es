---
title: Clase FrontEndFileGroup
description: Referencia C++ de la clase FRONTENDFILEGROUP del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 343a5a0d798d6c719088bd49668e70b10fba6d1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334833"
---
# <a name="frontendfilegroup-class"></a>Clase FrontEndFileGroup

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `FrontEndFileGroup` se usa con las funciones [MatchEventStack](../functions/match-event-stack.md) y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para hacer coincidir grupos de eventos de [FRONT_END_FILE](../event-table.md#front-end-file) .

## <a name="syntax"></a>Sintaxis

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su [EventGroup\<FrontEndFile\>](event-group.md) clase base, la clase `FrontEndFileGroup` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[FrontEndFileGroup](#front-end-file-group)

## <a name="front-end-file-group"></a>FrontEndFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>Parámetros

\ de *Grupo*
Grupo de eventos de [FRONT_END_FILE](../event-table.md#front-end-file) .

::: moniker-end
