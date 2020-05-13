---
title: Clase InvocationGroup
description: La referencia de clase InvocationGroup del SDK de Build Insights de C+++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff5a73d5304a21c314c0fc5ce442e0ffc23b28fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324691"
---
# <a name="invocationgroup-class"></a>Clase InvocationGroup

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `InvocationGroup` clase se utiliza con las funciones [MatchEventStack](../functions/match-event-stack.md) y [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilícelo para que coincida con grupos que contengan una combinación de eventos [COMPILER](../event-table.md#compiler) y [LINKER.](../event-table.md#linker)

## <a name="syntax"></a>Sintaxis

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su `InvocationGroup` clase base [EventGroup\<\> Invocation,](event-group.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[InvocationGroup](#invocation-group)

## <a name="invocationgroup"></a><a name="invocation-group"></a>InvocationGroup

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Parámetros

*Grupo*\
Un grupo que contiene una combinación de eventos [COMPILER](../event-table.md#compiler) y [LINKER.](../event-table.md#linker)

::: moniker-end
