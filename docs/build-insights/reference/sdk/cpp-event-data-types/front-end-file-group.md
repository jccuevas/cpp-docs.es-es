---
title: Clase FrontEndFileGroup
description: La referencia de clase FrontEndFileGroup del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d2eebb650e59e750e5ebde74914dca5f0ef4779d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324771"
---
# <a name="frontendfilegroup-class"></a>Clase FrontEndFileGroup

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `FrontEndFileGroup` clase se utiliza con las funciones [MatchEventStack](../functions/match-event-stack.md) y [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilícelo para que coincida con grupos de [eventos de FRONT_END_FILE.](../event-table.md#front-end-file)

## <a name="syntax"></a>Sintaxis

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su `FrontEndFileGroup` clase base [EventGroup\<\> FrontEndFile,](event-group.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[FrontEndFileGroup](#front-end-file-group)

## <a name="frontendfilegroup"></a><a name="front-end-file-group"></a>FrontEndFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>Parámetros

*Grupo*\
Un grupo de [eventos FRONT_END_FILE.](../event-table.md#front-end-file)

::: moniker-end
