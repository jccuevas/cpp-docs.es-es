---
title: Clase BackEndPass
description: La referencia de clase BackEndPass del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BackEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2b4b1a219abdbe418efaab4537f1c6dc9a22afb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325235"
---
# <a name="backendpass-class"></a>Clase BackEndPass

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `BackEndPass` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [BACK_END_PASS.](../event-table.md#back-end-pass)

## <a name="syntax"></a>Sintaxis

```cpp
class BackEndPass : public CompilerPass
{
public:
    BackEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `BackEndPass` su clase base [CompilerPass,](compiler-pass.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[BackEndPass](#back-end-pass)

## <a name="backendpass"></a><a name="back-end-pass"></a>BackEndPass

```cpp
BackEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [BACK_END_PASS.](../event-table.md#back-end-pass)

::: moniker-end
