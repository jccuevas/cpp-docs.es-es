---
title: Clase de compilador
description: Referencia C++ de la clase del compilador del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a63a0bad1ab6063d5986fec77b5135f500ded1ce
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334947"
---
# <a name="compiler-class"></a>Clase de compilador

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `Compiler` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento [del compilador](../event-table.md#compiler) .

## <a name="syntax"></a>Sintaxis

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de la clase base de [invocación](invocation.md) , la clase `Compiler` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[Compilación](#compiler)

## <a name="compiler"></a>Compilación

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento [del compilador](../event-table.md#compiler) .

::: moniker-end
