---
title: Clase C2DLL
description: Referencia de clase C++ Build Insights SDK C2DLL.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C2DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7711acf800999d4e97c3ae56fa2100a632a245b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325077"
---
# <a name="c2dll-class"></a>Clase C2DLL

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `C2DLL` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [C2_DLL.](../event-table.md#c2-dll)

## <a name="syntax"></a>Sintaxis

```cpp
class C2DLL : public Activity
{
public:
    C2DLL(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados `C2DLL` de su clase base [Activity,](activity.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[C2DLL](#c2-dll)

## <a name="c2dll"></a><a name="c2-dll"></a>C2DLL

```cpp
C2DLL(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [C2_DLL.](../event-table.md#c2-dll)

::: moniker-end
