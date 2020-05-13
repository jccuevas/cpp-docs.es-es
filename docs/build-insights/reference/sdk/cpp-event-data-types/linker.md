---
title: Clase de vinculador
description: Referencia de la clase Linker del SDK de C+++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Linker
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e5d4c0c3841377fc2e029c23d5cbbd076c8029cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324595"
---
# <a name="linker-class"></a>Clase de vinculador

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `Linker` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [LINKER.](../event-table.md#linker)

## <a name="syntax"></a>Sintaxis

```cpp
class Linker : public Invocation
{
public:
    Linker(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `Linker` su clase base [Invocation,](invocation.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[Enlazador](#linker)

## <a name="linker"></a><a name="linker"></a>Vinculador

```cpp
Linker(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [LINKER.](../event-table.md#linker)

::: moniker-end
