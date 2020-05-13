---
title: Clase ImpLibOutput
description: La referencia de clase ImpLibOutput del SDK de C+++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ImpLibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 98905dfe75484e98e14a0fa575e75fe3ab284559
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324699"
---
# <a name="impliboutput-class"></a>Clase ImpLibOutput

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `ImpLibOutput` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [IMP_LIB_OUTPUT.](../event-table.md#imp-lib-output)

## <a name="syntax"></a>Sintaxis

```cpp
class ImpLibOutput : public FileOutput
{
public:
    ImpLibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `ImpLibOutput` su clase base [FileOutput,](file-output.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[ImpLibOutput](#imp-lib-output)

## <a name="impliboutput"></a><a name="imp-lib-output"></a>ImpLibOutput

```cpp
ImpLibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un [evento IMP_LIB_OUTPUT.](../event-table.md#imp-lib-output)

::: moniker-end
