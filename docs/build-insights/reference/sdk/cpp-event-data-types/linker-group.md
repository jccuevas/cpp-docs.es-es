---
title: Clase LinkerGroup
description: Referencia C++ de la clase LINKERGROUP del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 95b0dcc3a771ec07ee60185a79a5ddbc29434b5d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334731"
---
# <a name="linkergroup-class"></a>Clase LinkerGroup

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `LinkerGroup` se usa con las funciones [MatchEventStack](../functions/match-event-stack.md) y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con grupos de eventos del [enlazador](../event-table.md#linker) .

## <a name="syntax"></a>Sintaxis

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su [EventGroup\<vinculador\>](event-group.md) clase base, la clase `LinkerGroup` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[LinkerGroup](#linker-group)

## <a name="linker-group"></a>LinkerGroup

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Parámetros

\ de *Grupo*
Grupo de eventos del [enlazador](../event-table.md#linker) .

::: moniker-end
