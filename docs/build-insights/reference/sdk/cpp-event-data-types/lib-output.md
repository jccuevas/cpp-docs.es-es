---
title: Clase LibOutput
description: Referencia a la clase LibOutput del SDK de C+++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fda7b471759a9c49937214bb2176473226668776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324620"
---
# <a name="liboutput-class"></a>Clase LibOutput

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `LibOutput` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [LIB_OUTPUT.](../event-table.md#lib-output)

## <a name="syntax"></a>Sintaxis

```cpp
class LibOutput : public FileOutput
{
public:
    LibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `LibOutput` su clase base [FileOutput,](file-output.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[LibOutput](#lib-output)

## <a name="liboutput"></a><a name="lib-output"></a>LibOutput

```cpp
LibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [LIB_OUTPUT.](../event-table.md#lib-output)

::: moniker-end
