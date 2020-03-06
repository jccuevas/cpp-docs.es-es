---
title: Clase ExpOutput
description: Referencia C++ de la clase EXPOUTPUT del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExpOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bc108096bf2fffba876231bbf522295d0d0dcc0d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334857"
---
# <a name="expoutput-class"></a>Clase ExpOutput

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `ExpOutput` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [EXP_OUTPUT](../event-table.md#exp-output) .

## <a name="syntax"></a>Sintaxis

```cpp
class ExpOutput : public FileOutput
{
public:
    ExpOutput(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base [FileOutput](file-output.md) , la clase `ExpOutput` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[ExpOutput](#exp-output)

## <a name="exp-output"></a>ExpOutput

```cpp
ExpOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [EXP_OUTPUT](../event-table.md#exp-output) .

::: moniker-end
