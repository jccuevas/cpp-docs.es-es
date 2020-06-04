---
title: Clase Pass1
description: Referencia de clase Pass1 del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Pass1
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 039c2cc92b8461009c235baa7e49484eb2a4f49f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324417"
---
# <a name="pass1-class"></a>Clase Pass1

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `Pass1` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [PASS1.](../event-table.md#pass1)

## <a name="syntax"></a>Sintaxis

```cpp
class Pass1 : public LinkerPass
{
public:
    Pass1(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `Pass1` su clase base [LinkerPass,](linker-pass.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[Pass1](#pass1)

## <a name="pass1"></a><a name="pass1"></a>Pass1

```cpp
Pass1(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [PASS1.](../event-table.md#pass1)

::: moniker-end
