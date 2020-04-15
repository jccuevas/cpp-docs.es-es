---
title: Clase C1DLL
description: Referencia de clase C++ Build Insights SDK C1DLL.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C1DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8c45942660a6e1b51dcd261bcf8977125c0d64a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325197"
---
# <a name="c1dll-class"></a>Clase C1DLL

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `C1DLL` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [C1_DLL.](../event-table.md#c1-dll)

## <a name="syntax"></a>Sintaxis

```cpp
class C1DLL : public Activity
{
public:
    C1DLL(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados `C1DLL` de su clase base [Activity,](activity.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[C1DLL](#c1-dll)

## <a name="c1dll"></a><a name="c1-dll"></a>C1DLL

```cpp
C1DLL(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [C1_DLL.](../event-table.md#c1-dll)

::: moniker-end
