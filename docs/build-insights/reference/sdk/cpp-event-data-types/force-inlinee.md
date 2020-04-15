---
title: Clase ForceInlinee
description: Referencia de clase ForceInlinee del SDK de C+++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c6a1af0384197a0a3b6062ad9ef30537c348190d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324777"
---
# <a name="forceinlinee-class"></a>Clase ForceInlinee

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `ForceInlinee` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [FORCE_INLINEE.](../event-table.md#force-inlinee)

## <a name="syntax"></a>Sintaxis

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `ForceInlinee` su clase base [SimpleEvent,](simple-event.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>Functions

[Name](#name)
[Tamaño del](#size) nombre

## <a name="forceinlinee"></a><a name="force-inlinee"></a>ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [FORCE_INLINEE.](../event-table.md#force-inlinee)

## <a name="name"></a><a name="name"></a>Nombre

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de la función de inlineación, codificada en UTF-8.

## <a name="size"></a>Tamaño de la <a name="size"></a>

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño de la función de forzar insertada, como un recuento de instrucciones intermedio.

::: moniker-end
