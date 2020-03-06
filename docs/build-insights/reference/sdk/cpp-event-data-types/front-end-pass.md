---
title: Clase FrontEndPass
description: Referencia C++ de la clase FRONTENDPASS del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cc0bf38c46b51d4a49da46be88e23afa64c12cc8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334785"
---
# <a name="frontendpass-class"></a>Clase FrontEndPass

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `FrontEndPass` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [FRONT_END_PASS](../event-table.md#front-end-pass) .

## <a name="syntax"></a>Sintaxis

```cpp
class FrontEndPass : public CompilerPass
{
public:
    FrontEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base [CompilerPass](compiler-pass.md) , la clase `FrontEndPass` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[FrontEndPass](#front-end-pass)

## <a name="front-end-pass"></a>FrontEndPass

```cpp
FrontEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [FRONT_END_PASS](../event-table.md#front-end-pass) .

::: moniker-end
