---
title: Clase C1DLL
description: Referencia C++ de la clase C1DLL del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C1DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f843e7dcd14dc9e9649317933008b575ff4eddf0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335007"
---
# <a name="c1dll-class"></a>Clase C1DLL

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `C1DLL` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [C1_DLL](../event-table.md#c1-dll) .

## <a name="syntax"></a>Sintaxis

```cpp
class C1DLL : public Activity
{
public:
    C1DLL(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base de [actividad](activity.md) , la clase `C1DLL` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[C1DLL](#c1-dll)

## <a name="c1-dll"></a>C1DLL

```cpp
C1DLL(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [C1_DLL](../event-table.md#c1-dll) .

::: moniker-end
