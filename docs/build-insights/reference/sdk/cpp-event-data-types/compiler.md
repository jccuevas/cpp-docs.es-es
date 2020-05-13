---
title: Clase de compilador
description: La referencia de clase del compilador del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9b0a2622c4bc0bc19d7222977fe24c060ee8709e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325025"
---
# <a name="compiler-class"></a>Clase de compilador

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `Compiler` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [COMPILER.](../event-table.md#compiler)

## <a name="syntax"></a>Sintaxis

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `Compiler` su clase base [Invocation,](invocation.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[Compilador](#compiler)

## <a name="compiler"></a><a name="compiler"></a>Compilador

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [COMPILER.](../event-table.md#compiler)

::: moniker-end
