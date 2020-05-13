---
title: Clase WholeProgramAnalysis
description: La referencia de la clase WholeProgramAnalysis del SDK de Compilación de C++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- WholeProgramAnalysis
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c68441b7da09f9880bbb2f97544b1ad8da2f631f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324117"
---
# <a name="wholeprogramanalysis-class"></a>Clase WholeProgramAnalysis

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `WholeProgramAnalysis` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [WHOLE_PROGRAM_ANALYSIS.](../event-table.md#whole-program-analysis)

## <a name="syntax"></a>Sintaxis

```cpp
class WholeProgramAnalysis : public Activity
{
public:
    WholeProgramAnalysis(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados `WholeProgramAnalysis` de su clase base [Activity,](activity.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[WholeProgramAnalysis](#whole-program-analysis)

## <a name="wholeprogramanalysis"></a><a name="whole-program-analysis"></a>WholeProgramAnalysis

```cpp
WholeProgramAnalysis(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [WHOLE_PROGRAM_ANALYSIS.](../event-table.md#whole-program-analysis)

::: moniker-end
