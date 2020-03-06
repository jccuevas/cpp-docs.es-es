---
title: Clase InvocationGroup
description: Referencia C++ de la clase INVOCATIONGROUP del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b9a2bbcd2b7649b9b5703adc08ed41b272e10276
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334755"
---
# <a name="invocationgroup-class"></a>Clase InvocationGroup

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `InvocationGroup` se usa con las funciones [MatchEventStack](../functions/match-event-stack.md) y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para buscar coincidencias con grupos que contengan una combinación de eventos [del compilador](../event-table.md#compiler) y del [enlazador](../event-table.md#linker) .

## <a name="syntax"></a>Sintaxis

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su [EventGroup\<invocación\>](event-group.md) clase base, la clase `InvocationGroup` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[InvocationGroup](#invocation-group)

## <a name="invocation-group"></a>InvocationGroup

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Parámetros

\ de *Grupo*
Un grupo que contiene una combinación de eventos del [compilador](../event-table.md#compiler) y del [enlazador](../event-table.md#linker) .

::: moniker-end
