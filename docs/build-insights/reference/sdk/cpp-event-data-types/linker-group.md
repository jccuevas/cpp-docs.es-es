---
title: Clase LinkerGroup
description: La referencia de clase LinkerGroup del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c59d62938e5bd7b839ad12a321a03510e708e0fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324656"
---
# <a name="linkergroup-class"></a>Clase LinkerGroup

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `LinkerGroup` clase se utiliza con las funciones [MatchEventStack](../functions/match-event-stack.md) y [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilícelo para hacer coincidir grupos de eventos [LINKER.](../event-table.md#linker)

## <a name="syntax"></a>Sintaxis

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su `LinkerGroup` clase base [EventGroup\<\> Linker,](event-group.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[LinkerGroup](#linker-group)

## <a name="linkergroup"></a><a name="linker-group"></a>LinkerGroup

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Parámetros

*Grupo*\
Un grupo de eventos [LINKER.](../event-table.md#linker)

::: moniker-end
