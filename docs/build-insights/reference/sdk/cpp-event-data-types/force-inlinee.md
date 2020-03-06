---
title: Clase ForceInlinee
description: Referencia C++ de la clase FORCEINLINEE del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7d3cce13601a0b3edbcd2b57664b2d0d94a7d3df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334839"
---
# <a name="forceinlinee-class"></a>Clase ForceInlinee

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `ForceInlinee` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [FORCE_INLINEE](../event-table.md#force-inlinee) .

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

Junto con los miembros heredados de su clase base [SimpleEvent](simple-event.md) , la clase `ForceInlinee` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>Funciones

[Nombre](#name)
[tamaño](#size)

## <a name="force-inlinee"></a>ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [FORCE_INLINEE](../event-table.md#force-inlinee) .

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre de la función insertada por fuerza, codificada en UTF-8.

## <a name="size"></a>Ajusta

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño de la función insertada por fuerza, como recuento de instrucciones intermedias.

::: moniker-end
