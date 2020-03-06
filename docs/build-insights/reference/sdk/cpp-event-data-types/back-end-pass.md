---
title: Clase BackEndPass
description: Referencia C++ de la clase BACKENDPASS del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BackEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c159fa09b5d8a4156fc6bd886fc36da09a66db73
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335019"
---
# <a name="backendpass-class"></a>Clase BackEndPass

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `BackEndPass` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [BACK_END_PASS](../event-table.md#back-end-pass) .

## <a name="syntax"></a>Sintaxis

```cpp
class BackEndPass : public CompilerPass
{
public:
    BackEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base [CompilerPass](compiler-pass.md) , la clase `BackEndPass` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[BackEndPass](#back-end-pass)

## <a name="back-end-pass"></a>BackEndPass

```cpp
BackEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [BACK_END_PASS](../event-table.md#back-end-pass) .

::: moniker-end
