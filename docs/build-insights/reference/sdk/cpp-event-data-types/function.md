---
title: Function (clase)
description: La C++ referencia de clase de función SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3ff66119007ed7172fed7e824287ab8617c70973
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334773"
---
# <a name="function-class"></a>Function (clase)

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `Function` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [función](../event-table.md#function) .

## <a name="syntax"></a>Sintaxis

```cpp
class Function : public Activity
{
public:
    Function(const RawEvent& event);

    const char* Name() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base de [actividad](activity.md) , la clase `Function` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[Function](#function)

### <a name="functions"></a>Funciones

[Nombre](#name)

## <a name="function"></a>Funcionalidad

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [función](../event-table.md#function) .

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre de la función, codificada en UTF-8.

::: moniker-end
