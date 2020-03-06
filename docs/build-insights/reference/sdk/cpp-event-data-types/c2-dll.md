---
title: Clase C2DLL
description: Referencia C++ de la clase C2DLL del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C2DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9a8ae7e8cd2d4d379865a9a7a388a6204eb9f173
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334977"
---
# <a name="c2dll-class"></a>Clase C2DLL

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `C2DLL` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [C2_DLL](../event-table.md#c2-dll) .

## <a name="syntax"></a>Sintaxis

```cpp
class C2DLL : public Activity
{
public:
    C2DLL(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base de [actividad](activity.md) , la clase `C2DLL` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[C2DLL](#c2-dll)

## <a name="c2-dll"></a>C2DLL

```cpp
C2DLL(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [C2_DLL](../event-table.md#c2-dll) .

::: moniker-end
